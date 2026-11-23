# 🧪 Dynamic LLM Cross-Validation Benchmark (v7.0 - Hardened)

A multi-model cross-evaluation harness testing **8 local Ollama models** across **168 total runs** (`56` generator-validator pairs × `3` evaluation lenses). Each model acts as both a **Generator**—tasked with modeling a sovereign debt crisis and global monetary unwind—and a **Validator**—grading peer outputs iteratively across *Conciseness*, *Technical* rigor, and *Objectivity*.

---

## 🎯 Benchmark Prompt & Provenance (`todays_q.txt`)

* **Prompt Date:** `23.11.26`
* **Prompt Owner / Author:** `dolphin3:latest` (Custom Question via `DOORMAN_TICKET` + `CROUPIER_REWRITE`, drift: `0.647`)
* **Domain:** Macroeconomics, Sovereign Debt Mechanics & Geopolitics

> **Exact Benchmark Question:**
> *"Analyze the structural, monetary, and geopolitical consequences if foreign central banks, institutional investors, and primary dealers cease absorbing net new U.S. Treasury issuance, effectively treating American sovereign debt as a toxic, un-investable asset class. Contrast the post-1971 petrodollar and reserve-currency recycling regime—which allowed persistent fiscal deficits to be funded at artificially suppressed yields—against the hard mathematical constraints of compounding debt-service costs, negative real returns, and failed Treasury auctions. Examine the structural mechanics of the resulting sovereign debt doom loop, tracing how the Federal Reserve is forced to choose between allowing catastrophic yield spikes (triggering domestic banking insolvency and pension collapse) or engaging in overt yield-curve control and debt monetization (accelerating currency debasement and stagflationary feedback loops). Provide a quantitative or systems-level assessment of the global financial unwind, modeling how the loss of the 'risk-free' Treasury benchmark triggers collateral liquidations across repo markets, forces bilateral trade settlement outside the SWIFT/dollar system, and compels severe domestic austerity and entitlement restructuring."*

---

## 📊 Executive Summary

* **Run Date:** November 23, 2026
* **Total Runtime:** `08:25:15`
* **Pass Rate:** `167 / 168` (`99.4%`) | `1` Timeout/Error (`Case 109`)
* **Global Mean Score:** `87.33 / 100` (reported as `87.3` in log summary)
* **Evaluation Lenses:** `Conciseness`, `Technical`, `Objectivity`

---

## 🏆 Generator Leaderboard (Ranked by Avg. Score)

*Note: Ties in average score are broken by fastest average pass runtime. `phi4:latest` experienced 1 timeout error (`2085.03s`) on Case 109; its average time excludes that outlier to reflect normal generation speed.*

| Rank | Generator Model | Pass Rate | Avg. Score | Avg. Loops | Avg. Time (Pass) |
| :--- | :--- | :---: | :---: | :---: | :---: |
| 🥇 **1** | `huihui_ai/qwen3-abliterated:8b` | 21 / 21 | **88.86** | 1.05 | 193.41s |
| 🥈 **2** | `llama3.2:3b` | 21 / 21 | **87.71** | 1.10 | **61.18s** |
| 🥉 **3** | `dolphin3:latest` *(Prompt Author)* | 21 / 21 | **87.57** | 1.10 | 109.24s |
| **4** | `mistral-nemo:12b` | 21 / 21 | **87.57** | 1.14 | 179.17s |
| **5** | `qwen2.5-coder:14b` | 21 / 21 | **87.57** | 1.10 | 247.70s |
| **6** | `phi4:latest` | 20 / 21 | **86.80** | 1.10 | 324.71s* |
| **7** | `qwen2.5-coder:7b` | 21 / 21 | **86.38** | 1.10 | 86.75s |
| **8** | `jaahas/gemma-2-9b-it-abliterated:latest` | 21 / 21 | **86.14** | 1.00 | 138.94s |

---

## ⚖️ Validator Strictness & Retry Behavior

How each model behaved when acting as an automated judge for the other 7 models:

| Validator Model | Avg. Score Given | Avg. Loops Forced | Retry Rate | Avg. Eval Time | Judge Profile |
| :--- | :---: | :---: | :---: | :---: | :--- |
| `qwen2.5-coder:14b` | **85.00** | 1.10 | 9.5% | 157.81s | Strictest baseline scorer |
| `jaahas/gemma-2-9b-it-abliterated:latest` | **86.48** | **1.33** | **28.6%** | 181.14s | Most demanding critic (forced retries on nearly 1 in 3 runs) |
| `huihui_ai/qwen3-abliterated:8b` | **86.50** | 1.20 | 20.0% | 183.52s | Strict on conciseness; frequent retries |
| `qwen2.5-coder:7b` | **86.67** | 1.00 | 0.0% | 141.97s | Fast single-pass grader |
| `phi4:latest` | **86.90** | 1.00 | 0.0% | 203.94s | Slowest single-pass validator |
| `dolphin3:latest` | **88.33** | 1.05 | 4.8% | 148.93s | Generous; awarded two `100` scores (`Cases 66, 87, 150` — three total) |
| `llama3.2:3b` | **88.48** | 1.00 | 0.0% | **141.56s** | Fastest, lenient scorer |
| `mistral-nemo:12b` | **90.24** | 1.00 | 0.0% | 175.50s | Most generous grader on macroeconomic/technical prose |

---

## 🔍 Performance by Evaluation Lens

| Evaluation Lens | Pass Rate | Avg. Score | Avg. Loops | Avg. Time (Pass) |
| :--- | :---: | :---: | :---: | :---: |
| **Technical** | 56 / 56 | **87.73** | 1.00 | 164.27s |
| **Objectivity** | 56 / 56 | **87.64** | 1.02 | 166.73s |
| **Conciseness** | 55 / 56 | **86.60** | **1.24** | 169.13s |

---

## 💡 Key Takeaways & Insights

1. **`qwen3-abliterated:8b` Takes Back-to-Back #1 Finishes:** Scoring **88.86** overall (`+1.53` above the global mean), `qwen3-abliterated:8b` maintained its top spot even on a purely macroeconomic/monetary systems prompt—proving its strength isn't limited to taboo or politically sensitive topics.
2. **Massive Punch-Above-Weight Performance by `llama3.2:3b`:** Despite having only 3B parameters, `llama3.2:3b` finished **2nd overall (`87.71`)** while averaging just **61.18s** per pass—more than **3× faster** than 1st-place `qwen3-abliterated:8b` (`193.41s`) and **5.3× faster** than `phi4:latest` (`324.71s`).
3. **Conciseness Was the Primary Bottleneck:** Unlike the previous sociopolitical benchmark (where *Objectivity* caused the most friction), *Technical* (`1.00` avg loops) and *Objectivity* (`1.02` avg loops) passed effortlessly here. Instead, **Conciseness** drove almost every multi-loop retry (`1.24` avg loops) as models struggled to compress dense monetary mechanics (repo liquidations, yield-curve control, SWIFT settlement) without sacrificing required depth.
4. **Recurring `Case 109` Deadlock (`phi4:latest` → `qwen3-abliterated:8b`):** For the second consecutive benchmark run, the exact same pairing (`GEN: phi4:latest | VAL: huihui_ai/qwen3-abliterated:8b | LENS: conciseness`) hung for ~35 minutes (`2085.03s`) before throwing an `ERROR`, pointing to a deterministic prompt/token-loop edge case between those two specific models.
