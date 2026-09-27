---
name: release-notes
description: İki sürüm (etiket ya da commit) arasındaki değişikliklerden, kullanıcının anlayacağı dilde sürüm notu hazırlar. Kullanıcı "sürüm notu yaz", "changelog hazırla", "bu sürümde neler var" dediğinde kullan.
---

# Sürüm Notu

Sürüm notu geliştirici günlüğü değildir; **ürünü kullanan kişinin** "bu sürüm bana ne getiriyor?" sorusuna cevap verir.

## 1. Aralığı belirle

- Son etiketi bul: `git describe --tags --abbrev=0`. Kullanıcı başka bir aralık verdiyse onu kullan.
- Değişiklikleri topla: `git log <önceki-etiket>..HEAD --no-merges --pretty=format:"%h %s"`.
- `gh` kuruluysa birleştirilen PR başlıklarına ve açıklamalarına da bak; commit mesajından daha açıklayıcıdır.

## 2. Grupla

- **Yeni** — kullanıcının yapabildiği yeni şeyler
- **İyileştirmeler** — var olanın daha iyi çalışması
- **Düzeltmeler** — giderilen hatalar
- **Dikkat** — geriye dönük uyumsuz değişiklikler, yapılması gereken geçiş adımları

İç düzenlemeleri, test ve araç değişikliklerini kullanıcıyı etkilemiyorsa nota koyma.

## 3. Yaz

- Her maddeyi fayda diliyle yaz: "refactor auth middleware" değil, "Oturum süresi dolduğunda artık veri kaybetmeden yeniden giriş yapılıyor".
- **Dikkat** bölümünü en üste koy ve ne yapılması gerektiğini adım adım yaz.
- Emin olmadığın bir etkiyi kesinmiş gibi yazma; kullanıcıya sor.

## Çıktı

```
## vX.Y.Z — <tarih>

### ⚠️ Dikkat
### Yeni
### İyileştirmeler
### Düzeltmeler
```

Boş başlıkları yazma.
