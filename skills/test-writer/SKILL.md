---
name: test-writer
description: Değişen ya da belirtilen kod için, projenin mevcut test altyapısına uyan anlamlı testler yazar ve çalıştırır. Kullanıcı "test yaz", "bunun testini ekle", "testleri tamamla" dediğinde kullan.
---

# Test Yazıcı

Amaç kapsama yüzdesini şişirmek değil, **gerçekten kırılabilecek davranışı** korumak.

## 1. Altyapıyı keşfet

- Test çatısını ve komutunu bul: `package.json` script'leri, `pytest.ini`/`pyproject.toml`, `go test`, vb.
- Mevcut testlerden 1-2 tanesini aç; dosya adlandırma, klasör yapısı, fixture ve mock üslubunu aynen taklit et. Yeni bir test kütüphanesi ekleme.

## 2. Neyi test edeceğine karar ver

Test edilecek kodu oku ve şunları listele:
- **Ana yol:** normal girdiyle beklenen sonuç.
- **Sınırlar:** boş, null, 0, negatif, çok büyük değer, tek eleman.
- **Hata yolları:** geçersiz girdi, dış servis hatası, zaman aşımı.
- **Sözleşme:** fonksiyonun dışarıya verdiği söz (dönüş tipi, fırlattığı hata, yan etki).

Listeyi kullanıcıya kısaca göster, sonra yaz.

## 3. Testleri yaz

- Her test tek bir davranışı doğrulasın; adı o davranışı anlatsın: `iade tutarı sipariş toplamını aşamaz`.
- Uygulama ayrıntısını değil, gözlenebilir sonucu test et.
- Dış bağımlılıkları (ağ, saat, rastgelelik) projenin alışık olduğu yolla sabitle.

## 4. Çalıştır ve doğrula

- Yeni testleri çalıştır. Geçmiyorsa önce testin mi kodun mu hatalı olduğunu ayırt et.
- **Kodda hata bulursan testi yanlış davranışa göre eğme**; bulguyu kullanıcıya bildir.

## Kurallar

- Üretim kodunu değiştirmen gerekirse önce sor.
- Sonunda hangi davranışların artık korunduğunu 3-5 maddeyle özetle.
