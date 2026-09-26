# NOTES — selah-bal, chair 97

Working notes in English. The reader-facing documents (`README.md`,
`CONTRIBUTING.md`) are in Balochi, as this chair's own documents should
be. The full account of what was done and what was decided is in
`PROVENANCE.md`.

Lit 2026-09-24 14:22. Burn complete 2026-09-24 21:26; residue gleaned
23:17; cleaned 2026-09-25 through eight press rounds.
Floor 23,213 verses.

**The first Balochi chair.** Balochi is spoken in four countries
(Pakistan, Iran, Afghanistan, Oman) and written three ways; this chair
writes the **Balochi Academy standard** (Sayad Hashmi's alphabet —
ہ · ے · ں · ٹ · ڈ · ڑ · ۏ), where most of the literature is, with
**Rakhshani** as the written base. Both of those are pinned choices, not
facts — see *Held for a Baloch ear*.

---

## Burn signature

| | |
|---|---|
| relay | `batch/relay-move-on! [:bal]`, engine-side |
| rate | ~52 verses/min, steady from first hour to last |
| after the relay | 23,166 / 23,213 — residue **47** |
| gleaning | batch-size 2, then 1 for the last straggler — all 47 landed |
| final | **23,213 / 23,213 verses** |
| first-hour gate | `dev/scripts/bal_gate.clj`, re-run at 215 · 3,428 · 20,799 |
| census | `dev/scripts/chair_census.clj bal`, 700 MB side JVM, thirteen runs |

## The thermometer

Vocabulary and letters, **whitelist first**. Balochi shares its alphabet
with Persian and Urdu, and the model has seen far more of both, so when
it tires it slides toward them. Three probes:

- **Persian/Urdu whole words** — است · این · از · در · برای · با · بود ·
  گفت · می‌رود · ہے · یہ · سے · میں, counted as whole words on **both**
  surfaces (the reader's flow and the token row). Balochi's own words
  that look Persian (آسمان · زمین · آپ · شپ · روچ · دل) are whitelisted
  first, because they are its own.
- **The Persian ه** (U+0647) where the Academy writes **ہ** (U+06C1).
- **Latin letters** outside ⟨ ⟩ — English, or Balo-Rabi (Latin Balochi).

**Final reading: every one of those classes at zero.**

## The letters that are not a fault

The thermometer first carried an `ar-letters` probe — ث · ذ · ص · ض ·
ط · ظ · ة, the Arabic letters the Academy respells (صبر → سبر). It
convicted **3,716 rows**. It was wrong: those letters are the loanwords'
own in written Balochi (طلا · نذر · حصار), and the Academy's respelling
is a rule about *Balochi* words, not about every Arabic loan that
circulates in print. The probe was **dropped** (`18d8b6a5`), and the
question — how far the respelling reaches — is filed for Scott.

**ك (U+0643) → ک (U+06A9)** and **ي (U+064A) → ی (U+06CC)** stayed: those
are codepoint substitutions, not spellings, and they were cured
deterministically.

## The Name

Balochi Bibles print **ہدا** / **خداوند** / **مالک**. This chair writes
**یاہوہ** — the Hebrew's four letters (י·ה·ו·ה) in the Academy's
letters, ہ for *h*, carried over from the Kurmanji chair's *Yahwe* and
the Sorani chair's *یاهوە*. The rest keeps D1: ایلوہیم · ادونای ·
ایل · ایل شدّای · یاہ · سباؤت · اِہیِہ اَشِر اِہیِہ.

**ہدا** keeps its lawful seat over the nations' gods (Ex 20:3,
אלהים אחרים → **دگہ ہدایان**), and **مالک** over a human lord. The
census reads the token's Hebrew surface, never the spelling.

**Name seats reading یاہوہ: 6,828 of 6,828**, across 6,254 verses.
Not-the-Name **0**. Drift **0**.

The oblique **-ءَ** and the ezafe **-ءِ** on the Name (یاہوہءَ گوَشت ·
یاہوہءِ گال) are pinned lawful — Balochi is ergative, and that is case,
not a title. No definite or plural ending ever touches a Name; the vocative
is the separate word **اے**.

## Open seats — declared, not repaired

| seat | what | waiting on |
|---|---|---|
| 18 verses | the flow carries fewer ⟨את⟩ than its row | a reader — see below |
| daniel/3/12 | `יתהון` glossed `⟨את⟩` — Aramaic's own object marker | the ruling on ית — 31 chairs mark it where the floor does not |
| genesis/42/23 | `ترجمان` (*interpreter*, מליץ) — lawful Balochi, and also the rails' own word for the translator | — |

### The ⟨את⟩ gap

Row markers **11,869**; flow markers **11,906**. The gap is **18 verses**
where the flow lost a marker the row carries — Balochi fuses the object
into the verb and drops the pronoun freely, so some rows carry a marker
the flow has no separate word to hang it on. Eight press rounds brought
the gap 807 → 19; a hand pass placed the three markers of
2-chronicles/22/11 in row order. The rest are left for a reader, not
guessed. That residue is the smallest in the live fleet (xh 357
verses · zu 542 · am 231 · sv 212).

## Held for a Baloch ear

- **The script standard.** The Academy (Pakistan) standard is pinned. If
  the Iranian readership should be served first, the ه/ہ row of the
  thermometer flips and the Arabic-letter question reopens.
- **The dialect.** Rakhshani as the written base; Makrani and Sulemani
  forms were not rejected where the model reached for them.
- **گوَشت for every ויאמר** — no honorific split (Sorani's
  فەرموو / وت is not this chair's grammar). If the register wants one,
  that is a later pass.
- **The loanword letters** — ث · ذ · ص · ض · ط · ظ · ة (above).
- **ءُ for *and*** — the Academy's hamza-waw is pinned; bare و also
  circulates.
- **شبات** for שבת, not شنبہ (the calendar's day-name); **مِشکان** for
  משכן; **شیئول**, **ماشیاح**, **ملاقاتءِ گدان**.
- The coined method terms in the rails and the UI catalog — کوان ·
  ٹوکن · گرماپیم · کرسی · گلاس · ترجمان · توارنبشت · قاعدہ — and the
  book names, against a printed Balochi Bible. The book-names catalog
  ships only the 18 slots two independent renderings agreed on; the rest
  show English until someone fills them in.

## Hand seats

- **2-chronicles/22/11** — a Latin `a` inside two words (گadan for گدان,
  اخزیaہو for اخزیاہو), in the flow and in two rows, and three ⟨את⟩
  markers missing from the flow. All five cured by hand, both surfaces,
  in row order.

## The standing step

**After every press round the model re-emits fused surfaces** — an
Arabic or Persian letter welded into the Hebrew `surface` field (کمونی ·
עלינו · یאמרו) — and a few Name drifts. Not a one-time fault of the
burn: a standing property of re-rendering. So §9 of the runbook
(`lang-surface-repair` + the token-guided Name pass) runs after *every*
round, not once. Round by round it restored 6,487 → 16,296 → 2,222 →
… → 44 surfaces. That is this chair's note for the runbook.
