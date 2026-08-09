# Promptlar Kutubxonasi

Tizimlashtirilgan, versiyalanadigan va jamoa bo'yicha boshqariladigan AI promptlar to'plami. Har bir prompt alohida faylda saqlanadi, metama'lumotlar bilan ta'minlanadi va Git orqali kuzatiladi.

> **Prompt — kod kabi aktiv:** versiyalanadi, review qilinadi va sinovdan o'tkaziladi.

---

## Kutubxona tuzilmasi

```
prompts-library/
├── README.md              # Siz hozir shu faylni o'qyapsiz
├── .gitignore
├── dasturlash/             # Dasturlash bilan bog'liq promptlar
│   ├── code-review-security.md
│   ├── api-design-review.md
│   └── bug-fixing-assistant.md
├── tahlil/                 # Tahlil va tadqiqot promptlari
│   ├── data-analysis-report.md
│   ├── swot-analysis.md
│   └── competitor-analysis.md
├── kontent/                # Kontent yaratish promptlari
│   ├── blog-post-writer.md
│   └── social-media-copy.md
├── agentlar/               # AI agent uchun system promptlar
│   ├── research-agent.md
│   ├── code-review-agent.md
│   └── meeting-summarizer.md
└── testapp/                # Android loyihalarini test qilish
    └── ieee-829-test-plan.md
```

## Kategoriyalar

| Kategoriya | Tavsif | Promptlar soni |
|---|---|---|
| **dasturlash** | Kod ko'rib chiqish, API dizayn, xatolarni tuzatish | 3 |
| **tahlil** | Ma'lumot tahlili, SWOT, raqobat tahlili | 3 |
| **kontent** | Blog yozish, ijtimoiy tarmoq postlari | 2 |
| **agentlar** | Tadqiqot, kod review, uchrashuv xulosasi | 3 |
| **testapp** | Android Kotlin XML loyihalarini IEEE 829 bo'yicha test qilish | 1 |

## Har bir prompt fayli tarkibi

Har bir `.md` fayl ikki qismdan iborat:

### 1. Metama'lumot (YAML frontmatter)

Faylning eng boshidagi `---` belgilari orasida joylashadi:

```yaml
---
nomi: code-review-security
kategoriyasi: dasturlash
maqsadi: PR ni xavfsizlik bo'yicha tekshirish
versiya: 1.0
model: Claude 3.5 Sonnet
o_zgaruvchilar:
  - "{{stack}}"
  - "{{pr_description}}"
sinovdan_o_tgan: "2026-08"
muallif: Shakhbozbek Usmonov
---
```

| Maydon | Tavsif |
|---|---|
| `nomi` | Prompt nomi (inglizcha, kichik harflar, chiziq bilan ajratilgan) |
| `kategoriyasi` | Kategoriya: `dasturlash`, `tahlil`, `kontent`, `agentlar`, `testapp` |
| `maqsadi` | Prompt nimaga kerak — qisqacha tavsif |
| `versiya` | Semver format: `1.0`, `1.3`, `2.0` |
| `model` | Qaysi AI model bilan sinovdan o'tkazilgan |
| `o_zgaruvchilar` | Shablon o'zgaruvchilari ro'yxati |
| `sinovdan_o_tgan` | Oxirgi marta sinov qilingan sana (YYYY-MM) |
| `muallif` | Prompt muallifi |

### 2. Prompt matni

Metama'lumotdan keyin quyidagi bo'limlar ketma-ketlikda keladi:

```markdown
## Prompt

**Role:** (Rol — vazifa nuqtaiy nazaridan mutaxassis roli)
**Task:** (Vazifa — bitta aniq harakat fe'li bilan ifodalangan topshiriq)
**Context:** (Kontekst — loyiha, auditoriya, fon ma'lumoti)
**Format:** (Format — natija ko'rinishi: jadval, ro'yxat, JSON va h.k.)
**Constraints:** (Cheklovlar — nima qilinmasligi, hajm va uslub taqiqlari)
**Example:** (Namuna — kutilayotgan natijaning misoli)
```

## Yangi prompt qo'shish

1. Tegishli kategoriya papkasiga o'ting (`dasturlash/`, `tahlil/`, `kontent/`, `agentlar/`, `testapp/`)
2. Mavjud promptlardan birini nusxalang va nomini o'zgartiring
3. YAML frontmatter ni to'ldiring
4. Prompt matnini yuqoridagi 6 bo'lim bo'yicha yozing
5. `{{o_zgaruvchi}}` shablonlarini ishlatib, qayta ishlatiladigan qismlarni ajratib qo'ying
6. Git orqali commit va push qiling

### Namuna: yangi prompt yaratish

```bash
# Mavjud promptni nusxalash
cp dasturlash/code-review-security.md dasturlash/performance-review.md

# Tahrirlash va commit qilish
git add dasturlash/performance-review.md
git commit -m "feat(dasturlash): performance-review prompt qo'shildi v1.0"
git push
```

## Promptlardan foydalanish

1. Kerakli kategoriyani toping (yoki README dagi jadvaldan foydalaning)
2. Faylni oching va `## Prompt` bo'limini nusxalang
3. `{{o_zgaruvchi}}` larni o'zingizga kerakli qiymatlar bilan almashtiring
4. AI modeliga (ChatGPT, Claude, Gemini va h.k.) yuboring
5. Natijani tekshiring — agar sifat past bo'lsa, promptni yangilang va versiyani oshiring

## Versiyalash va yangilash

- **Minor yangilanish** (`1.0` → `1.1`): Kichik tuzatishlar, misolarni yangilash
- **Major yangilanish** (`1.0` → `2.0`): Prompt strukturasi o'zgarishi, yangi bo'limlar qo'shilishi
- `sinovdan_o_tgan` sanasini har yangilaganda yangilang
- **Choraklik tekshiruv:** Har 3 oyda barcha promptlarni qayta sinovdan o'tkazing

## Amaliyotlar

- [x] Har bir prompt alohida faylda
- [x] YAML frontmatter metama'lumot
- [x] O'zgaruvchilar shabloni `{{variable}}`
- [x] Git versiyalash va kuzatish
- [x] Role, Task, Context, Format, Constraints, Example tuzilmasi
- [ ] Choraklik qayta sinov jarayoni
- [ ] Jamoa review prosesi

## Muallif

**Shakhbozbek Usmonov**

---

> Ushbu kutubxona "Prompt texnologiyasi" kursi doirasida yaratilgan.
