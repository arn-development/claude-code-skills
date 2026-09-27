---
name: commit-message
description: Hazırlanan (staged) değişiklikleri okuyup Conventional Commits biçiminde açık, doğru bir commit mesajı yazar. Kullanıcı "commit mesajı yaz", "bunu commitle", "mesaj öner" dediğinde kullan.
---

# Commit Mesajı

Amaç, değişikliğin **ne yaptığını ve neden yapıldığını** tek bakışta anlatan bir mesaj yazmak. Dosya listesini tekrar etmek değil.

## 1. Değişikliği oku

- `git diff --cached` ile hazırlanan değişikliklere bak. Hiçbir şey hazırlanmamışsa bunu söyle ve `git diff` çıktısına göre öneri yap; kendiliğinden `git add` çalıştırma.
- Deponun mevcut üslubunu öğren: `git log --oneline -15`. Depo kendi kuralını kullanıyorsa (ör. emoji, bilet numarası) ona uy.

## 2. Türü ve kapsamı seç

| Tür | Ne zaman |
|---|---|
| `feat` | Kullanıcının göreceği yeni bir yetenek |
| `fix` | Hata düzeltmesi |
| `refactor` | Davranışı değiştirmeyen yeniden düzenleme |
| `perf` | Performans iyileştirmesi |
| `test` | Yalnızca test ekleme veya düzeltme |
| `docs` | Yalnızca dokümantasyon |
| `chore` | Bağımlılık, yapılandırma, araç işleri |

Kapsam (scope) değişikliğin yaşadığı modüldür: `feat(auth): ...`.

## 3. Mesajı yaz

```
<tür>(<kapsam>): <emir kipinde, 72 karakteri geçmeyen özet>

<neden gerekti; önceki davranış neydi, şimdi ne oluyor>

<varsa: BREAKING CHANGE: ... / Closes #123>
```

- Özet satırı emir kipinde ve somut olsun: "Oturum süresi dolunca kullanıcıyı girişe yönlendir". "Düzeltmeler", "güncelleme" gibi boş özet yazma.
- Gövdede "neden"i anlat; "ne"yi diff zaten gösteriyor.
- Birden fazla ilgisiz değişiklik varsa bunu söyle ve ayrı commit'lere bölmeyi öner.

## Kurallar

- Mesajı öner, kullanıcı onaylamadan commit atma.
- Kullanıcının dilinde yaz; depo İngilizce commit kullanıyorsa İngilizce yaz.
