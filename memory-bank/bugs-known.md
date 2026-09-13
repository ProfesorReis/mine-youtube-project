# Bilinen Hatalar (Bugs Known)

Bu dosya sistemdeki açık veya çözülmüş sorunları takip eder. Sprint 0 itibariyle kendi tarafımızda oluşmuş bir hata bulunmamaktadır; ancak upstream sistemin bilinen davranışları aşağıda listelenmiştir.

## Open Issues

### 1. Bayat ATS İlanları (Stale ATS Job Postings)
- **Sorun:** Bazı şirketler yayından kaldırdıkları ilanları public API feed'lerinde tutmaya devam etmektedir. `node scan.mjs` varsayılan modda bu feed'e güvendiği için, süresi dolmuş veya kapanmış ilanlar `pipeline.md` dosyasına sızabilmektedir.
- **Geçici Çözüm / Çözüm:** `node scan.mjs --verify` komutunu kullanın. Bu parametre, API taramasından sonra Playwright kullanarak ilanın canlılık durumunu kontrol eder. Sıralı çalışır ve sadece yeni ilanları doğrular.

### 2. Yüksek Teknik Uyum & Düşük Kültür Skoru Tuzağı
- **Sorun:** Teknik uyum çok yüksek olmasına rağmen, şirketin kültürü/çalışma modeli (`config/profile.yml` altındaki `culture_screen.require` kriterleri) ile uyuşmazlık tespit edildiğinde, kültür skoru 2/5 seviyesine sabitlenir. Bu alan **Blok A** (Role Summary) altındaki *Culture Screen* alanında yer alır (Blok E veya F ile ilgisi yoktur). Genel skor 4.5+ çıksa bile, bu çelişki nedeniyle raporda şu uyarı oluşur: *"High technical fit, unconfirmed/poor culture fit - verify before applying."*
- **Kural:** `modes/_shared.md` § Scoring System (madde 5-7) altında tanımlanan bu mekanizma gereği, kültür boyutu uyarısı hafife alınmamalı ve genel skora körü körüne güvenilmemelidir.


## Resolved Issues

### 1. Playwright MCP Uyarısı (`Playwright MCP tools not detected`)
- **Sorun:** `npm run doctor` çalıştığında browser tabanlı tarama/canlılık denetimleri için Playwright MCP sunucusu bulunamadı uyarısı veriyordu.
- **Çözüm:** `career-ops/.claude/settings.json` dosyası içinde `mcpServers.playwright` tanımı (`npx -y @playwright/mcp-server@latest`) eklendi. `npm run doctor` uyarısı başarıyla giderildi ve `scan`, `pipeline`, `apply` modları için tam tarayıcı entegrasyonu sağlandı.

## Sistem Davranışları (Hata Değil)

### 1. Liveness Gate (Canlılık Kapısı) Koruma Mekanizması
- **Mekanizma:** `modes/oferta.md` satır 5-16 gereği, sisteme bir ilan URL'si girildiğinde, Block A değerlendirmesinden **önce** ilanın canlı olup olmadığı kontrol edilir. Eğer ilan kapanmış veya URL 404 dönüyorsa, sistem **orada işlemi durdurur**. Bu sayede tüm A-G değerlendirme sürecinin, rapor üretiminin ve PDF oluşturulmasının boşa gitmesi ve API token'larının israf edilmesi önlenmiş olur.
## Süreç Olayları (Process Incidents)

### 3. Sprint 2.2 Sabit Domain Allowlist Mantığı & Birim Test Çözümü (2026-07-21)
- **Olay:** Sprint 2.2'de Getro parser'ı yazılırken harici linkler için sabit domain kontrolü (`pancakeswap.finance`, `predict.fun`) konulmuş ve `j.url` mevcut olmasına rağmen `/companies/` dizgilemesi uygulanmıştı.
- **Kök Neden:** Parser kodunun yalnızca test kümesindeki harici linklere uydurulması (overfitting to test fixture).
- **Önlem / Düzeltme:** Tüm dizgileme ve allowlist kodları temizlendi. `j.url` koşulsuz okunacak şekilde refaktör edildi. Ağı bağımsız 4 senaryolu birim test takımı (`user-layer/parsers/getro-board.test.mjs`) eklenerek genellik kanıtlandı.

