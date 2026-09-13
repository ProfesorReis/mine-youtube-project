# Project Brief

## Vizyon

AgentTube (youtube-automation-agent) açık kaynaklı projesini fork ederek Mehmet'in kendi YouTube kanalını uçtan uca yöneten bir AI otomasyon sistemi kurmak. Sistem; konu araştırması, senaryo yazımı, seslendirme, görsel/video üretimi, montaj, SEO optimizasyonu, inceleme, zamanlama ve yayınlama süreçlerini otonom olarak yönetecek.

## Upstream Proje: AgentTube

- **Repo:** [darkzOGx/youtube-automation-agent](https://github.com/darkzOGx/youtube-automation-agent)
- **Sürüm:** v2.10.0
- **Lisans:** MIT
- **Teknoloji:** Node.js 18+, SQLite, Web Dashboard (port 3456)
- **Temel Yetenekler:**
  - Approval-first (onay odaklı) iş akışı
  - Çoklu AI provider desteği (Gemini, OpenAI, OpenRouter, Kimi, MiMo, GLM)
  - Çoklu video provider desteği (Seedance, MiniMax H3, Kling, Wan, FFmpeg)
  - DarkzSEO entegrasyonu (opsiyonel)
  - Checkpoint tabanlı sürdürülebilir üretim
  - Scene Repair Studio ve Shorts Repurposing Studio

## Roller

- **Mehmet (Patron):** Yönlendirici, karar verici ve onaylayıcı.
- **Antigravity (Kodlayıcı):** Uygulayıcı, geliştirici ve raporlayıcı.

## Fazlı Yol Haritası

| Faz | İçerik | Durum |
|---|---|---|
| **F0 (İskelet)** | Memory-bank kurulumu, repo fork'lama, lokal klonlama, Git yapılandırması | ⏳ Devam Ediyor |
| **F1 (Kurulum)** | `npm install`, `.env` yapılandırması, API credential'ları, `npm run walkthrough` | Bekliyor |
| **F2 (İlk Test)** | Production readiness kontrolü, ilk video üretim testi, dashboard tanıtımı | Bekliyor |
| **F3 (Kişiselleştirme)** | Kanal stratejisi, hedef kitle, içerik sütunları, yayın kadansı tanımlamaları | Bekliyor |
| **F4 (Otonom Üretim)** | Autonomous Channel Operator ile tam döngü üretim ve yayınlama | Bekliyor |

## Başarı Kriterleri

1. **Çalışan Fork:** Upstream'den fork edilmiş ve lokal olarak çalışan bir AgentTube kurulumu.
2. **Onay Mekanizması:** Hiçbir video Mehmet'in açık onayı olmadan yayınlanmaz.
3. **Güvenlik:** API anahtarları ve credential dosyaları asla git'e commit edilmez.
4. **Sürdürülebilirlik:** Upstream güncellemeleri takip edilebilir yapıda kalır.
5. **Kaliteli İçerik:** Üretilen videoların seslendirme, görsel ve SEO açısından yayına hazır kalitede olması.
