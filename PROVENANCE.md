# PROVENANCE — how this rendering came to be

*Balochi (بلوچی), chair 97. Lit 2026-09-24 14:22. Floor 23,213 verses.*

This is the record of how the text in this repository was produced and
what had to be corrected in it. A machine-assisted rendering has no
standing unless you can see how it was made, so this file says both.

---

## The approach

Every verse is rendered from the Hebrew of that verse, under a written
discipline — `docs/methodology/translation-discipline/bal.md` in the
Selah repository, itself written in Balochi, built on the sister chairs
`ckb.md` (Sorani — the Arabic-Persian script mechanics, right to left),
`kmr.md` (Kurmanji — the Name's ruling) and `ug.md` (Uyghur). Seven rules
govern it: the Hebrew token is the unit; the Name stays the Name; both
truths of Deut 6:4; no foreknowledge (Gen 22:1 does not know Gen 22:13);
numbers and marks stay put; the translator has no word of its own; a hard
verse is laid bare, not smoothed.

**The `⟨ ⟩` brackets do two different jobs.** `⟨את⟩` is the Hebrew
direct-object marker, which Balochi has no word for; it is left standing
so the reader sees it. `⟨لبز⟩` is a word Hebrew did not write but Balochi
grammar requires — visibly marked, so you can always tell what the
Hebrew said from what the grammar needed.

**The script is the Balochi Academy standard**, Sayad Hashmi's alphabet
(ہ · ے · ں · ٹ · ڈ · ڑ · ۏ), with **Rakhshani** as the written base. That
is a pinned choice: Balochi is also written in an Iranian Persian-based
orthography and in Latin (Balo-Rabi). See NOTES.md, *Held for a Baloch
ear*.

## The fight on this chair is the Name

| Hebrew | here | rejected |
|---|---|---|
| יהוה | **یاہوہ** | ہدا · خدا · خداوند · پروردگار · یہوواہ · یہوہ · اللہ · رب · مالک |
| אלהים | **ایلوہیم** | ہدا in the Name's place |
| אל | **ایل** | ہدا |
| אל שדי | **ایل شدّای** | قادر مطلق ہدا |
| אדני | **ادونای** | خداوند · مالک |
| יה | **یاہ** | ہدا |
| צבאות | **سباؤت** | لشکرانی · سپاہانی |
| אהיה אשר אהיה | **اِہیِہ اَشِر اِہیِہ** | من آں کہ ہستاں |

**ہدا** over the nations' gods and **مالک** over a human lord remain
lawful; the census applies that distinction by the token's Hebrew
surface, never by spelling. The oblique **-ءَ** and the ezafe **-ءِ** on
the Name are grammar (Balochi is ergative), not title.

## The burn and the gate

The relay rendered 23,166 of 23,213 verses at about 52 a minute and moved
on with a residue of **47**; a gleaning pass at batch-size 2, then 1 for
the last straggler, landed all of them. A first-hour gate
(`dev/scripts/bal_gate.clj`) — the Name, the את family, Persian/Urdu
words, the Academy's letters, marquee verses — was run at 215 verses
(Name 41/41 clean), at 3,428 and at 20,799.

The corpus was committed to git **before any pass touched it**
(`3bc9f49e`), so every repair below is a diff you can read.

## Finding: a probe that convicted the language

The thermometer began with an `ar-letters` probe — the Arabic letters the
Academy respells for Balochi words (ث ذ ص ض ط ظ ة). It convicted **3,716
rows**. Those letters are the loanwords' own in written Balochi (طلا ·
نذر · حصار); the respelling rule is about Balochi words, not about every
Arabic loan in print. The probe was dropped, and how far the respelling
reaches is filed for Scott as a question. **ك → ک** and **ي → ی**
(codepoint substitutions, not spellings) stayed and were cured
deterministically.

The census probe was corrected twice more for the same reason: **کے**
(*who*, מי) and **هست** (*there is*, יש) were on the Persian bleed list
and are Balochi's own — 194 true rows convicted falsely.

