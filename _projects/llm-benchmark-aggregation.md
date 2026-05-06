---
layout: page
title: Robust LLM Benchmark Aggregation
description: Median-percentile aggregation and statistical tiering for frontier LLM benchmark rankings
img: assets/img/llm-benchmark-aggregation/coding-and-agentic-coding.png
importance: 1
category: ai
github: https://github.com/rsnemmen/rank-clippies
---

<div class="alert alert-info"><h4>Executive Summary</h4><p>
Robust LLM Benchmark Aggregation is a statistical ranking system for comparing frontier language models across heterogeneous public leaderboards. The project normalizes model ranks into percentiles, aggregates them with robust statistics, groups statistically similar models into tiers, and compares performance against relative cost. The live rankings and interactive charts are published at <a href="https://rsnemmen.github.io/rank-clippies/">rank-clippies</a>, with methodology summarized on this site.
</p></div>

The LLM ecosystem changes quickly, and individual leaderboards only capture part of model behavior. Coding benchmarks, human preference arenas, terminal-agent tasks, and codebase question-answering tests all measure different capabilities. This project combines those signals into a practical decision framework for model selection.

<div class="row">
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/llm-benchmark-aggregation/coding-and-agentic-coding.png" title="Coding and agentic coding model comparison" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
Coding and agentic coding models compared by aggregate benchmark performance and relative cost.
</div>

## Technical Approach

The ranking pipeline starts by collecting model placements from established leaderboards. For coding and agentic coding, the source set includes coding-specific leaderboard slices, software-engineering benchmarks, terminal-agent evaluations, and codebase question-answering tasks.

Because each leaderboard evaluates a different number of models, raw ranks are converted to fractional percentiles:

$$\text{percentile} = \frac{\text{rank}}{\text{total models evaluated}}$$

This makes a rank from a small expert benchmark comparable to a rank from a large public arena. Each model's composite score is then computed as the median of its benchmark percentiles. The median is deliberately used instead of the mean because it is less sensitive to outlier benchmarks and better matches the noisy, heterogeneous nature of public evaluations.

## Statistical Tiering

The project avoids over-interpreting tiny rank differences by grouping models into statistically plausible tiers. It uses a semi-IQR uncertainty interval around each model's median score, then applies an "indistinguishable from best" grouping rule within each tier.

This produces a more useful output than a strict numbered list: models in the same tier should be treated as broadly comparable unless additional domain-specific evidence separates them.

<div class="row">
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid loading="lazy" path="assets/img/llm-benchmark-aggregation/coding-and-agentic-coding-ranking.png" title="Coding and agentic coding ranking tiers" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
Coding and agentic coding ranking tiers derived from median-percentile aggregation and semi-IQR uncertainty.
</div>

## Why It Matters

The result is a model-selection workflow that balances capability, robustness, and cost. It helps answer practical questions such as which models are strongest for coding workflows, which models are statistically tied, and which models offer the best value relative to the top-ranked system.

## Resources

- [Live rankings and charts](https://rsnemmen.github.io/rank-clippies/)
- [Methodology page](/llm-ranking/)
- [GitHub repository](https://github.com/rsnemmen/rank-clippies)
