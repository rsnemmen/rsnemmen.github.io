---
layout: page
title: LLM ranking
permalink: /llm-ranking/
description: Methodology and links to the live LLM rankings
nav: false
nav_order: 4
---

I benchmark LLMs across coding and general reasoning tasks and compare performance against API pricing. The latest rankings and interactive charts now live on the dedicated GitHub Pages site: [rsnemmen.github.io/rank-clippies](https://rsnemmen.github.io/rank-clippies/).

**Live rankings:** [Open the latest leaderboard and plots](https://rsnemmen.github.io/rank-clippies/).

This page remains a short methodology summary and a stable entry point from the main website.

## Introduction

I conducted this statistical analysis of LLM rankings with three goals:

1. Derive the average ranking of models from multiple LLM leaderboards.
2. Group models into tiers with similar performance levels.
3. Compare model performance against relative cost to identify strong value picks.

The live site contains the latest rankings and visualizations; the sections below describe how the ranking procedure works.

## Methods

### Benchmark selection and data collection

I manually collect model rankings from established LLM leaderboards, choosing benchmarks that cover different evaluation angles.

_General reasoning_ draws on eight leaderboards:

- [LiveBench](https://livebench.ai) — regularly refreshed, multi-domain evaluation designed to resist contamination
- [Arena](https://arena.ai/leaderboard) — ELO-style ranking from blind human preference votes (a popular-preference signal rather than a strict accuracy benchmark, but informative nonetheless)
- [Scale's Humanity's Last Exam](https://scale.com/leaderboard/humanitys_last_exam) — expert-level reasoning questions
- [SimpleBench](https://simple-bench.com) — commonsense and reasoning-trap questions designed to expose systematic errors
- [GPQA Diamond](https://scale.com/leaderboard/gpqa) — graduate-level science questions spanning biology, chemistry, and physics
- [MMMLU](https://huggingface.co/datasets/openai/MMMLU) — massive multilingual multitask language understanding
- [USAMO](https://scale.com/leaderboard) — USA Mathematical Olympiad problems
- [CharXiv](https://charxiv.github.io) — chart understanding and scientific figure comprehension

_Coding and agentic coding_ draws on seven leaderboards:

- LiveBench (coding subcategory), Arena (coding subcategory), and Artificial Analysis (agentic and coding sub-scores) plus four focused evaluations below
- [Scale's SWE Bench Pro Public](https://scale.com/leaderboard/swe_bench_pro_public)
- [Terminal-Bench 2.0](https://www.tbench.ai/leaderboard/terminal-bench/2.0) — agentic terminal and shell-based coding tasks
- [SWE-Atlas Codebase QnA](https://sweatlas.com) — question-answering over large, real-world codebases

I track 30+ frontier models, including proprietary systems from OpenAI, Anthropic, Google, xAI, and Meta, plus open-weights challengers from DeepSeek, Moonshot AI, Z AI, MiniMax, Alibaba, Meta/Google, and NVIDIA.

### Percentile normalization

Different leaderboards evaluate different numbers of models. Being ranked 5th out of 600 models is far more impressive than 5th out of 30. To make cross-benchmark comparisons fair, I normalize each rank to a fractional percentile:

$$\text{percentile} = \frac{\text{rank}}{\text{total models evaluated}}$$

This puts every score on a 0-1 scale (0 = best, 1 = worst). A model that's 3rd out of 600 on Arena (percentile 0.005) and 2nd out of 50 on LiveBench (percentile 0.04) can now be compared on the same axis.

### Aggregation and penalties

A model's composite score is the unweighted **median** of its percentiles across all benchmarks it appears on. To avoid boosting the ranking of a model that happens to score well on the single benchmark it was evaluated on, a sparse-data penalty is added: +0.25 for one benchmark, +0.10 for two, and zero for three or more.

The median is preferred over the arithmetic mean because benchmark scores are heterogeneous—different leaderboards have different scale, coverage, and noise characteristics. A single outlier benchmark can pull a mean-based score well away from a model's typical performance. The median is resistant to such outliers, giving a more representative summary of where the model actually sits across evaluations.

### Statistical tiering

Rather than treating every rank difference as meaningful, I group models into _tiers_ using the "indistinguishable from best" method:

1. The best model becomes the tier leader.
2. Every remaining model whose plus/minus semi-IQR interval overlaps with the leader's joins the same tier.
3. Remove the tier, promote the next-best model to leader, and repeat.

Formally, _model i_ is grouped with _leader j_ if:

$$\text{score}_i + \frac{\text{IQR}_i}{2} \geq \text{score}_j - \frac{\text{IQR}_j}{2}$$

In plain terms: if B's best-case performance could plausibly reach A's worst-case, we can't confidently distinguish them. This acknowledges that benchmark scores carry noise and avoids drawing artificial distinctions where the evidence doesn't support them.

The **semi-IQR** (half the interquartile range) is the natural robust companion to the median as the dispersion measure. Unlike standard deviation, it is not sensitive to the same outlier benchmarks the median was chosen to resist—using mean + SD or median + SD would be internally inconsistent. Semi-IQR requires at least three data points to be defined; models with fewer than three benchmarks receive the average semi-IQR across all other models as a stand-in.

### Cost metric

For consistent cost comparison, I normalize each model's Poe credit cost per 1,000 tokens to the cost of the best-ranked model in each category (Rel. Cost = 1 for the top model; values below 1 are cheaper, above 1 are more expensive). This removes absolute pricing noise while preserving the cost ratios that matter for budget decisions. Absolute credit prices vary by provider and plan, but the relative ordering remains stable across models on the same platform.

## Reproducibility

The full code, data files, and methodology details live in the [rank-clippies GitHub repository](https://github.com/rsnemmen/rank-clippies), and the latest published rankings are available at [rsnemmen.github.io/rank-clippies](https://rsnemmen.github.io/rank-clippies/).
