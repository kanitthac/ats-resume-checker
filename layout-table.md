## Layout — Table

Render the report content in this layout.

```
# ATS Resume Check — <title>

> **Overall readiness: 🟡 Moderate**
> <one-sentence rationale>

## 📊 At a glance
| Category | Verdict |
|---|---|
| Layout & Formatting | <verdict> |
| Structure & Headings | <verdict> |
| Keywords & Optimization | <e.g. "5 / 5 stated requirements met"> |
| Content Quality | <verdict> |
| Contact & Length | <verdict> |

## 🔧 Issues & Fixes
*Worst first — all ❌ rows above all ⚠️ rows.*
| Priority | Area | Problem | How to fix |
|---|---|---|---|
| ❌ | <one of the five Area names> | <what's wrong + brief why it matters> | <concrete fix> |
| ⚠️ | Keywords & Optimization | <e.g. title line lacks the JD's exact title term> | <e.g. add a JD-matched headline> |
| ⚠️ | Content Quality | <what's wrong + why> | <fix>. **Rewrite:** "<rewritten bullet>" |

## ✅ Passing
| Area | What's working |
|---|---|
| <one of the five Area names> | <what passed> |

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

Table-layout rules: **Issues & Fixes** holds only ⚠️/❌ (❌ rows first); the
`**Rewrite:**` sits inline in the "How to fix" cell for content items only.
**Passing** holds only ✅ items.
