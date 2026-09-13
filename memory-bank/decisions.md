# Decisions

Bu dosya, proje sürecinde alınan mimari ve süreç kararlarını, gerekçelerini ve güncel durumlarını takip eder.

### [2026-09-14] AgentTube upstream fork olarak kullanılacak
- **Context:** AgentTube (youtube-automation-agent) aktif olarak geliştirilen açık kaynaklı bir YouTube otomasyon ajanıdır (v2.10.0, MIT lisanslı).
- **Rationale:** Sıfırdan yazmak yerine olgun bir projeyi fork etmek; approval-first workflow, checkpoint sistemi, çoklu provider desteği ve dashboard gibi özelliklerden hemen yararlanmayı sağlar. Upstream güncellemeleri merge ile takip edilebilir.
- **Status:** ✅ Active

### [2026-09-14] Memory-bank yapısı career-ops modelinden uyarlandı
- **Context:** Mehmet'in career-ops projesinde başarıyla kullanılan memory-bank sistemi referans alındı.
- **Rationale:** Kanıtlanmış bir yapı. Dosya haritası (index.md), aktif bağlam (activeContext.md), proje özeti (projectbrief.md), teknik bağlam (techContext.md), güvenlik bağlamı (securityContext.md) ve kararlar (decisions.md) dosyalarından oluşur. `bugs-known.md` henüz eklenmedi çünkü proje henüz çalışır durumda değil.
- **Status:** ✅ Active

### [2026-09-14] bugs-known.md ve runbook.md başlangıçta eklenmedi
- **Context:** Örnek memory-bank'te bu dosyalar mevcuttu.
- **Rationale:** Proje henüz fork aşamasında; bilinen hata veya çalıştırma rehberi yazacak deneyim birikimi yok. Sistem kurulup ilk hatalar ve süreçler ortaya çıktıkça eklenecek.
- **Status:** 📋 Deferred
