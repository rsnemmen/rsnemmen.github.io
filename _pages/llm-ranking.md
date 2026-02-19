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

Updated on Feb. 19 2026.

## Introduction

I conducted a statistical analysis of LLM rankings. My specific goals were:

1. Derive the average ranking of models from multiple LLM leaderboards.
2. Group models into tiers with similar performance levels.
3. Plot model performance against relative cost to identify which models offer performance comparable to top-tier options at a lower price.

By analyzing the results, we can identify the highest-performing models as well as those offering the optimal cost-benefit ratio.

## Results

### General reasoning

The general reasoning ranking, aggregated across four leaderboards, reveals a tight race at the top—and a perhaps surprising amount of statistical ambiguity below it.

```
+------------------------------------------------------------------------------------+
| Rank  | Model                   | Avg Pctl  | Std Dev   | # Benchmarks  | Cost/1k  |
+------------------------------------------------------------------------------------+
| 1     | opus46                  | 0.015     | 0.008     | 4             | 850      |
| 2     | gpt52                   | 0.069     | 0.046     | 4             | 470      |
| 3     | gemini-pro3             | 0.080     | 0.044     | 4             | 370      |
| 4     | sonnet46                | 0.124     | 0.079     | 4             | 510      |
| 5     | glm5                    | 0.144     | 0.095     | 4             | 140      |
| 6     | kimi25                  | 0.167     | 0.085     | 4             | 120      |
| 7     | gpt-codex53             | 0.179     | 0.005     | 2             | 470      |
| 8     | qwen3-max               | 0.220     | 0.089     | 3             | 220      |
| 9     | grok41                  | 0.233     | 0.146     | 4             | 600      |
| 10    | grok-fast41             | 0.243     | 0.116     | 3             | 24       |
| 11    | gpt-pro52               | 0.244     | 0.022     | 2             | 5700     |
| 12    | gemini-flash3           | 0.261     | 0.291     | 4             | 100      |
| 13    | deepseek32              | 0.261     | 0.105     | 4             | 23       |
| 14    | haiku45                 | 0.290     | 0.076     | 3             | 170      |
| 15    | qwen35                  | 0.343     | 0.074     | 2             | 86       |
| 16    | minimax25               | 0.358     | 0.128     | 4             | 50       |
| 17    | qwen3-235b              | 0.395     | 0.190     | 3             | 300      |
| 18    | qwen3-80b               | 0.462     | 0.178     | 3             | 80       |
| 19    | glm-flash47             | 0.497     | 0.146     | 3             | 17       |
| 20    | gpt-instant52           | 0.523     | 0.289     | 4             | 470      |
| 21    | gpt-oss-120b            | 0.552     | 0.184     | 4             | 40       |
| 22    | qwen3-32b               | 0.699     | 0.181     | 4             | 40       |
| 23    | llama-maverick          | 0.709     | 0.187     | 3             | 55       |
| 24    | gpt-oss-20b             | 0.793     | 0.087     | 2             | 15       |
| 25    | nemotron-nano3          | 0.856     | N/A       | 1             | 20       |
| 26    | qwen3-coder-30b         | 0.904     | N/A       | 1             | 50       |
+------------------------------------------------------------------------------------+
```

<a href="/assets/img/clippies/ranks_general_ranking.png" data-lightbox="roadtrip">
  <img src="/assets/img/clippies/ranks_general_ranking.png" alt="General Ranking" style="width: 45%;">
</a>
<a href="/assets/img/clippies/ranks_general.png" data-lightbox="roadtrip">
  <img src="/assets/img/clippies/ranks_general.png" alt="General Scores" style="width: 45%;">
</a>

**Figure 1. Left panel:** Overall ranking. Circle size proportional to log10(API cost). **Right panel:** Credit cost (log scale) on the x-axis and average percentile score on the y-axis (inverted, so the best models appear at the top). The upper-left corner is the sweet spot: best performance at lowest cost. In both panels, error bars show ±1σ. Colors indicate statistical tier. Circles mark proprietary models; squares mark open-weights models. 


### Coding and agentic coding

The coding ranking, drawn from seven benchmarks including demanding agentic evaluations, tells a more subtle story.

