# Mine YouTube Project - Runbook (Kullanım Kılavuzu)

Bu kılavuz, sistemi başlatmak, kontrol etmek ve günlük işlemleri yürütmek için gereken temel adımları sade bir dille açıklar.

---

## 🚀 1. Web Panelini Başlatma

### Terminalden Nasıl Başlatılır?
Mac terminalinizi açtığınızda **önce proje klasörüne girmelisiniz**:

```bash
cd "Yazılımsal Macbook/Mine YouTube Project"
npm start
```

### Web Paneline Giriş:
Komutu çalıştırdıktan sonra tarayıcınızdan şu adrese gidin:
👉 **[http://localhost:3456](http://localhost:3456)**

*(Durdurmak istediğinizde terminalde `Ctrl + C` tuşlarına basmanız yeterlidir).*

---

## 📊 2. Web Panelinde Neler Var?

Panel açıldığında sol menüden veya linklerden şu bölümlere erişebilirsiniz:

| Sayfa / Link | Ne İşe Yarar? |
|---|---|
| **Dashboard** (`/`) | Genel durum, çalışan ajanlar, son üretilen videolar ve sistem durumu |
| **Production Readiness** | Sistemin canlı testini yapar (Gemini, seslendirme, YouTube erişimi kontrolü) |
| **Review Studio** | Üretilen videoları YouTube'a gitmeden önce izleme, senaryoyu ve seslendirmeyi düzenleme yeri |
| **Scene Repair Studio** | Videonun sadece beğenmediğiniz bir sahnesini sıfırdan yapmadan tek tıkla onarma |
| **Shorts Repurposing** | Üretilen uzun videodan otomatik 9:16 dikey Shorts klipleri çıkarma |
| **Schedule** (`/schedule`) | Zamanlanmış yükleme takvimi |
| **Analytics** (`/analytics`) | Kanal izlenme ve abone performans grafikleri |

---

## ⚙️ 3. Sık Kullanılan Terminal Komutları

| Komut | Ne Yapar? |
|---|---|
| `npm start` | Web panelini ve arka plan servislerini başlatır (Port: 3456) |
| `node test.js` | Sistemin tüm parçalarını (45 test) kontrol eder, hata olup olmadığını söyler |
| `git status` | Hangi dosyaların değiştiğini ve git durumunu gösterir |
| `npm run scheduler` | Günlük otonom içerik üretim ve zamanlama döngüsünü başlatır |
| `npm run walkthrough` | İnteraktif terminal kurulum rehberini baştan açar |

---

## 🔄 4. Orijinal Depodan (Upstream) Güncelleme Alma

Orijinal açık kaynaklı proje (`darkzOGx/youtube-automation-agent`) yeni bir özellik veya güncelleme yayınladığında kendi projenizi güncellemek için:

```bash
cd "Yazılımsal Macbook/Mine YouTube Project"
git fetch upstream
git merge upstream/master
git push origin master
```
*Bu işlem sizin API anahtarlarınızı, ayarlarınızı veya YouTube token'larınızı bozmaz.*

---

## 🛡️ 5. Önemli Güvenlik Kuralları

1. **`.env` ve `config/tokens.json`:** Bu dosyalar sizin gizli API ve YouTube şifrelerinizi tutar. Asla silmeyin ve kimseyle paylaşmayın. Bunlar zaten `.gitignore` ile korunmaktadır (GitHub'a gitmez).
2. **Onay Mekanizması (Approval-First):** Sistem siz web panelinden onay vermediğiniz sürece YouTube kanalınıza kendi kafasına göre video yüklemez. Önce üretir, önizlemenize sunar, onaylarsanız yükler.
