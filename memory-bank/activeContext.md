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

**Faz 0 — İskelet Kurulumu** devam ediyor.
- [ ] Memory-bank altyapısı oluşturuldu
- [ ] Upstream repo fork edilecek
- [ ] Lokal klonlama ve ilk çalıştırma
- [ ] `.env` yapılandırması

## Kalıcı Çalışma Kuralları

1. **Git ve Commit Düzeni:** Her alt görev sonrası git commit atılır. API anahtarları, `.env` ve credential dosyaları asla commit edilmez.
2. **Eşzamanlı Güncelleme:** Bir kod değişikliği memory-bank'i bayatlatıyorsa, memory-bank güncellemesi ile kod değişikliği **aynı commit içinde** yer almalıdır. Tek-kaynak ilkesi esastır.
3. **Uydurma (Fabrication) Yasağı:** Sistem tarafından üretilecek içerikler yalnızca doğrulanmış kaynaklara dayanmalıdır.
4. **İnsan Onayı (Human-in-the-Loop):** AgentTube'un approval-first prensibi korunur. Hiçbir video Mehmet'in onayı olmadan yayına gönderilmez.

## Upstream Sürüm Bilgisi

- **AgentTube Sürümü:** v2.10.0 (master)
- **Upstream:** `https://github.com/darkzOGx/youtube-automation-agent`
