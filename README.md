# Korean Kutie 💕 코리안 큐티

A tiny, hand-built Korean learning app with one mission: **learn just enough Korean to
say ridiculously cute things to your wife — and actually remember them.**

**▶ Live app (permanent URL):** https://josiahdowdy.github.io/KoreanKutie/

Also published as a Claude Artifact: https://claude.ai/code/artifact/12d53f90-6ffe-4515-9867-6e5dc02308b9

The app is [`index.html`](index.html) — a single self-contained file (no build step, no
dependencies, works offline). Every push to `main` redeploys it to the URL above via the
GitHub Pages workflow in [`.github/workflows/pages.yml`](.github/workflows/pages.yml).

---

## What's inside the app

| Section | What it does |
|---|---|
| **Start** | Why Hangul takes a weekend, how the memory system works, your route, and a rotating "phrase of the day for her" |
| **Alphabet (한글)** | All 35 letter cards you need — shape stories + sound hooks, tap-to-hear audio, filters by group, a composition chart, and the 7 romanization sound traps |
| **Read (읽기)** | Interactive syllable **block builder** (assemble real Korean blocks from letters), decode 사랑해 piece by piece, and a "first reads" self-test |
| **Sweet talk (달콤한 말)** | 28 phrases across pet names, love notes, compliments, daily care, and basics — every one with a sound-alike **memory hook**, a "say it like" guide, politeness notes, favorites, and audio (normal + slow) |
| **Practice (연습)** | Three 8-question quiz decks (letters, reading, phrases), saved best scores, and progress bars |

Audio uses your device's built-in Korean text-to-speech voice (most phones and laptops
have one). Progress, favorites, and scores are saved locally in your browser.

## The memory method (why the silly hooks work)

The app runs on the **keyword mnemonic method**: tie the *sound* of a new word to a
vivid image you already own, and recall becomes automatic. Three amplifiers are baked in:

1. **Sound-alike scenes** — 사랑해 (*saranghae*) → love **RANG** the doorbell → "**HEY!**"
   The weirder the scene, the stickier it is.
2. **Emotion** — say the phrase *to your wife*. Her reaction (laughing at your
   pronunciation counts) welds the memory in place.
3. **Retrieval practice** — short daily quiz rounds beat long cram sessions. The app's
   "daily ritual": say it at breakfast, replay the scene at noon, quiz at night.

Pro tip built into the app: swap the stranger in any hook scene for *her*. Your brain
never deletes a movie she stars in.

## Research summary

### Hangul (the alphabet) is genuinely a weekend project
- Created by King Sejong in 1443 (introduced 1446) so ordinary people could read; the
  introduction document itself says a wise man learns it "before the morning is over."
- It's **not** thousands of characters: 14 basic consonants + 10 basic vowels do most of
  the work (plus 5 "tense twin" consonants and 11 combo vowels = 40 jamo total).
- Consonants sketch mouth shapes (ㅁ = closed lips, ㄱ = tongue root); vowels combine a
  standing person (ㅣ), the ground (ㅡ), and a dot (the sun). Shape mnemonics (ㅂ =
  bucket, ㅅ = ski slope, ㅎ = person in a hat) are the standard fast path.
- Letters stack into square **syllable blocks**: consonant + vowel, with tall vowels
  standing to the right (사), flat vowels lying below (보), and an optional final
  consonant — the 받침 *batchim* — in the "basement" (랑).

### Reading & speaking traps worth knowing on day one
- Romanized **eo = "uh"** (서울 Seoul = *suh-ool*), **eu** = flat unrounded "euh".
- **ㄹ** is a single tongue tap between r and l.
- Tense twins **ㅃ ㄸ ㄲ ㅆ ㅉ** are squeezed with zero puff of air (뽀뽀!).
- **ㅅ → "sh"** before i/y sounds (싶어 = *shee-puh*).
- **ㅇ** is silent at the front of a block, "ng" at the end (안녕 uses both).
- Final consonants are unreleased (밥 ends with closed lips).