## Finding: the model welds letters into the Hebrew record

The gate at 20,799 counted **2,783** rows whose `surface` field — the
Hebrew record, which is not ours to rewrite — had an Arabic or Persian
letter fused into it (کمونی · עלינו · یאמرو). The first census counted
3,106. They were restored from the text, not guessed
(`lang-surface-repair`, engine-side): the row's Hebrew is looked up in
the record and written back.

**And it recurs.** After *every* press round the model re-emits fused
surfaces — 597, then 87, then 79, then 44 — plus a few Name drifts. So §9
of the runbook became a standing step, run after every round rather than
once. That is this chair's finding for the fleet.

## Finding: the Name slips in spelling, not in substance

Four misses at the 3,428-verse gate, 70 at 20,799, 105 at the first
census: یاهوہ with the Arabic ه · یہوہ · یاہوو · یاہووہ · یاہوה with a
Hebrew ה. Every one a spelling slip of the same Name, cured token-guided
(the pass reads the Hebrew `surface` to know a Name seat, never the
Balochi spelling). Final: **0 drift, 0 not-the-Name**.

## The cure, in order

| pass | what |
|---|---|
| gleaning | 47 residue seats → 0 |
| §9 round 1 | 6,487 surfaces in 3,501 files (corrupt 3,106 → 12); Name pass 183 files (drift 105 → 0) |
| press round 1 | **4,631** census-convicted seats — count-mismatch 40 → 0, empty tokens 28 → 0, empty flows 5 → 0 |
| §9 round 2 | 16,296 surfaces in 1,757 files; Name pass 27 files |
| press round 2 | **599** (577 press · 22 ladder) |
| §9 round 3 | 2,222 surfaces in 232 files; Name pass 6 files |
| press round 3 | **195** (183 · 12) |
| §9 round 4 | 86 files |
| press round 4 | **97** (93 · 4) |
| §9 round 5 | 362 surfaces in 37 files |
| press round 5 | **57** (56 · 1) |
| §9 round 6 | 231 surfaces in 20 files |
| press round 6 | **37** (36 · 1) |
| §9 round 7 | 88 surfaces in 10 files |
| press round 7 | **30** |
| §9 round 8 | 79 surfaces in 9 files |
| press round 8 | **22** |
| §9 round 9 | 44 surfaces in 7 files |
| hand pass | 2-chronicles/22/11 — two Latin `a`s in three places, three ⟨את⟩ markers placed in row order |

Eight rounds, each roughly a third of the last: 4,631 → 599 → 195 → 97 →
57 → 37 → 30 → 22. The ninth census moved the marker gap by one (20 →
19), so the press was stopped: it had stopped moving it, and what is left
is not the press's to move.

## Open — declared, not repaired

- **The ⟨את⟩ gap** — 18 verses whose flow carries fewer markers than the
  row. Balochi fuses the object into the verb; none of the 18 is placeable
  by proof.
- **Aramaic ית** — Dan 3:12 `יתהון` glossed `⟨את⟩`. Aramaic's own object
  marker; D1 covers Hebrew. 31 chairs mark it where the English floor
  does not.
- **Gen 42:23 ترجمان** — lawful Balochi for *interpreter* (מליץ), and
  also the rails' own word for the translator, so the census flags it.
- **The script standard, the dialect, the loanword letters, گوَشت for
  every ויאמר** — a Baloch ear. See NOTES.md.

## Final

**23,213 / 23,213 verses.** یاہوہ in **6,828 of 6,828** Name seats,
across 6,254 verses. Every census class zero — not-the-Name, drift,
erasure, empty glosses, empty tokens, empty flows, Hebrew leaks, corrupt
surfaces, count mismatches, digits, Persian/Urdu bleed, Latin letters,
foreign letters — except the declared marker gap of 18 verses, the
Aramaic ית, and the one lawful rails word.
