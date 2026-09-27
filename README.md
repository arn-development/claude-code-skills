# Claude Code Skills

ARN Development ekibinin günlük işte kullandığı [Claude Code](https://claude.com/claude-code) skill'leri. Her skill tek bir klasördür; kurulumu birkaç saniye sürer.

Instagram'da paylaştığımız skill'lerin kaynağı burası: [@arndevelopment](https://www.instagram.com/arndevelopment/)

## Skill'ler

| Skill | Ne yapar |
|---|---|
| [pr-review](skills/pr-review/SKILL.md) | Dalındaki değişiklikleri inceler; kritik bulguları önce sıralar, her bulguyu `dosya:satır` ile gösterir, eksik testleri önerir. |
| [commit-message](skills/commit-message/SKILL.md) | Hazırlanan değişikliklerden Conventional Commits biçiminde açık bir commit mesajı yazar. |
| [test-writer](skills/test-writer/SKILL.md) | Değişen koda, projenin test altyapısına uyan anlamlı testler yazar ve çalıştırır. |
| [bug-hunt](skills/bug-hunt/SKILL.md) | Hatayı tahminle değil kanıtla ayıklar: yeniden üretir, kök nedeni bulur, düzeltmeyi testle kanıtlar. |
| [release-notes](skills/release-notes/SKILL.md) | İki sürüm arasındaki değişikliklerden kullanıcının anlayacağı dilde sürüm notu hazırlar. |

## Kurulum

Tüm projelerinde kullanmak için:

```bash
git clone https://github.com/arn-development/claude-code-skills.git
mkdir -p ~/.claude/skills
cp -r claude-code-skills/skills/* ~/.claude/skills/        # hepsi
# ya da tek tek: cp -r claude-code-skills/skills/pr-review ~/.claude/skills/
```

Yalnızca bir projede kullanmak için klasörü o projenin `.claude/skills/` dizinine kopyala.

## Kullanım

Claude Code'da doğal dille iste: "PR'ımı incele" ya da "değişikliklerimi gözden geçir". Claude uygun skill'i kendisi bulup çalıştırır.

## Lisans

MIT — dilediğin gibi kullan, değiştir, paylaş.
