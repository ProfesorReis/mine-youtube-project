# Technical Context

## Upstream Proje Bilgileri

- **Proje:** AgentTube (youtube-automation-agent)
- **Upstream:** [github.com/darkzOGx/youtube-automation-agent](https://github.com/darkzOGx/youtube-automation-agent)
- **Sürüm:** v2.10.0 (master)
- **Runtime:** Node.js 18+
- **Veritabanı:** SQLite (lokal, self-hosted)
- **Dashboard:** Web UI — `http://localhost:3456`
- **Lisans:** MIT

## Teknoloji Yığını (Provider'lar)

### Metin / Script Üretimi
| Provider | Notlar |
|---|---|
| Gemini | Google AI |
| OpenAI | GPT modelleri |
| OpenRouter | Çoklu model erişimi |
| Kimi | |
| MiMo | |
| GLM | |

### Video Üretimi
| Provider | Notlar |
|---|---|
| Seedance | |
| MiniMax H3 | |
| Gemini Omni Flash | |
| Kling | |
| Wan | |
| FFmpeg (Lokal) | Ücret yok, lokal montaj |

### Opsiyonel Entegrasyonlar
| Araç | Gereksinim |
|---|---|
| DarkzSEO | Python + DarkzSEO 1.4+ veya `DARKZSEO_PATH` |

## Klasör Yapısı

*(Fork tamamlandıktan sonra güncellenecek)*

```
Mine YouTube Project/
├── memory-bank/           # Bu proje için AI bağlam dosyaları
│   ├── index.md
│   ├── activeContext.md
│   ├── projectbrief.md
│   ├── techContext.md
│   ├── securityContext.md
│   └── decisions.md
└── youtube-automation-agent/  # Fork edilecek upstream repo
    ├── package.json
    ├── .env.example
    ├── ...
    └── (upstream dosyaları)
```

## Temel Komutlar

| Komut | Açıklama |
|---|---|
| `npm install` | Bağımlılıkları kur |
| `npm run walkthrough` | İnteraktif kurulum rehberi |
| `npm start` | Uygulamayı başlat (port 3456) |
| `npm run setup` | Kısa kurulum akışı |

## Önemli Mimari Notlar

- **Approval-first:** Tüm yayın akışları insan onayı gerektirir (varsayılan).
- **Checkpoint sistemi:** Her üretim aşaması SQLite'a kaydedilir, kesintide kaldığı yerden devam eder.
- **Scene Manifest:** Her sahne; seslendirme, görsel prompt, zamanlama, provider/task kimliği, asset kaynağı, haklar durumu ve revizyon geçmişini tutar.
- **Fail-closed narration:** Eksik, simüle edilmiş veya başarısız seslendirme ile üretim onaylanamaz, zamanlanamaz veya yayınlanamaz.
