# 🌸 Nowruz

> **The world's oldest annual release — no breaking changes in 3,000 years. Zero deprecated features. Backwards compatible with every civilization that ever touched it.**

[![Version](https://img.shields.io/badge/version-1405.0.0-brightgreen)](https://en.wikipedia.org/wiki/Nowruz)
[![Build Status](https://img.shields.io/badge/build-passing%20since%203000%20BCE-success)](https://en.wikipedia.org/wiki/Nowruz)
[![License](https://img.shields.io/badge/license-Zoroastrian%20Public%20License-orange)](https://en.wikipedia.org/wiki/Zoroastrianism)
[![Uptime](https://img.shields.io/badge/uptime-99.999%25%20(3000%20years)-blue)](https://worldometer.info)
[![Contributors](https://img.shields.io/badge/contributors-300M%2B%20humans-ff69b4)](https://en.wikipedia.org/wiki/Nowruz)
[![Schedule](https://img.shields.io/badge/cron-0%200%2020%203%20*-purple)](https://crontab.guru)
[![Maintained](https://img.shields.io/badge/maintained-by%20the%20sun-yellow)](https://en.wikipedia.org/wiki/Vernal_equinox)

---

## 📖 Table of Contents

- [What is Nowruz?](#what-is-nowruz)
- [Why It Slaps](#why-it-slaps)
- [Installation](#installation)
- [The Haft Seen API](#the-haft-seen-api)
- [Architecture](#architecture)
- [Scheduler](#scheduler)
- [Known Issues](#known-issues)
- [Migration Guide](#migration-guide)
- [FAQ](#faq)
- [Contributing](#contributing)
- [Sponsors](#sponsors)
- [Changelog](#changelog)

---

## What is Nowruz?

**Nowruz** (`نوروز`, lit. *"New Day"*) is a zero-cost, zero-dependency, fully distributed Persian New Year celebration that deploys itself every year at the **exact moment of the vernal equinox** — no cron job needed, the sun handles scheduling.

It is the most reliable piece of infrastructure humans have ever built.

```
$ curl -X GET https://earth.sun/spring?hemisphere=north

HTTP/1.1 200 OK
Content-Type: application/joy
X-Season: Spring
X-Year: 1405
X-Mood: Renewed

{
  "event": "Nowruz",
  "timestamp": "2026-03-20T17:46:00Z",
  "duration": "13 days (minimum)",
  "status": "blooming",
  "recommended_action": "call your mother"
}
```

---

## Why It Slaps

- 🌱 **Self-healing** — no matter what chaos the previous year shipped, Nowruz resets the state
- ☀️ **Astronomically scheduled** — maintained by a 4.6-billion-year-old star with no downtime
- 🍎 **Zero vendor lock-in** — celebrated across Iran, Afghanistan, Tajikistan, Kurdistan, Azerbaijan, Uzbekistan, and wherever Persians have taken their rice cookers
- 📦 **Ships with food** — literally every release includes `ash-e-reshteh`, `sabzi polo mahi`, and `reshteh khoshkar`
- 🔁 **Fully idempotent** — run it every year, always returns joy
- 🕯️ **No dark mode** — candles only

---

## Installation

Nowruz requires no installation. It finds you.

```bash
# Option A: Be born into a Persian family
$ ancestry --set iranian
> Nowruz will install itself. You will also receive strong opinions
> about rice, ta-dig, and how to properly greet elders.

# Option B: Marry into it
$ relationship --join persian_family
> Warning: you will now be expected at haft-seen by 11:30am sharp.
> Tardiness is not a known error code in this culture.

# Option C: Have a Persian friend
$ friendship --add persian_person
> Nowruz detected in your social graph.
> Expect: sweets, flowers, invitations, and being told you are
> "like family now" by someone's grandmother within 20 minutes.
```

**Minimum system requirements:**
- 1x sofreh (table cloth)
- 7x items starting with the letter `س` (see [Haft Seen API](#the-haft-seen-api))
- 1x goldfish (live, not NFT)
- Infinite sabzi polo
- At least one family member who insists the haft seen is wrong

---

## The Haft Seen API

The core module. Seven items, all starting with `س`, each a named export of the universe's hope for the coming year.

```ts
import { HaftSeen } from '@nowruz/sofreh'

const sofreh = new HaftSeen({
  sabzeh:  Sprouts,        // رشد — growth, rebirth
  samanu:  WheatPudding,   // شیرینی — sweetness, abundance
  sib:     Apple,          // سلامتی — health, beauty
  sir:     Garlic,         // دارو — medicine, protection
  senjed:  OliveberryDried,// عشق — love, wisdom
  serkeh:  Vinegar,        // صبر — patience, age
  somaq:   Sumac,          // سپیده‌دم — sunrise, the color of dawn
})

sofreh.deploy()
// → table looks incredible
// → house smells like herbs and hope
// → grandmother approves (rare event, log this)
```

**Optional but strongly recommended extras:**

| Item | Purpose | Notes |
|------|---------|-------|
| 🪞 Mirror | Reflection | Shows who you were; suggests who you could be |
| 🕯️ Candles | Light | One per family member. No dimmers. |
| 🐟 Goldfish | Life | Must be alive. Must not die before Sizdah Bedar. |
| 📖 Holy book | Guidance | Quran, Avesta, or Hafez — based on family config |
| 🪙 Coins | Prosperity | Old. Gold. Ideally inherited. |
| 🥚 Painted eggs | Fertility | One per child. More eggs = more pressure. |
| 🌹 Flowers | Beauty | Hyacinth preferred. Freshness required. |

---

## Architecture

```
                        ☀️  THE SUN
                     (primary scheduler)
                           │
              ─────────────┼─────────────
             │                           │
      🌍 Earth orbit              Vernal Equinox
      (dependency)             (event trigger, ~March 20)
                                         │
                              ┌──────────▼──────────┐
                              │     NOWRUZ CORE     │
                              │   نوروز مبارک باد   │
                              └──────────┬──────────┘
                                         │
              ┌──────────┬───────────────┼──────────────┬──────────┐
              │          │               │              │          │
         🌱 Sabzeh   🍎 Haft Seen    🍚 Food        👨‍👩‍👧 Family   💸 Eidi
         (growth)   (sofreh table)  (infinite)     (mandatory)  (cash gifts
                                                                  to children
                                                                  + adults
                                                                  who act
                                                                  childlike)
              │
    ┌─────────┼─────────┐
    │         │         │
  Chaharshanbe  Nowruz  Sizdah
  Suri 🔥     Day 🌸   Bedar 🌿
 (jump over   (year    (picnic,
  fire,        resets)  don't stay
  burn the               indoors
  old year)              or you'll
                         stay
                         unmarried
                         all year —
                         this is
                         canon)
```

---

## Scheduler

Nowruz does not use cron. It uses the **heliocentric equinox model**, which has been running in production since ~4.6 billion BCE with zero outages.

```
# human cron (for reference only — the sun doesn't need this)
# ┌──── second (exact, calculated by astronomers)
# │  ┌─ minute
# │  │  ┌── hour (UTC)
# │  │  │   ┌─── day (~March 20)
# │  │  │   │  ┌──── month
# │  │  │   │  │
# 46 46 17  20  3  →  fire Nowruz 1405
```

**Countdown to next release:**

```bash
$ nowruz --next

> Nowruz 1405 deploys in: 365 days, 5 hours, 48 minutes
> This is not a bug. Time is passing. Go call someone you love.
```

---

## Known Issues

| ID | Description | Status |
|----|-------------|--------|
| #1 | Traffic jams during `noruz safar` (Nowruz travel) — entire nation migrates simultaneously | `by design` |
| #2 | `ta-dig` race condition — multiple family members claim the crispy rice | `wontfix` (heated) |
| #3 | Haft Seen item placement causes unresolved merge conflicts at every family gathering | `ongoing` |
| #4 | `eidi` inflation — the amount expected by children increases 12% per year | `known issue` |
| #5 | Goldfish mortality spikes post-Nowruz — `sizdah-bedar` branch frequently releases fish into canals | `environmental concern` |
| #6 | Visitors appear without prior notification between Day 1–13 | `feature, not bug` |
| #7 | Ash-e-reshteh noodles represent the threads of fate — nobody agrees on the recipe | `unresolvable philosophical conflict` |
| #8 | "Just one more day" on Sizdah Bedar | `memory leak` |

---

## Migration Guide

### From Gregorian New Year (`v2025.12.31`)

You have already been running this. It is fine. But consider:

```diff
- January 1st: hungover, cold, dark, arbitrary
+ March 20th: spring, nature literally blooming, food is better,
+             the sun itself shows up to confirm the date
```

**Breaking changes:** None. Nowruz is non-breaking by definition.

**New in 1405:**
- Same as 1403, but with more hope
- Deprecated: carrying last year's regrets into the new year (please remove)
- Added: permission to start fresh

---

## FAQ

**Q: When exactly does Nowruz start?**
A: At the precise moment of the vernal equinox. Families will begin the sofreh countdown with a TV broadcast, collectively staring at numbers until the year ticks over, then immediately saying `نوروز مبارک` while crying a little. It is perfect.

**Q: What if I don't have all seven haft-seen items?**
A: Historically, civilizations have survived. But your aunt will notice, mention it to your mother, and it will be discussed for eleven months.

**Q: Can I do Nowruz if I'm not Iranian/Persian?**
A: Yes. Bring an appetite, take off your shoes at the door, and accept that you will leave with more food than you arrived with.

**Q: Is the goldfish mandatory?**
A: The goldfish is mandatory.

**Q: What happens on Sizdah Bedar (day 13)?**
A: You go outside. You tie the sabzeh in a knot and throw it in running water (releasing the old year's troubles). You eat. You refuse to go home. You are coerced home. You are already planning next year.

**Q: Why 13 days?**
A: Because 12 was not enough and 14 was too many. This was decided approximately 3,000 years ago and is no longer open for debate.

**Q: My sabzeh died before Nowruz.**
A: This is a known issue. Grow backup sabzeh. Start in late February. Do not tell your grandmother it died. 

---

## Contributing

Nowruz has 300 million active contributors and accepts contributions in the following formats:

- **Cooking** — accepted, celebrated, consumed
- **Visiting relatives** — mandatory PR, cannot be closed
- **Planting sabzeh** — small contribution, high impact
- **Giving eidi** — financial contribution, tax-deductible in the spirit economy
- **Calling someone you've been meaning to call** — most impactful PR of the release cycle
- **Forgiving something from last year** — advanced contribution, deeply respected

**PR review process:** Your grandmother is the CODEOWNER. All changes require her approval. She will not use GitHub. She will tell you in person, over food.

---

## Sponsors

This project has been sponsored, in various centuries, by:

- ☀️ **The Sun** — primary infrastructure sponsor since forever
- 🌍 **Earth's axial tilt** — enables the equinox trigger (23.5°, non-negotiable)
- 🌿 **Spring itself** — environmental sponsor
- 👩‍🍳 **Every Persian grandmother who has ever lived** — catering sponsor
- 🐟 **The goldfish** — silent sponsor, present at every sofreh

---

## Changelog

```
v1405.0.0  (March 2026)
  - Another year. Same beauty. New hope.
  - feat: you are still here (underrated)
  - fix: last year's mistakes not carried forward (manual step required)

v1403.0.0  (March 2025)
  - stable release
  - chore: cleaned house before guests arrived

v1000.0.0  (circa 1000 CE)
  - feat: Ferdowsi's Shahnameh merged into cultural canon
  - Nowruz described in verse that still compiles

v1.0.0  (circa 3000 BCE)
  - initial commit by Zoroastrian astronomers
  - no tests (the sun was the test)
  - no README (you are reading the first one)
  - shipped anyway
  - still running
```

---

<div align="center">

## نوروز 1405 مبارک 🌸

*May your sabzeh grow tall,*
*your ta-dig be crispy,*
*your builds be green,*
*and your logs be clean.*

**`git commit -m "feat: new year, new self"`**

---

*Nowruz has been open-source since 3000 BCE.*
*No license needed. It belongs to everyone.*
*⭐ Star this repo if spring made you feel something.*

</div>
