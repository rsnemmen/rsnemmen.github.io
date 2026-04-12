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

Updated on Apr. 12 2026.

## Introduction

I conducted a statistical analysis of LLM rankings. My specific goals were:

1. Derive the average ranking of models from multiple LLM leaderboards.
2. Group models into tiers with similar performance levels.
3. Plot model performance against relative cost to identify which models offer performance comparable to top-tier options at a lower price.

By analyzing the results, we can identify the highest-performing models as well as those offering the optimal cost-benefit ratio.

## Results

### General reasoning

The general reasoning ranking, aggregated across eight leaderboards, is dominated at the top by proprietary models—with open-weights challengers competitive from tier 2 onward.

```
+-------------------------------------------------------------------------------------+
| Rank  | Model                   | Avg Pctl  | IQR/2     | # Benchmarks  | Rel. Cost |
+-------------------------------------------------------------------------------------+
| 1     | mythos                  | 0.000     | 0.000     | 5             | 1.000     |
| 2     | gemini-pro31            | 0.006     | 0.032     | 8             | 0.110     |
| 3     | gpt54                   | 0.021     | 0.015     | 6             | 0.124     |
| 4     | gpt-pro54               | 0.080     | 0.065     | 3             | 1.482     |
| 5     | opus46                  | 0.083     | 0.096     | 9             | 0.200     |
| 6     | sonnet46                | 0.096     | 0.050     | 7             | 0.120     |
| 7     | muse                    | 0.096     | 0.024     | 5             | 0.200     |
| 8     | qwen36-plus             | 0.135     | 0.033     | 3             | 0.028     |
| 9     | grok42                  | 0.173     | 0.092     | 5             | 1.482     |
| 10    | gemini-flash3           | 0.188     | 0.056     | 8             | 0.024     |
| 11    | gpt-codex53             | 0.208     | N/A       | 2             | 0.111     |
| 12    | glm51                   | 0.212     | 0.178     | 7             | 0.046     |
| 13    | gpt-mini54              | 0.221     | 0.094     | 4             | 0.037     |
| 14    | qwen35                  | 0.231     | 0.210     | 5             | 0.020     |
| 15    | kimi25                  | 0.236     | 0.113     | 7             | 0.028     |
| 16    | gemma4-31               | 0.236     | 0.141     | 6             | 0.004     |
| 17    | qwen3-max               | 0.275     | 0.083     | 4             | 0.129     |
| 18    | minimax27               | 0.303     | 0.087     | 4             | 0.012     |
| 19    | gemini-flash-lite31     | 0.325     | 0.129     | 5             | 0.014     |
| 20    | deepseek32              | 0.326     | 0.084     | 7             | 0.005     |
| 21    | haiku45                 | 0.385     | 0.103     | 7             | 0.040     |
| 22    | grok-fast41             | 0.386     | 0.148     | 6             | 0.006     |
| 23    | gpt-oss-120b            | 0.590     | 0.211     | 6             | 0.009     |
| 24    | qwen35-35b              | 0.635     | N/A       | 1             | 0.012     |
| 25    | gpt-oss-20b             | 0.842     | N/A       | 2             | 0.004     |
+-------------------------------------------------------------------------------------+
```

<a href="/assets/img/clippies/general_ranking.png" data-lightbox="roadtrip">
  <img src="/assets/img/clippies/general_ranking.png" alt="General Ranking" style="width: 45%;">
</a>
<a href="/assets/img/clippies/general.png" data-lightbox="roadtrip">
  <img src="/assets/img/clippies/general.png" alt="General Scores" style="width: 45%;">
</a>

**Figure 1. Left panel:** Overall ranking. Circle size proportional to log10(API cost). **Right panel:** Credit cost (log scale) on the x-axis and median percentile score on the y-axis (inverted, so the best models appear at the top). The upper-left corner is the sweet spot: best performance at lowest cost. In both panels, error bars show ±semi-IQR; dots show individual benchmark percentiles. Colors indicate statistical tier. Circles mark proprietary models; squares mark open-weights models.


### Coding and agentic coding

The coding ranking, drawn from seven benchmarks including demanding agentic evaluations, reveals a two-model tier-1 club at the top—and a wide, cost-diverse tier 2 below it.

