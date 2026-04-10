---
layout: page
title: LLM ranking
permalink: /llm-ranking/
description: LLM ranking including proprietary and open models
nav: false
nav_order: 4
images:
  lightbox2: true
---

I benchmarked dozens of LLMs across coding and general reasoning tasks, then mapped their performance against API pricing. This page breaks down the rankings and highlight the best value picks in each category.

Updated on Apr. 10 2026.

## Introduction

I conducted a statistical analysis of LLM rankings. My specific goals were:

1. Derive the average ranking of models from multiple LLM leaderboards.
2. Group models into tiers with similar performance levels.
3. Plot model performance against relative cost to identify which models offer performance comparable to top-tier options at a lower price.

By analyzing the results, we can identify the highest-performing models as well as those offering the optimal cost-benefit ratio.

## Results

### General reasoning

The general reasoning ranking, aggregated across seven leaderboards, is dominated at the top by proprietary models—with open-weights challengers competitive from tier 2 onward.

```
+-------------------------------------------------------------------------------------+
| Rank  | Model                   | Avg Pctl  | Std Dev   | # Benchmarks  | Rel. Cost |
+-------------------------------------------------------------------------------------+
| 1     | gemini-pro31            | 0.041     | 0.078     | 7             | 1.000     |
| 2     | gpt54                   | 0.083     | 0.115     | 6             | 1.124     |
| 3     | mythos                  | 0.101     | 0.001     | 2             | 6.424     |
| 4     | opus46                  | 0.106     | 0.097     | 7             | 1.820     |
| 5     | gpt-pro54               | 0.114     | 0.109     | 3             | 13.490    |
| 6     | sonnet46                | 0.129     | 0.142     | 6             | 1.092     |
| 7     | muse                    | 0.139     | 0.086     | 3             | 1.820     |
| 8     | grok42                  | 0.181     | 0.149     | 6             | 13.490    |
| 9     | gpt-codex53             | 0.208     | 0.050     | 2             | 1.006     |
| 10    | glm51                   | 0.214     | 0.166     | 7             | 0.415     |
| 11    | kimi25                  | 0.241     | 0.163     | 7             | 0.257     |
| 12    | qwen35                  | 0.245     | 0.167     | 4             | 0.184     |
| 13    | gemini-flash3           | 0.249     | 0.246     | 7             | 0.214     |
| 14    | gpt-mini54              | 0.259     | 0.172     | 4             | 0.338     |
| 15    | qwen3-max               | 0.272     | 0.133     | 5             | 0.471     |
| 16    | gemini-flash-lite31     | 0.274     | 0.144     | 4             | 0.126     |
| 17    | gemma4-31               | 0.286     | 0.219     | 6             | 0.041     |
| 18    | deepseek32              | 0.290     | 0.163     | 7             | 0.049     |
| 19    | qwen35-max              | 0.291     | N/A       | 1             | 0.749     |
| 20    | minimax27               | 0.318     | 0.145     | 4             | 0.107     |
| 21    | qwen3-235b              | 0.365     | N/A       | 1             | 0.642     |
| 22    | grok-fast41             | 0.373     | 0.175     | 6             | 0.051     |
| 23    | haiku45                 | 0.404     | 0.219     | 6             | 0.364     |
| 24    | qwen3-80b               | 0.442     | N/A       | 1             | 0.171     |
| 25    | glm-flash47             | 0.507     | 0.112     | 2             | 0.036     |
| 26    | llama-maverick          | 0.583     | N/A       | 1             | 0.118     |
| 27    | gpt-oss-120b            | 0.584     | 0.201     | 6             | 0.086     |
| 28    | qwen35-35b              | 0.635     | N/A       | 1             | 0.107     |
| 29    | qwen3-32b               | 0.637     | 0.203     | 3             | 0.086     |
| 30    | gpt-oss-20b             | 0.647     | 0.160     | 3             | 0.032     |
| 31    | qwen3-coder-30b         | 0.840     | N/A       | 1             | 0.107     |
| 32    | nemotron-nano3          | 0.885     | N/A       | 1             | 0.043     |
+-------------------------------------------------------------------------------------+
```

<a href="/assets/img/clippies/general_ranking.png" data-lightbox="roadtrip">
  <img src="/assets/img/clippies/general_ranking.png" alt="General Ranking" style="width: 45%;">
</a>
<a href="/assets/img/clippies/general.png" data-lightbox="roadtrip">
  <img src="/assets/img/clippies/general.png" alt="General Scores" style="width: 45%;">
</a>

**Figure 1. Left panel:** Overall ranking. Circle size proportional to log10(API cost). **Right panel:** Credit cost (log scale) on the x-axis and average percentile score on the y-axis (inverted, so the best models appear at the top). The upper-left corner is the sweet spot: best performance at lowest cost. In both panels, error bars show ±1σ. Colors indicate statistical tier. Circles mark proprietary models; squares mark open-weights models. 


