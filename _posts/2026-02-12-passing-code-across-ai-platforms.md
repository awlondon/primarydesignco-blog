---
layout: post
title: "Passing Code Across AI Platforms"
subtitle: "Generative AI Product Relay"
author: Alexander Warren London
contributors:
  - Alexander Warren London
published_at: 2026-02-12T11:00:00-08:00
tags: [ai, llm, generative-code, product-design, systems]
reading_time: 18
abstract: |
  A structured comparison of leading LLM platforms using a controlled generative coding experiment. This essay evaluates baseline outputs, relay performance, and production viability, arguing that intentional cross-model orchestration outperforms single-model loyalty.
---

<!-- Top Relay Artifact -->
<div style="position:relative; width:100%; padding-top:56.25%;">
  <iframe
    src="/assets/2026-02-12-passing-code-across-ai-platforms/relay-city/index.html"
    style="position:absolute; top:0; left:0; width:100%; height:100%; border:0;"
    loading="lazy"
  ></iframe>
</div>

> The above artifact is the result of iterative relay between PDCo Dev Studio and Gemini (Canvas). All other embedded examples in this article represent first-pass outputs only.

---

## I. The Myth of the “Best Model”

In early 2026, AI evaluation discourse remains dominated by leaderboards. Models are compared by benchmark deltas, reasoning tests, token limits, and synthetic coding suites. The implicit assumption is that performance is scalar: one model is simply better.

But generative product work does not resemble a benchmark.

Benchmarks reward deterministic correctness under controlled constraints. Product generation rewards coherence under ambiguity. Benchmarks evaluate answer quality. Product generation exposes architectural philosophy.

These are not the same task.

Human–AI co-creation research has already demonstrated that output quality in creative and engineering domains depends heavily on interaction structure rather than raw model capability.^[1] Iterative framing, constraint reinforcement, and staged refinement consistently outperform single-shot prompting.^[2] Yet most public comparisons still treat LLMs as independent competitors rather than composable components.

This article rejects that framing.

Instead of asking which model is “best,” we ask:

Which models are worth using, and in what sequence?

{% include ad.html %}

---

## II. Experiment Design

To ground the analysis, we ran a controlled generative test across platforms.

**Prompt (identical across models):**

> “Generate a pixel-based animation of a futuristic cityscape.”

Constraints:
- Must output complete HTML/CSS/JS.
- Must run in a single iframe.
- No post-editing.
- No cross-model modification.
- No manual structural correction.

Each model was evaluated on its first-pass output.

The relay artifact shown at the top of this article is intentionally excluded from baseline scoring. It represents iterative passing between PDCo Dev Studio and Gemini. Its purpose is diagnostic: to show what emerges when models are sequenced rather than isolated.

This distinction matters.

Studies of LLM interaction stability show that iterative refinement often introduces drift, architectural mutation, and feature regression when state continuity is not preserved.^[3] Evaluating baseline output separately from relay behavior allows us to measure both generative competence and structural resilience.

### Evaluation Axes

Each model is evaluated across the following dimensions:

1. Baseline Visual Quality  
2. Code Architecture Coherence  
3. Determinism / Stability  
4. Feature Preservation Under Iteration  
5. Context Continuity  
6. Debuggability  
7. Packaging / Deployment Friction  
8. Relay Utility  
9. Overall Workflow Value  

Scores are reported to two decimal places. A rating above 9.00 indicates production-caliber reliability. Scores between 7.50 and 8.99 indicate strong but constrained utility. Anything below 6.00 suggests fragility under real-world conditions.

The objective is not aesthetic preference. It is production viability.

{% include ad.html %}

---

## III. Baseline Outputs — First-Pass Only

The following sections present each model’s first response to the identical prompt. No edits. No relay. No improvement passes.

This isolates default generative character.

---

### 1. PDCo Dev Studio (GPT-4-mini API)

Baseline output characteristics:

- Single-file architecture.
- Clean procedural generation logic.
- Moderate starfield + skyline composition.
- Minimal UI scaffolding.
- Simple neon gradient aesthetic.

Strengths:

- Structural clarity.
- Low deployment friction.
- Easy to modify.
- Deterministic enough for iteration.

Weaknesses:

- Limited visual layering.
- No parallax.
- No seeded determinism.
- Window flicker logic introduces stochastic inconsistency.

The model clearly optimizes for interpretability and constraint alignment. It produces stable, comprehensible systems but does not aggressively push visual complexity.

Baseline Assessment:
Competent, clean, conservative.

---

### 2. Gemini (Canvas)

Baseline output characteristics:

- Higher visual density.
- Multi-layer parallax.
- Palette cycling.
- User interaction (click-to-change theme).
- Atmospheric fog and traffic simulation.

Strengths:

- Strong visual imagination.
- Layered scene construction.
- More ambitious animation logic.
- Cohesive aesthetic system.

Weaknesses:

- Tendency toward structural mutation under iteration.
- Occasional redefinition of internal heuristics.
- Increased debugging surface area.

Gemini optimizes for visual expressiveness and layered complexity. It behaves more like a graphics designer than a systems engineer.

Baseline Assessment:
High aesthetic output; moderate structural volatility.

---

### 3. ChatGPT 5.2 Thinking (Canvas)

Baseline output characteristics:

- Logical low-resolution buffer scaling.
- Deterministic seeded generation.
- UI sliders controlling rain, traffic, hue, neon.
- Modular rendering pipeline.

Strengths:

- Explicit architectural segmentation.
- Adjustable parameters.
- Reproducible scene state.
- Advanced layering logic.

Weaknesses:

- Increased complexity footprint.
- Higher cognitive load for modification.
- More code than minimal use-cases require.

This output suggests optimization for extensibility rather than minimalism. It reads as a production-ready scaffold rather than a quick generative artifact.

Baseline Assessment:
Architecturally mature; slightly heavy for simple tasks.

---

### 4. Claude Code (Sonnet 4.5)

Baseline output characteristics:

- Pixel-drawing via nested loops.
- Billboard animation.
- Simple flying vehicle logic.
- Structured but traditional approach.

Strengths:

- Clear rendering primitives.
- Predictable flow.
- Easy conceptual understanding.

Weaknesses:

- Repeated randomization inside draw loops.
- Flicker logic tied to frame randomness.
- Limited abstraction.

Claude demonstrates consistent compositional logic but exhibits lower emphasis on architectural refinement compared to higher-tier models.

Baseline Assessment:
Solid mid-tier generative coder.

---

### 5. Grok 4.1 (Code Mode)

Baseline output characteristics:

- Explicit low-resolution scaling.
- Structured vehicle and window systems.
- Deterministic flicker probability.
- Clean loop architecture.

Strengths:

- Clear separation of update vs render.
- Simple deployment.
- Strong pixel-art discipline.

Weaknesses:

- Limited atmospheric layering.
- Lower creative risk.
- Less dynamic aesthetic variation.

Grok behaves conservatively but predictably.

Baseline Assessment:
Reliable baseline generator; moderate creative ceiling.

---

### 6. LlamaCode GLM 4.6

Baseline behavior:

- Multi-file structure by default.
- Complex project scaffolding.
- Partial runtime inconsistencies.
- Slower generation cycle.

Strengths:

- Ambition toward full project architecture.
- Clear separation of concerns.

Weaknesses:

- Not iframe-friendly by default.
- Execution friction.
- Inconsistent runtime results.

Baseline Assessment:
Architecturally over-scoped for the task; not deployment-ready in single-pass form.

---

### 7. Base 44

Observed behavior:

- Limited code transparency.
- Subpar visual output.
- Restricted structural visibility.

Strengths:
- Rapid generation.

Weaknesses:
- Low output quality.
- Poor inspectability.
- Low modification affordance.

Baseline Assessment:
Not production-viable for this class of task.

---

{% include ad.html %}