### Talking to your wife: banmal + aegyo
- Korean grammar encodes politeness. With a spouse you use **반말 (banmal)** — intimate
  casual speech — which is conveniently the *shortest* form (사랑해, not 사랑합니다).
- Golden rule: add **~요 (yo)** to make almost anything polite for her parents,
  strangers, and waiters (사랑해 → 사랑해요, 맛있어 → 맛있어요).
- **여보 (yeobo)** is the classic "honey" reserved for married couples; **자기야
  (jagiya)** works for any couple; **애교 (aegyo)** — deliberate, weaponized cuteness
  (stretched vowels, higher pitch) — is a beloved part of Korean couple culture, as is
  the viral **Gwiyomi song** (1 + 1 = 귀요미).
- Care phrases *are* love language in Korean: 밥 먹었어? ("have you eaten?") and
  수고했어 ("you worked hard today") land like "I love you" in practice.

### The 28 phrases
Organized by category and difficulty (● first week → ●●● showing off), each with a
sound-hook. A taste:

| Korean | Sounds like | Means | The hook |
|---|---|---|---|
| 여보 | YUH-boh | Honey (married) | literally "**Yo, boo!**" |
| 사랑해 | sah-rahng-HEH | I love you | love **RANG** the doorbell — "**HEY!**" |
| 보고 싶어 | boh-goh shee-puh | I miss you | **BOGO** deal on **SHIP** tickets home |
| 많이 사랑해 | MAH-nee… | I love you so much | "mani" = **money** — rich in love |
| 안아줘 | ah-nah-JWUH | Hug me | "**Anna! Joe!**" airport bear hug |
| 뽀뽀해 줘 | ppoh-ppoh-heh JWUH | Kiss me | 뽀뽀 *is* the sound: **po!-po!** |
| 수고했어 | soo-goh-heh-ssuh | You worked hard today | "**SUE, GO** rest — **HEY, SO** proud" |
| 잘 자, 내 꿈 꿔 | jahl jah, neh koom kkwuh | Sleep well — dream of me | jolly jammies + a dove **coo-coo**ing you into *my* dream |

…and 20 more in the app, each with politeness notes (including in-law mode:
감사합니다, 식사하셨어요?, 안녕히 주무세요).

## Tech notes

- One self-contained HTML file: vanilla JS, no frameworks, no external requests.
- Fredoka display font embedded as a data URI (OFL license); Korean text renders in
  your device's native Korean fonts.
- Syllable builder composes real Hangul via Unicode arithmetic
  (`0xAC00 + (initial × 21 + vowel) × 28 + final`).
- Audio via the browser's `speechSynthesis` with a `ko-KR` voice when available.
- Light & dark themes; chart colors validated for color-blind safety (deuteranopia /
  tritanopia ΔE checks) in both modes.
- Progress stored in `localStorage` — private to your browser.

## Sources consulted

- [90 Day Korean — Korean terms of endearment](https://www.90daykorean.com/korean-terms-of-endearment/)
- [90 Day Korean — Korean love phrases](https://www.90daykorean.com/korean-love-phrases/)
- [90 Day Korean — How to learn the Korean alphabet fast](https://www.90daykorean.com/how-to-learn-the-korean-alphabet/)
- [Fluent in 3 Months — "Cute" in Korean & aegyo phrases](https://www.fluentin3months.com/cute-in-korean/)
- [Go! Go! Hanguk — 4 ways to say I love you in Korean](https://gogohanguk.com/en/blog/how-to-say-i-love-you-in-korean/)
- [Lingopie — Korean terms of endearment](https://lingopie.com/blog/korean-terms-of-endearment-a-heartfelt-guide-to-expressing-love-and-affection/)
- [Talkpal — How to memorize Hangul fast](https://talkpal.ai/how-to-memorize-hangul-fast-easy-tips-and-tricks/)
- [Dear Asia — Read Hangeul in a day](https://dearasia.co.uk/read-hangeul-in-a-day-a-quick-guide-to-mastering-korean-alphabets-for-beginners/)

---

*Built with 💗 and a lot of very silly mnemonics, for one very lucky wife. 한국어 화이팅!*