```
+------------------------------------------------------------------------------------+
| Rank  | Model                   | Avg Pctl  | Std Dev   | # Benchmarks  | Cost/1k  |
+------------------------------------------------------------------------------------+
| 1     | opus46                  | 0.025     | 0.030     | 7             | 850      |
| 2     | sonnet46                | 0.065     | 0.039     | 7             | 510      |
| 3     | gpt-codex53             | 0.094     | 0.090     | 6             | 470      |
| 4     | gpt52                   | 0.117     | 0.072     | 7             | 470      |
| 5     | gemini-pro3             | 0.121     | 0.133     | 7             | 370      |
| 6     | kimi25                  | 0.154     | 0.106     | 7             | 120      |
| 7     | glm5                    | 0.165     | 0.187     | 7             | 140      |
| 8     | qwen35                  | 0.189     | 0.105     | 3             | 86       |
| 9     | gemini-flash3           | 0.207     | 0.142     | 7             | 100      |
| 10    | gpt-pro52               | 0.239     | 0.139     | 2             | 5700     |
| 11    | minimax25               | 0.284     | 0.256     | 6             | 50       |
| 12    | deepseek32              | 0.299     | 0.171     | 7             | 23       |
| 13    | grok-fast41             | 0.336     | 0.276     | 4             | 20       |
| 14    | mistral                 | 0.345     | N/A       | 1             | 400      |
| 15    | haiku45                 | 0.364     | 0.257     | 7             | 170      |
| 16    | glm-flash47             | 0.386     | 0.135     | 3             | 17       |
| 17    | qwen3-max               | 0.407     | 0.252     | 3             | 220      |
| 18    | grok41                  | 0.464     | 0.290     | 6             | 600      |
| 19    | qwen3-235b              | 0.473     | 0.312     | 6             | 300      |
| 20    | gpt-instant52           | 0.582     | 0.413     | 6             | 470      |
| 21    | qwen3-coder-30b         | 0.636     | 0.420     | 4             | 50       |
| 22    | gpt-oss-120b            | 0.673     | 0.180     | 5             | 40       |
| 23    | qwen3-80b               | 0.707     | 0.397     | 3             | 80       |
| 24    | llama-maverick          | 0.770     | 0.421     | 5             | 55       |
| 25    | gpt-oss-20b             | 0.781     | 0.241     | 4             | 15       |
| 26    | qwen3-32b               | 0.983     | 0.267     | 3             | 40       |
| 27    | nemotron-nano3          | 1.000     | N/A       | 1             | 20       |
+------------------------------------------------------------------------------------+
```

<a href="/assets/img/clippies/ranks_coding_ranking.png" data-lightbox="roadtrip">
  <img src="/assets/img/clippies/ranks_coding_ranking.png" alt="Coding Ranking" style="width: 45%;">
</a>
<a href="/assets/img/clippies/ranks_coding.png" data-lightbox="roadtrip">
  <img src="/assets/img/clippies/ranks_coding.png" alt="Coding Scores" style="width: 45%;">
</a>

**Figure 2:** Same conventions as Figure 1.


## Methods

### Benchmark selection and data collection

I manually collected model rankings from established LLM leaderboards on February 11, 2026, choosing benchmarks that cover different evaluation angles.

*General reasoning* draws on four leaderboards:

- [LiveBench](https://livebench.ai) — regularly refreshed, multi-domain evaluation designed to resist contamination
- [Arena](https://arena.ai/leaderboard) — ELO-style ranking from blind human preference votes (a popular-preference signal rather than a strict accuracy benchmark, but informative nonetheless)
- [Artificial Analysis Intelligence Index](https://artificialanalysis.ai) — a composite of 10 evaluations including GPQA Diamond, Humanity's Last Exam, SciCode, and others
- [Scale's Humanity's Last Exam](https://scale.com/leaderboard/humanitys_last_exam) — expert-level reasoning questions

*Coding and agentic coding* draws on seven leaderboards:

- The three leaderboards previously mentioned (using coding-specific subcategories where applicable) plus four focused evaluations below.
- [Scale's SWE Bench Pro Public](https://scale.com/leaderboard/swe_bench_pro_public)
- [Berkeley Function-Calling Leaderboard (BFCL)](https://gorilla.cs.berkeley.edu/leaderboard.html) — tool and function call accuracy
- [SWE-bench Verified](https://www.swebench.com) — real-world GitHub issue resolution
- [Terminal-Bench 2.0](https://www.tbench.ai/leaderboard/terminal-bench/2.0) — agentic terminal and shell-based coding tasks

I selected 20+ models spanning the current frontier: proprietary leaders from OpenAI (GPT-5.2+ family), Anthropic (Claude 4.5+ family), Google (Gemini 3), and xAI (Grok 4+), plus open-weights challengers from DeepSeek, Moonshot AI (Kimi), Z AI (GLM), MiniMax, Alibaba (Qwen3+), and Meta/NVIDIA (Llama 4).

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

For consistent cost comparison, I use the credit cost per 1,000 tokens from a single API provider ([Poe](https://poe.com)) as a uniform pricing reference. Absolute dollar costs vary by provider and plan, but this gives a stable *relative* comparison across all models on the same platform.


## Conclusions

- If you need the absolute best coding reliability and can afford it, Claude Opus 4.6 earns its price. It ranks consistently at tier 1.
- For general reasoning, you have several affordable options: Kimi K2.5, GLM-5 deliver Tier 2 performance at a fraction of the cost. Also competitive: Gemini Flash 3 and Qwen 3 Max.
- For coding and agentic coding (e.g. [opencode](https://opencode.ai)), there are many options with great value: Gemini Flash 3, Kimi K2.5, GLM-5, MiniMax M2.5 and Qwen 3.5.
- If budget is the primary concern, DeepSeek V3.2 and Grok 4.1 Fast offer the standout value of this generation.

---

## Reproducibility

All code, data files, and full methodology details are [here](https://github.com/rsnemmen/rank-clippies). 
