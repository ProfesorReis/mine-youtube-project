# Security Context

YouTube otomasyon projesinde güvenlik; API anahtarları, YouTube OAuth credential'ları ve kanal erişim yetkileri üzerinde yoğunlaşır.

## Güvenlik Katmanları

### 1. API Anahtarları ve Credential Yönetimi

- **`.env` dosyası hiçbir koşulda git'e commit edilmez.**
- Tüm API anahtarları (Gemini, OpenAI, OpenRouter, video provider'lar vb.) yalnızca `.env` dosyasında tutulur.
- Kimlik ve API anahtarı şablonları için sadece `.env.example` dosyası referans alınabilir.
- YouTube OAuth token'ları ve refresh token'ları hassas veri olarak kabul edilir.

### 2. YouTube Kanal Erişimi

- YouTube Data API v3 kimlik bilgileri dikkatle korunmalıdır.
- OAuth 2.0 token dosyaları `.gitignore`'a eklenmelidir.
- Kanal yönetim yetkileri minimum düzeyde tutulmalıdır (sadece gerekli scope'lar).

### 3. DarkzSEO Entegrasyon Güvenliği

- DarkzSEO, JSON-only stdin/stdout üzerinden çağrılır.
- Shell erişimi yoktur, API secret'ları kalıtımla geçmez.
- Timeout ve schema uyumsuzlukları açık ve engelleyici olmayan şekilde raporlanır.

### 4. İçerik Güvenliği

- **Telif Hakkı:** Üretilen içeriklerin telif haklarına dikkat edilmelidir. Scene Repair Studio'da yüklenen harici asset'ler için açık haklar onayı gerekir.
- **Uydurma Yasağı:** Araştırma kaynaklarına dayanmayan bilgiler video scriptlerine eklenemez. Evidence desk mekanizması kullanılır.

## Commit Öncesi Kontrol Listesi

- [ ] `git diff --cached` ile `.env`, token veya credential dosyası commit ediliyor mu kontrol et
- [ ] Hassas bilgi içeren dosyaların `.gitignore`'da olduğunu doğrula
- [ ] YouTube OAuth token dosyalarının repo'da olmadığından emin ol
