## Layout — Bullets

Render the report content in this layout. No tables: each issue is a block, so
long text never breaks alignment in a terminal.

```
# ATS Resume Check — <title>

**Overall readiness: 🟡 Moderate**
<one-sentence rationale>

## 📊 At a glance
- **Layout & Formatting** — <verdict>
- **Structure & Headings** — <verdict>
- **Keywords & Optimization** — <e.g. "5 / 5 stated requirements met">
- **Content Quality** — <verdict>
- **Contact & Length** — <verdict>

## 🔧 Issues & Fixes  *(worst first)*

**❌ <one of the five Area names> — <short problem title>**
   Problem: <what's wrong + why it matters>
   Fix: <concrete fix>

**⚠️ Keywords & Optimization — title line lacks the JD's exact title term**
   Problem: <resume title vs JD title — why a literal scan won't match>
   Fix: <add a JD-matched headline>

**⚠️ Content Quality — <short problem title>**
   Problem: <what's wrong + why>
   Fix: <fix>
   Rewrite: "<rewritten bullet>"
(…one block per issue, all ❌ blocks before all ⚠️ blocks.)

## ✅ Passing
- **<one of the five Area names>** — <what's working>

## 🎯 Keyword & Skills Match
*Reference — data only; actionable gaps also appear in Issues & Fixes.*
- **Must-have hard skills — matched (literal):** a, b, c
- **Must-have hard skills — ❌ missing (literal):** x, y, z
- **Covered semantically (not by exact keyword):**
  - **<keyword>** — <where/how it's implied>
- **Soft skills:** matched: … · missing: …

## 📝 Other observations
*(Only if there are any. Not graded.)*
- <anything worth saying that falls outside the five categories>

---
*Heuristic ATS-readiness check: strong guidance, not a guaranteed pass. It does not replicate any specific vendor's parser.*
```

Bullets-layout rules: **Issues & Fixes** holds only ⚠️/❌ blocks, all ❌ blocks
before all ⚠️ blocks; the `Rewrite:` line appears on content items only.
**Passing** holds only ✅ items — an Area with nothing passing is simply **absent
from the list**, never an entry saying it has nothing to report.