### 4. `--verify` Geçmişe Dönük Temizleme Yapmaz (2026-07-21)
- **Davranış:** `node scan.mjs --verify` yalnızca **o koşu sırasında yeni eklenen** ilanları canlılık denetimine tabi tutar. Daha önceki koşularda `pipeline.md`'ye eklenmiş ilanlar, sonraki bir `--verify` çalışmasında otomatik olarak temizlenmez.
- **Hata mı, davranış mı?** Tasarım gereği; dedup mantığının geriye dönük bir tarama yapmaması beklenen bir özelliktir.
- **Neden Önemli:** Sprint 3'te *"4 bayat Fireblocks ilanı elendi"* ifadesi raporlanmıştı. Oysa bu ilanlar Sprint 3.1'de hâlâ `pipeline.md`'de bulunuyordu; `--verify` onları silmemişti çünkü T3.1'de zaten eklenmişlerdi. Sprint 3 raporu bu çelişkiyi belgelemek yerine *"elendi"* diye sonuçlandırmıştı - bu belge içi çelişkidir.
- **Ne Yapmalı:** `pipeline.md`'deki ilanların geçmişte `--verify`'dan geçip geçmediğinden bağımsız olarak, eski ilanları manuel `grep`+HTTP kontrolüyle düzenli aralıklarla temizle.

### 5. Block G Tazelik Kör Noktası - Paradigm Olayı (2026-07-21)
- **Olay:** Sprint 3'te `Growth - Paradigm Portfolio` ilanı 4.6/5 aldı ve *"Apply immediately"* tavsiyesiyle raporlandı. Oysa ilan **2022-09-20** tarihinde yayınlanmıştı (~4 yıl önce) ve JD'nin kendi metni *"is not for an internal position at Paradigm"* yazıyordu. Bu, ders kitabı tanımıyla bir yetenek havuzu + hayalet ilan birleşimiydi.
- **Kök Neden:** Block G yalnızca ATS kaynağının meşruiyetine (resmi pano mu?) bakıyordu; posting tarihini ve ilanın gerçek bir pozisyon olup olmadığını değerlendirmiyordu.
- **Nasıl Yakalandı:** Sprint 3 denetiminde Claude, 2022 tarihini ve *"not for an internal position"* ifadesini JD'den gözlemleyerek işaretledi.
- **Çözüm:** `user-layer/_custom.md` → House Rules altına *Posting Freshness & Legitimacy* kuralları eklendi (Sprint 3.1 T3.1.2). Kurallar Block G davranışını `user-layer`'dan yönetiyor; sistem güncellemelerinden etkilenmiyor.
- **Kural Kanıtı:** Paradigm yeniden değerlendirmesi **2.8 / 5.0** verdi (önceki: 4.6). Trust Wallet (84 gün, taze) yeniden değerlendirmesi **4.4 / 5.0** verdi (değişmedi). Kural çalışıyor.

### 6. Ön Yazılarda Uydurma İşveren İddiaları ve Kural 11'in Doğuşu (2026-07-21)
- **Olay:** Sprint 4'te üretilen ön yazılarda (Cover Letter) Trust Wallet için "perpetual DEX, prediction markets DeFi entegrasyonları", United Stables için ise "$U's yield-bearing collateral models" gibi iddialar yer aldı. Bu iddialar ne ilan metninde ne de aday profilinde geçiyordu.
- **Kök Neden:** Sistemin uydurma denetimleri yalnızca aday (Mehmet) hakkındaki iddialara odaklanıyordu. Şirket ürün ve stratejilerini üretirken serbest kalan model, hayali özellikler/planlar uydurdu.
- **Nasıl Yakalandı:** Sprint 4 sonu denetiminde mimar Claude bu ifadeleri taratarak hiçbir kaynakta geçmediğini kanıtladı ve uydurma olduğunu tespit etti.
- **Çözüm:** `securityContext.md` ve `activeContext.md` dosyalarına Kural 11 eklenerek işveren iddialarının da uydurulması yasaklandı. Ön yazılar yalnızca ilan metninde geçen somut sorumluluklarla sınırlandırılarak yeniden üretildi.

### 7. Süreç Kontrolü Eksikliği: 22 Raporsuz Evaluated Kayıt, Çift Numara ve 5.0/5 Skoru (2026-07-23)
- **Olay:** applications.md dosyasında 22 kayıt raporları ve URL'leri olmadan "Evaluated" statüsünde girilmiştir. Aynı zamanda #114 numarası iki farklı ilana atanmış (PancakeSwap ve Crypto.com), PancakeSwap BD Manager rolü hem #110 (4.8, raporlu) hem #114 (5.0, raporsuz) olarak mükerrer eklenmiş ve 5.0/5 skoru kural dışı olarak verilmiştir.
- **Kök Neden:** Sistemin add-entry.mjs, reserve-report-num.mjs gibi core scriptleri atlanıp uygulamalar elle (manuel) girilmiştir. Bu durum doğrulama eksikliği nedeniyle fark edilmemiştir.
- **Çözüm:** `user-layer/scripts/verify-tracker.mjs` doğrulayıcı scripti yazıldı. applications.md'deki hatalı satırlar düzeltildi: PancakeSwap mükerrer satırı silindi, Crypto.com #136'ya taşındı, raporsuz Evaluated statüleri Triaged yapıldı, 5.0/5 olan OKX skoru 4.8/5'e çekildi ve gap adlandırıldı. `verify-tracker.mjs` artık her taramadan sonra çalıştırılmak üzere runbook'a eklendi.

