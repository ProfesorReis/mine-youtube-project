# Memory Bank - Mine YouTube Project

> [!WARNING]
> **AI Agent'lar:** Daima `activeContext.md` ile başla. Tek-kaynak ilkesi: her bilgi SADECE bir dosyada yaşar.

Bu Memory Bank, AgentTube (youtube-automation-agent) fork'unun Mehmet'in kendi YouTube kanalı için uyarlanması sürecindeki tüm bağlamı, kararları ve teknik durumu takip eder.

## Dosya Haritası

| Dosya | İçerik | Ne Zaman Okunmalı |
|---|---|---|
| [index.md](index.md) | Dosya haritası, kılavuz ve dokümantasyon referansları | Bilgi haritasını anlamak veya referans bulmak gerektiğinde |
| [activeContext.md](activeContext.md) | Mevcut sprint hedefleri, roller, güncel durum ve kalıcı kurallar | **Her oturumun başında (Mecburi)** |
| [projectbrief.md](projectbrief.md) | Proje vizyonu, fazlı yol haritası ve başarı kriterleri | Projenin kapsamı ve hedefleri gözden geçirilirken |
| [techContext.md](techContext.md) | Teknoloji yığını, klasör yapısı ve sistem mimari bilgileri | Teknik detaylar ve mimari yapı incelenirken |
| [securityContext.md](securityContext.md) | API anahtarları, YouTube OAuth kimlik bilgileri ve gizlilik kuralları | API entegrasyonu, credential yönetimi veya git commit öncesi |
| [decisions.md](decisions.md) | Alınan mimari ve süreç kararları, gerekçeleri ve durumları | Yeni bir karar almadan önce veya geçmiş kararları incelemek için |

## Tek-Kaynak İlkesi

Aşağıdaki konular memory-bank içinde kopyalanmaz. İlgili bilgilerin tek kaynağı upstream proje dosyalarıdır:

| Konu | Kaynak |
|---|---|
| AgentTube kurulum rehberi | Proje kökündeki `README.md` |
| Ortam değişkenleri | `.env.example` |
| Changelog | `CHANGELOG.md` |
| Lisans | `LICENSE` |

## Okuma Sıraları

1. **Yeni Oturum Başlangıcı:** `activeContext.md` → `projectbrief.md`
2. **Kod/Uygulama İşi:** `activeContext.md` → `securityContext.md` → `techContext.md`
3. **Planlama / Karar Alma:** `activeContext.md` → `decisions.md` → `projectbrief.md`