### Coding and agentic coding

The coding ranking, drawn from nine benchmarks including demanding agentic evaluations, reveals a two-model tier-1 club at the top—and a wide, cost-diverse tier 2 below it.

```
+-------------------------------------------------------------------------------------+
| Rank  | Model                   | Avg Pctl  | Std Dev   | # Benchmarks  | Rel. Cost |
+-------------------------------------------------------------------------------------+
| 1     | mythos                  | 0.000     | 0.000     | 3             | 1.000     |
| 2     | gpt54                   | 0.052     | 0.091     | 7             | 0.175     |
| 3     | gpt-codex53             | 0.147     | 0.096     | 6             | 0.158     |
| 4     | glm51                   | 0.160     | 0.099     | 6             | 0.065     |
| 5     | opus46                  | 0.164     | 0.115     | 8             | 0.283     |
| 6     | grok42                  | 0.189     | 0.121     | 3             | 2.833     |
| 7     | sonnet46                | 0.206     | 0.136     | 8             | 0.170     |
| 8     | gemini-pro31            | 0.240     | 0.255     | 8             | 0.156     |
| 9     | gpt-mini54              | 0.250     | 0.097     | 6             | 0.053     |
| 10    | minimax27               | 0.271     | 0.098     | 6             | 0.017     |
| 11    | qwen35                  | 0.286     | 0.127     | 5             | 0.029     |
| 12    | grok-fast41             | 0.288     | 0.179     | 5             | 0.008     |
| 13    | gemma4-31               | 0.335     | 0.151     | 4             | 0.006     |
| 14    | kimi25                  | 0.349     | 0.240     | 7             | 0.040     |
| 15    | deepseek32              | 0.379     | 0.233     | 7             | 0.008     |
| 16    | minimax25               | 0.396     | 0.219     | 8             | 0.017     |
| 17    | haiku45                 | 0.396     | 0.220     | 8             | 0.057     |
| 18    | gemini-flash3           | 0.416     | 0.283     | 7             | 0.033     |
| 19    | qwen3-max               | 0.428     | 0.200     | 4             | 0.073     |
| 20    | gemini-flash-lite31     | 0.456     | 0.160     | 5             | 0.020     |
| 21    | gpt-oss-120b            | 0.599     | 0.168     | 5             | 0.013     |
| 22    | glm-flash47             | 0.609     | N/A       | 1             | 0.006     |
| 23    | nemotron-super3         | 0.613     | 0.176     | 4             | 0.013     |
| 24    | gpt-oss-20b             | 0.700     | 0.186     | 4             | 0.005     |
| 25    | nemotron-nano3          | 0.830     | 0.051     | 2             | 0.007     |
| 26    | qwen3-coder-30b         | 1.000     | N/A       | 1             | 0.017     |
+-------------------------------------------------------------------------------------+
```

<a href="/assets/img/clippies/coding_ranking.png" data-lightbox="roadtrip">
  <img src="/assets/img/clippies/coding_ranking.png" alt="Coding Ranking" style="width: 45%;">
</a>
<a href="/assets/img/clippies/coding.png" data-lightbox="roadtrip">
  <img src="/assets/img/clippies/coding.png" alt="Coding Scores" style="width: 45%;">
</a>

**Figure 2:** Same conventions as Figure 1.


## Methods

### Benchmark selection and data collection

I manually collected model rankings from established LLM leaderboards on April 10, 2026, choosing benchmarks that cover different evaluation angles.

*General reasoning* draws on seven leaderboards:

- [LiveBench](https://livebench.ai) — regularly refreshed, multi-domain evaluation designed to resist contamination
- [Arena](https://arena.ai/leaderboard) — ELO-style ranking from blind human preference votes (a popular-preference signal rather than a strict accuracy benchmark, but informative nonetheless)
- [Artificial Analysis Intelligence Index](https://artificialanalysis.ai) — a composite of 10 evaluations including GPQA Diamond, Humanity's Last Exam, SciCode, and others
- [Scale's Humanity's Last Exam](https://scale.com/leaderboard/humanitys_last_exam) — expert-level reasoning questions
- [SimpleBench](https://simple-bench.com) — commonsense and reasoning-trap questions designed to expose systematic errors
- [Dubesor LLM Leaderboard](https://dubesor.de/benchtable) — hand-graded multi-domain evaluation
- [GPQA Diamond](https://scale.com/leaderboard/gpqa) — graduate-level science questions spanning biology, chemistry, and physics

*Coding and agentic coding* draws on nine leaderboards:

- The three leaderboards previously mentioned (LiveBench coding subcategory, Arena, and Artificial Analysis agentic and coding sub-scores) plus six focused evaluations below.
- [Scale's SWE Bench Pro Public](https://scale.com/leaderboard/swe_bench_pro_public)
- [Berkeley Function-Calling Leaderboard (BFCL)](https://gorilla.cs.berkeley.edu/leaderboard.html) — tool and function call accuracy
- [SWE-bench Verified](https://www.swebench.com) — real-world GitHub issue resolution
- [Terminal-Bench 2.0](https://www.tbench.ai/leaderboard/terminal-bench/2.0) — agentic terminal and shell-based coding tasks
- [SWE-Atlas Codebase QnA](https://sweatlas.com) — question-answering over large, real-world codebases

I selected 30+ models spanning the current frontier: proprietary leaders from OpenAI (GPT-5.4 family: gpt54, gpt-pro54, gpt-mini54, gpt-codex53), Anthropic (Claude 4.5+ family including the unreleased Mythos), Google (Gemini 3.1 family and Gemma 4), xAI (Grok 4.2 and Grok Fast 4.1), and Meta (unreleased Muse), plus open-weights challengers from DeepSeek (V3.2), Moonshot AI (Kimi K2.5), Z AI (GLM 5.1), MiniMax (M2.5/M2.7), Alibaba (Qwen 3/3.5 variants), Meta/Google (Llama 4 Maverick, Gemma 4), and NVIDIA (Nemotron Nano/Super 3).

### Percentile normalization

Different leaderboards evaluate different numbers of models. Being ranked 5th out of 600 models is far more impressive than 5th out of 30. To make cross-benchmark comparisons fair, I normalize each rank to a fractional percentile:

$$\text{percentile} = \frac{\text{rank}}{\text{total models evaluated}}$$

This puts every score on a 0–1 scale (0 = best, 1 = worst). A model that's 3rd out of 600 on Arena (percentile 0.005) and 2nd out of 50 on LiveBench (percentile 0.04) now live on the same axis.

### Aggregation and penalties

A model's composite score is the unweighted arithmetic mean of its percentiles across all benchmarks it appears on. To avoid boosting the ranking of a model that happens to score well on the single benchmark it was evaluated on, a sparse-data penalty is added: +0.25 for one benchmark, +0.10 for two, and zero for three or more.

### Statistical tiering

Rather than treating every rank difference as meaningful, I group models into *tiers* using the "indistinguishable from best" method:

1. The best model becomes the tier leader.
2. Every remaining model whose $$\pm 1\sigma$$ confidence interval overlaps with the leader's joins the same tier.
3. Remove the tier, promote the next-best model to leader, and repeat.

Formally, *model i* is grouped with *leader j* if:

$$\text{score}_i + \sigma_i \geq \text{score}_j - \sigma_j$$

In plain terms: if B's best-case performance could plausibly reach A's worst-case, we can't confidently distinguish them. This acknowledges that benchmark scores carry noise and avoids drawing artificial distinctions where the evidence doesn't support them. Models evaluated on fewer than two benchmarks have no standard deviation, so the average σ across all other models is used as a stand-in.

### Cost metric

For consistent cost comparison, I normalize each model's Poe credit cost per 1,000 tokens to the cost of the best-ranked model in each category (Rel. Cost = 1 for the top model; values below 1 are cheaper, above 1 are more expensive). This removes absolute pricing noise while preserving the cost ratios that matter for budget decisions. Absolute credit prices vary by provider and plan, but the relative ordering remains stable across models on the same platform.


## Conclusions

- For coding, the tier-1 club is now just three models: Anthropic's unreleased *Mythos*, *GPT-5.4* and *Gemini 3.1 Pro*. If you need that peak performance today and cost is secondary, those are the top LLM models.
- There is a large tier-2 coding population that includes Claude Opus 4.6, Sonnet 4.6, GLM 5.1, GPT-Codex 5.3, GPT Mini 5.4 and Minimax 2.7, among others. This cohort is statistically indistinguishable from each other and close to the top.
- For general reasoning, all eight tier-1 models are proprietary. The best open-weights pick here is *GLM 5.1*, landing at rank 10.
- Best value for general reasoning: *Kimi K2.5*, *Qwen 3.5*, *Gemini Flash 3* and lite version, and *Gemma 4 3.1* deliver tier-2-or-better performance at well below the cost of the top models.
- Best value for coding and agentic tasks (e.g. [opencode](https://opencode.ai)): *Grok Fast 4.1*, *Gemma 4 3.1*, *MiniMax M2.7*, *Qwen 3.5*, *Kimi K2.5*, and *Gemini Flash 3* all sit in the upper-left of the cost-performance plot.
- For the tightest budgets, *DeepSeek V3.2*, *Grok Fast 4.1* and *Gemma 4* remain the standout value picks.

---

## Reproducibility

All code, data files, and full methodology details are [here](https://github.com/rsnemmen/rank-clippies). 
