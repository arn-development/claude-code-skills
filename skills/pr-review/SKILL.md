---
name: pr-review
description: Mevcut daldaki değişiklikleri (diff) inceler; kritik bulguları önce sıralar, her bulguyu dosya:satır ile gösterir ve eksik testleri önerir. Kullanıcı "PR'ımı incele", "değişikliklerimi gözden geçir", "review yap" gibi bir şey istediğinde kullan.
---

# PR İnceleme

Bu skill, daldaki değişiklikleri kıdemli bir geliştirici gözüyle inceler. Amaç stil yorumu yapmak değil; hatayı, riski ve eksik testi bulmaktır.

## 1. Kapsamı belirle

- Temel dalı bul: `git symbolic-ref refs/remotes/origin/HEAD`. Sonuç yoksa `main`, o da yoksa `master` kullan.
- İncelenecek değişiklik: `git diff <temel>...HEAD`. Commit edilmemiş değişiklik varsa `git diff HEAD` çıktısını da dahil et.
- Kullanıcı bir PR numarası verdiyse ve `gh` kuruluysa: `gh pr diff <numara>`.
- Değişen dosyaları listele. 40'tan fazla dosya varsa kullanıcıya hangi kısma odaklanılacağını sor.

## 2. Bağlamı oku

Diff tek başına yetmez. Değişen her fonksiyonun çağrıldığı yerleri ve ilgili testleri aç. Değişikliğin sözleşmeyi (girdi, çıktı, hata davranışı) bozup bozmadığını kontrol et.

## 3. Neye bakılır

- **Doğruluk:** mantık hatası, sınır durumları (boş, null, 0, çok büyük değer), off-by-one, yanlış karşılaştırma.
- **Veri ve durum:** yarış koşulu, paylaşılan durum, işlem (transaction) bütünlüğü, geri alınamayan işlemler.
- **Güvenlik:** kullanıcı girdisinin doğrulanması, SQL veya komut enjeksiyonu, sırların koda ya da loglara düşmesi, yetki kontrolü.
- **Hata yönetimi:** yutulan hatalar, anlamsız hata mesajları, yeniden denemesi olmayan dış çağrılar.
- **Performans:** döngü içinde sorgu veya ağ çağrısı, gereksiz büyük veri yükleme.
- **Testler:** değişen davranışı kapsayan test var mı? Yoksa hangi testin yazılması gerektiğini söyle.

## 4. Kanıtsız bulgu yazma

Her bulgu için somut bir senaryo ver: "şu girdi gelirse şu olur". Emin değilsen bulguyu **Soru** olarak işaretle; tahmini kesin bulgu gibi sunma.

## 5. Çıktı biçimi

Önce 1-2 cümlelik özet: değişiklik ne yapıyor ve genel risk düzeyi (düşük / orta / yüksek).

Sonra bulgular, önem sırasına göre:

```
### 🔴 Kritik
- `dosya.ts:42` — Sorun. Senaryo. Önerilen düzeltme.

### 🟠 Önemli
### 🟡 Öneri
### ❓ Soru

### 🧪 Eksik testler
- Hangi davranış, hangi dosyada test edilmeli.
```

Boş kalan başlıkları yazma. Hiç bulgu yoksa bunu açıkça söyle; olmayan sorun uydurma. Stil ve biçim yorumlarını yalnızca kullanıcı isterse ekle.

## Kurallar

- Kodu kendiliğinden değiştirme; önce bulguları sun. Kullanıcı isterse düzeltmeleri uygula.
- Kullanıcının dilinde yanıt ver.
