# Results: Dense Mode vs Cave Talk

**Date:** 2026-04-07
**Method:** Word count x 1.3 as token proxy (BPE tokenizers average ~1.3 tokens/word for English technical text)

---

## Output Token Comparison (6 Tasks x 4 Styles)

| Task | Type | Normal | Caveman Full | Caveman Ultra | Dense Mode |
|------|------|--------|-------------|---------------|------------|
| 1. React re-render | Prose | 296 | 142 | 57 | 125 |
| 2. JWT middleware fix | Code-heavy | 328 | 153 | 64 | 124 |
| 3. Micro vs mono | Prose | 354 | 181 | 55 | 147 |
| 4. Security review | Mixed | 393 | 155 | 65 | 152 |
| 5. Docker build | Code-heavy | 308 | 164 | 107 | 148 |
| 6. Refactor + tests | Tool-heavy | 255 | 101 | 77 | 100 |
| **Average** | | **322** | **149** | **71** | **133** |

## Reduction vs Normal (%)

| Task | Caveman Full | Caveman Ultra | Dense Mode |
|------|-------------|---------------|------------|
| 1. React re-render | 52% | 81% | 58% |
| 2. JWT middleware fix | 53% | 80% | 62% |
| 3. Micro vs mono | 49% | 84% | 58% |
| 4. Security review | 61% | 83% | 61% |
| 5. Docker build | 47% | 65% | 52% |
| 6. Refactor + tests | 60% | 70% | 61% |
| **Average** | **54%** | **77%** | **59%** |

---

## Information Completeness (1-5 scale)

5 = all actionable info present | 1 = critical info missing

| Task | Normal | Caveman Full | Caveman Ultra | Dense Mode |
|------|--------|-------------|---------------|------------|
| 1. React re-render | 5 | 5 | 4 | 5 |
| 2. JWT middleware fix | 5 | 5 | 4 | 5 |
| 3. Micro vs mono | 5 | 5 | 3 | 5 |
| 4. Security review | 5 | 4 | 3 | 5 |
| 5. Docker build | 5 | 5 | 5 | 5 |
| 6. Refactor + tests | 5 | 5 | 5 | 5 |
| **Average** | **5.0** | **4.8** | **4.0** | **5.0** |

---

## Readability (1-5 scale)

5 = reads naturally | 1 = requires mental parsing

| Task | Normal | Caveman Full | Caveman Ultra | Dense Mode |
|------|--------|-------------|---------------|------------|
| 1. React re-render | 5 | 4 | 2 | 4 |
| 2. JWT middleware fix | 5 | 4 | 3 | 4 |
| 3. Micro vs mono | 5 | 4 | 2 | 4 |
| 4. Security review | 5 | 4 | 3 | 5 |
| 5. Docker build | 5 | 5 | 4 | 5 |
| 6. Refactor + tests | 5 | 5 | 4 | 5 |
| **Average** | **5.0** | **4.3** | **3.0** | **4.5** |

---

## Context Compounding Analysis

Claude resends the full conversation on every turn. Each response persists in context for all subsequent turns.

**30-turn coding session:**

| Style | Avg tokens/response | Cumulative context cost* | Saved vs Normal |
|-------|--------------------|---------------------------------|-----------------|
| Normal | 322 | 149,730 | — |
| Caveman Full | 149 | 69,285 | 80K |
| Caveman Ultra | 71 | 33,015 | 117K |
| Dense Mode | 133 | 61,845 | 88K |

*Each response is re-sent on all subsequent turns. Sum of 1 to 30 = 465.

A 30-turn session costs roughly 500K-2M total tokens. Dense mode's 88K savings = **4-18% of total session cost**.

---

## Composite Scorecard

| Metric | Normal | Caveman Full | Caveman Ultra | Dense Mode |
|--------|--------|-------------|---------------|------------|
| Token reduction | 0% | 54% | 77% | 59% |
| Info completeness | 5.0 | 4.8 | 4.0 | 5.0 |
| Readability | 5.0 | 4.3 | 3.0 | 4.5 |
| 30-turn context savings | 0 | 80K | 117K | 88K |
| % of total session saved | 0% | 4-16% | 6-23% | 4-18% |
| Daily usability | High | Medium | Low | High |

**Winner: Dense Mode.** Best balance of savings, completeness, and readability. Saves 5% more than caveman full, loses zero information, and reads like a professional.