```
+-------------------------------------------------------------------------------------+
| Rank  | Model                   | Avg Pctl  | IQR/2     | # Benchmarks  | Rel. Cost |
+-------------------------------------------------------------------------------------+
| 1     | gpt54                   | 0.000     | 0.024     | 7             | 1.000     |
| 2     | mythos                  | 0.000     | 0.000     | 3             | 8.095     |
| 3     | gpt-codex53             | 0.129     | 0.086     | 6             | 0.901     |
| 4     | qwen36-plus             | 0.148     | 0.035     | 3             | 0.223     |
| 5     | gemini-pro31            | 0.164     | 0.134     | 8             | 0.890     |
| 6     | opus46                  | 0.186     | 0.088     | 8             | 1.619     |
| 7     | sonnet46                | 0.189     | 0.112     | 8             | 0.971     |
| 8     | glm51                   | 0.206     | 0.087     | 6             | 0.370     |
| 9     | muse                    | 0.268     | N/A       | 1             | 1.619     |
| 10    | grok42                  | 0.268     | 0.066     | 3             | 16.190    |
| 11    | minimax27               | 0.275     | 0.048     | 6             | 0.095     |
| 12    | qwen35                  | 0.286     | 0.085     | 5             | 0.164     |
| 13    | gpt-mini54              | 0.286     | 0.041     | 6             | 0.301     |
| 14    | gemini-flash3           | 0.297     | 0.133     | 7             | 0.190     |
| 15    | kimi25                  | 0.304     | 0.118     | 7             | 0.229     |
| 16    | deepseek32              | 0.308     | 0.156     | 6             | 0.044     |
| 17    | gemma4-31               | 0.379     | 0.093     | 4             | 0.036     |
| 18    | grok-fast41             | 0.388     | 0.093     | 4             | 0.046     |
| 19    | haiku45                 | 0.453     | 0.080     | 7             | 0.324     |
| 20    | qwen3-max               | 0.476     | 0.119     | 4             | 1.048     |
| 21    | gemini-flash-lite31     | 0.482     | 0.006     | 5             | 0.112     |
| 22    | gpt-oss-120b            | 0.500     | 0.122     | 5             | 0.076     |
| 23    | nemotron-super3         | 0.555     | 0.122     | 4             | 0.076     |
| 24    | gpt-oss-20b             | 0.660     | 0.079     | 4             | 0.029     |
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

I manually collected model rankings from established LLM leaderboards on April 12, 2026, choosing benchmarks that cover different evaluation angles.

*General reasoning* draws on eight leaderboards:

- [LiveBench](https://livebench.ai) — regularly refreshed, multi-domain evaluation designed to resist contamination
- [Arena](https://arena.ai/leaderboard) — ELO-style ranking from blind human preference votes (a popular-preference signal rather than a strict accuracy benchmark, but informative nonetheless)
- [Scale's Humanity's Last Exam](https://scale.com/leaderboard/humanitys_last_exam) — expert-level reasoning questions
- [SimpleBench](https://simple-bench.com) — commonsense and reasoning-trap questions designed to expose systematic errors
- [GPQA Diamond](https://scale.com/leaderboard/gpqa) — graduate-level science questions spanning biology, chemistry, and physics
- [MMMLU](https://huggingface.co/datasets/openai/MMMLU) — massive multilingual multitask language understanding
- [USAMO](https://scale.com/leaderboard) — USA Mathematical Olympiad problems
- [CharXiv](https://charxiv.github.io) — chart understanding and scientific figure comprehension

*Coding and agentic coding* draws on seven leaderboards:

- LiveBench (coding subcategory), Arena (coding subcategory), and Artificial Analysis (agentic and coding sub-scores) plus four focused evaluations below.
- [Scale's SWE Bench Pro Public](https://scale.com/leaderboard/swe_bench_pro_public)
- [Terminal-Bench 2.0](https://www.tbench.ai/leaderboard/terminal-bench/2.0) — agentic terminal and shell-based coding tasks
- [SWE-Atlas Codebase QnA](https://sweatlas.com) — question-answering over large, real-world codebases

I selected 30+ models spanning the current frontier: proprietary leaders from OpenAI (GPT-5.4 family: gpt54, gpt-pro54, gpt-mini54, gpt-codex53), Anthropic (Claude 4.5+ family including the unreleased Mythos), Google (Gemini 3.1 family and Gemma 4), xAI (Grok 4.2 and Grok Fast 4.1), and Meta (unreleased Muse), plus open-weights challengers from DeepSeek (V3.2), Moonshot AI (Kimi K2.5), Z AI (GLM 5.1), MiniMax (M2.5/M2.7), Alibaba (Qwen 3/3.5 variants), Meta/Google (Llama 4 Maverick, Gemma 4), and NVIDIA (Nemotron Nano/Super 3).

### Percentile normalization

Different leaderboards evaluate different numbers of models. Being ranked 5th out of 600 models is far more impressive than 5th out of 30. To make cross-benchmark comparisons fair, I normalize each rank to a fractional percentile:

$$\text{percentile} = \frac{\text{rank}}{\text{total models evaluated}}$$

This puts every score on a 0–1 scale (0 = best, 1 = worst). A model that's 3rd out of 600 on Arena (percentile 0.005) and 2nd out of 50 on LiveBench (percentile 0.04) now live on the same axis.

### Aggregation and penalties

A model's composite score is the unweighted **median** of its percentiles across all benchmarks it appears on. To avoid boosting the ranking of a model that happens to score well on the single benchmark it was evaluated on, a sparse-data penalty is added: +0.25 for one benchmark, +0.10 for two, and zero for three or more.

The median is preferred over the arithmetic mean because benchmark scores are heterogeneous—different leaderboards have different scale, coverage, and noise characteristics. A single outlier benchmark can pull a mean-based score well away from a model's typical performance. The median is resistant to such outliers, giving a more representative summary of where the model actually sits across evaluations.

### Statistical tiering

Rather than treating every rank difference as meaningful, I group models into *tiers* using the "indistinguishable from best" method:

1. The best model becomes the tier leader.
2. Every remaining model whose ±semi-IQR interval overlaps with the leader's joins the same tier.
3. Remove the tier, promote the next-best model to leader, and repeat.

Formally, *model i* is grouped with *leader j* if:

$$\text{score}_i + \frac{\text{IQR}_i}{2} \geq \text{score}_j - \frac{\text{IQR}_j}{2}$$

In plain terms: if B's best-case performance could plausibly reach A's worst-case, we can't confidently distinguish them. This acknowledges that benchmark scores carry noise and avoids drawing artificial distinctions where the evidence doesn't support them.

The **semi-IQR** (half the interquartile range) is the natural robust companion to the median as the dispersion measure. Unlike standard deviation, it is not sensitive to the same outlier benchmarks the median was chosen to resist—using mean + SD or median + SD would be internally inconsistent. Semi-IQR requires at least three data points to be defined; models with fewer than three benchmarks receive the average semi-IQR across all other models as a stand-in.

### Cost metric

For consistent cost comparison, I normalize each model's Poe credit cost per 1,000 tokens to the cost of the best-ranked model in each category (Rel. Cost = 1 for the top model; values below 1 are cheaper, above 1 are more expensive). This removes absolute pricing noise while preserving the cost ratios that matter for budget decisions. Absolute credit prices vary by provider and plan, but the relative ordering remains stable across models on the same platform.


## Conclusions

- For coding, the tier-1 club is now just two models: *GPT-5.4* and Anthropic's unreleased *Mythos*, both tied at 0.000 median percentile. If you need peak coding performance and cost is secondary, those are the models.
- There is a large tier-2 coding population—*GPT-Codex 5.3*, *Qwen 3.6 Plus*, *Gemini 3.1 Pro*, *Claude Opus 4.6*, *Claude Sonnet 4.6*, and *GLM 5.1*—statistically indistinguishable from each other and close to the top.
- For general reasoning, the top three are extremely close: *Mythos*, *Gemini 3.1 Pro* (0.006), and *GPT-5.4* (0.021)—effectively a three-way tie within the margin of variability.
- Best open-weights pick for general reasoning: *GLM 5.1* (rank 12), *Qwen 3.5* (rank 14), *Kimi K2.5* (rank 15), and *Gemma 4 3.1* (rank 16) are all competitive in the upper half of the table.
- Best value for general reasoning: *Gemma 4 3.1* (Rel. Cost 0.004), *DeepSeek V3.2* (0.005), *MiniMax M2.7* (0.012), and *Gemini Flash Lite 3.1* (0.014) deliver strong performance at a fraction of the frontier price.
- Best value for coding and agentic tasks (e.g. [opencode](https://opencode.ai)): *DeepSeek V3.2*, *Gemma 4 3.1*, *Grok Fast 4.1*, *MiniMax M2.7*, and *Qwen 3.5* all offer solid performance at the low end of the cost range.
- For the tightest budgets, *DeepSeek V3.2* (0.005 relative cost for coding), *Gemma 4 3.1*, and *Grok Fast 4.1* remain the standout value picks across both categories.

---

## Reproducibility

All code, data files, and full methodology details are [here](https://github.com/rsnemmen/rank-clippies). 
