# Active Context

## Kalıcı Uyarılar (her oturumda oku)

- Proje henüz fork aşamasında. Upstream: `https://github.com/darkzOGx/youtube-automation-agent`
- Hiçbir API anahtarı veya credential dosyası git'e commit edilmez.

## Kullanıcı Profili ve Rol Dağılımı

- **Mehmet (Patron):** Yönlendirici, karar verici ve onaylayıcı. Tüm açıklamalar sade ve jargonsuz olmalıdır.
- **Antigravity (Kodlayıcı):** Uygulayıcı, geliştirici ve raporlayıcı.

## Kullanıcı Tercihleri

- Büyük mantık değişiklikleri yapmadan önce daima Mehmet'ten **açık izin ve onay** isteyin.

## Güncel Durum (2026-09-14)

**Faz 0 (İskelet Kurulumu) Başarıyla Tamamlandı:**
- [x] Memory-bank altyapısı kuruldu
- [x] Upstream repo (`darkzOGx/youtube-automation-agent`) bağlandı
- [x] Private fork (`ProfesorReis/mine-youtube-project`) yerel olarak yapılandırıldı
- [x] `npm install` tamamlandı (tüm bağımlılıklar kuruldu)
- [x] `node test.js` ile sistem testleri çalıştırıldı (45/45 test BAŞARILI)
- [x] İlk commit atıldı ve GitHub private reposuna push edildi

**Sıradaki Adım (Faz 1 - Yapılandırma):**
- [ ] `.env` oluşturulması ve API anahtarlarının (Gemini/OpenAI vb.) tanımlanması
- [ ] `npm run walkthrough` ile ilk kurulum sihirbazının çalıştırılması ve YouTube yetkilendirmesi

## Kalıcı Çalışma Kuralları

1. **Git ve Commit Düzeni:** Her alt görev sonrası git commit atılır. API anahtarları, `.env` ve credential dosyaları asla commit edilmez.
2. **Eşzamanlı Güncelleme:** Bir kod değişikliği memory-bank'i bayatlatıyorsa, memory-bank güncellemesi ile kod değişikliği **aynı commit içinde** yer almalıdır. Tek-kaynak ilkesi esastır.
3. **Uydurma (Fabrication) Yasağı:** Sistem tarafından üretilecek içerikler yalnızca doğrulanmış kaynaklara dayanmalıdır.
4. **İnsan Onayı (Human-in-the-Loop):** AgentTube'un approval-first prensibi korunur. Hiçbir video Mehmet'in onayı olmadan yayına gönderilmez.

## Upstream Sürüm Bilgisi

- **AgentTube Sürümü:** v2.10.0 (master)
- **Upstream:** `https://github.com/darkzOGx/youtube-automation-agent`
