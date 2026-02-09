---
layout: post
title: "Real-Time HTML/JS/CSS as a First-Class LLM Interface"
subtitle: "Turning text-only chat into a live, multimodal surface"
author: Alexander Warren London
contributors:
  - Alexander Warren London
published_at: 2026-02-06T08:00:00-08:00
tags: [ai, interfaces, llms, multimodal, tooling, design-practice]
reading_time: 18
abstract: |
  Contemporary large language models are already capable of producing interactive
  user interfaces, executable logic, and stylistic systems. Yet most chat platforms
  flatten these capabilities into static text. This essay argues that multimodal
  interaction does not require new models or native platform features. By structuring
  prompts to return executable HTML, CSS, and JavaScript alongside prose—and rendering
  that code in real time—users can convert existing text-based chatbots into live,
  inspectable, and extensible interaction surfaces.
---

<div style="width:100%; aspect-ratio: 16 / 27; margin-bottom:2rem;">
  <iframe
    src="https://dev.primarydesignco.com"
    style="width:100%; height:100%; border:0;"
    loading="lazy"
  ></iframe>
</div>

**Preview: Maya Dev Interface**

[Open dev.primarydesignco.com](https://dev.primarydesignco.com){:target="_blank" rel="noopener noreferrer"}

## The Interface Bottleneck

Large language models already generate far more than sentences. They routinely emit executable logic, interface layouts, stateful behavior, and visual structure. Yet most conversational platforms collapse these outputs into a single modality: static text.

This flattening is not an intelligence constraint. It is an interface choice.

Across major platforms—ChatGPT, Gemini, Claude, and Grok—the same pattern appears. Models generate structured artifacts, but the surrounding UI treats them as prose. Even when code blocks or previews exist, they are typically non-interactive, stateless, or visually secondary to the text stream.

The result is a persistent mismatch between capability and experience. Users ask for systems, tools, or interfaces; the model responds with the raw materials; the platform discards their operational form. What remains is an explanation of a thing that could have existed, not the thing itself.

This matters because interaction quality is not determined by output accuracy alone. It is shaped by feedback, manipulability, and inspection. A response that can be *touched*—clicked, adjusted, rerun—conveys understanding in a way a paragraph never can.

{% include ad.html %}

## The Prompt-Wrapper Pattern

The fastest way to close this gap does not require new models, plugins, or native platform features. It requires discipline at the prompt boundary.

The core move is simple: ask the model to separate explanation from execution, and to return both in a predictable structure. One effective pattern is to instruct the model to emit two parallel artifacts—human-readable text and fully executable interface code—returned in a machine-parseable form.

A minimal version looks like this:

> Generate a clear text response to the prompt, and also generate stylistic HTML, CSS, and JavaScript that implements or visualizes the response.  
> Return the result as an array in this order:  
> \["text response", "full HTML/JS/CSS code"\].

This wrapper does several important things at once. It prevents code from being interleaved with prose. It makes the response reliably extractable. And it establishes an expectation that the code is not illustrative, but operational.

Nothing about this pattern is novel at the model level. Large language models already comply with structured output requests, generate valid front-end code, and reason about UI state. What changes is the *intent signal*: code is no longer an appendix to the answer. It is the answer’s executable surface.

Crucially, this technique works today across existing LLMs. It does not depend on hidden APIs or experimental features. It is a user-side convention that treats the model as a co-author of live interfaces rather than a narrator describing them.

## What You’re Seeing Above

The embedded interface at the top of this article is a reference implementation of this pattern.

The iframe demonstrates a simple loop: a prompt is sent to an LLM, the response is parsed into text and code, and the generated HTML/JS/CSS is rendered immediately as a live surface. The text remains visible as explanation and context, but interaction happens inside the rendered artifact.

This is not a product pitch. It is a proof that the bottleneck is not generative capacity. It is rendering.

Once code is treated as first-class output—executed rather than quoted—the conversation itself becomes an interface. Text becomes a control plane: a way to steer, refine, and interrogate behavior that is already present on the screen.

{% include ad.html %}

## What Existing Platforms Already Hint At

Major LLM platforms already acknowledge—implicitly—that text alone is an impoverished interface. Over the last year, each has introduced partial mechanisms for displaying generated artifacts, especially code. What differs is not model capability, but how far each platform allows those artifacts to behave like *interfaces* rather than excerpts.

In ChatGPT, generated HTML, CSS, and JavaScript are typically presented inside fenced code blocks, occasionally accompanied by limited previews. While this supports inspection, it suppresses interaction. State resets on every turn, execution is visually de-emphasized, and the conversational loop remains anchored to text. The model may generate a working interface, but the platform treats it as documentation rather than a surface.^[1]

Gemini goes further by sometimes rendering generated UI elements inline, particularly for simple visualizations or widgets. This signals an important shift: the recognition that model output can be *shown*, not just read. However, these previews are tightly scoped, often ephemeral, and rarely designed for iterative manipulation across turns.^[2]

Claude introduces a more explicit separation between explanation and artifact through its “Artifacts” panel. This is one of the clearest acknowledgments that generated code and documents deserve their own spatial context. Yet even here, execution is limited. Artifacts are inspectable, not alive. They do not naturally accumulate state, nor do they participate directly in the conversational feedback loop.^[3]

Grok experiments with rendering and real-time elements in a more fluid way, but primarily as demonstrations rather than durable interaction surfaces. The emphasis remains on speed and novelty, not on sustained, inspectable systems that evolve over a session.^[4]

Across all of these platforms, the same pattern holds. The model can already generate interactive systems. The interface acknowledges this only partially, and then reins it back in. What users receive is a *representation* of an interface, not the interface.

{% include ad.html %}

## The Missing Layer: Real-Time Rendering

The difference between reading an interface and using one is not cosmetic. It is structural.

When generated code is executed immediately—when HTML is rendered, JavaScript runs, and CSS governs layout—the interaction acquires properties that text cannot provide: state persistence, feedback, and affordances. Buttons can be clicked. Sliders can be adjusted. Outputs can change without re-prompting the model. The system becomes something you *operate*, not something you interpret.

This exposes a crucial insight: LLM conversations already contain the logic of tools. What they lack is a rendering loop that treats those tools as present rather than hypothetical. Real-time execution does not add intelligence; it removes friction.

Once this layer is in place, the role of text changes. Language becomes a steering mechanism—a way to specify constraints, modify behavior, or request extensions—while the primary interaction happens through the rendered artifact itself. The conversation stops being a transcript and starts behaving like a workbench.

This is why the prompt-wrapper pattern matters. By forcing a clean separation between explanation and execution, it enables immediate rendering without ambiguity. The model is not asked to *describe* a UI. It is asked to deliver one, alongside its rationale.

## A Reference Implementation: maya-dev-ui

The embedded interface at the top of this article demonstrates this missing layer in its simplest viable form.

A prompt is sent to an LLM with a structured wrapper. The response is parsed deterministically. The textual explanation is displayed as context, while the generated HTML, CSS, and JavaScript are executed inside a sandboxed frame. The result is a live surface that can be interacted with immediately.

What matters here is not sophistication. The implementation is intentionally modest. Its purpose is to show that nothing fundamental is missing from today’s stack. No new model capabilities are required. No proprietary extensions are involved. The gap being closed is purely one of interface execution.

Once that gap is closed, a different style of interaction becomes possible—one where users and models co-construct tools in real time, and conversation becomes the means of steering a system already in motion.

{% include ad.html %}

## Why This Works Now (Not Later)

The most striking aspect of this approach is how little it depends on future development.

It does not require multimodal models beyond what already exists. It does not require fine-tuning. It does not require platform-level feature releases. Any environment capable of rendering HTML and executing JavaScript can participate in this loop today.

This makes the technique portable and resilient. It works in hosted platforms, local tools, and experimental UIs alike. More importantly, it shifts agency toward the user. Instead of waiting for platforms to expose richer interaction modes, users can construct them themselves by treating generated code as first-class output.

Multimodal interaction is not something that will arrive all at once through official updates. It is already emerging wherever execution is allowed to follow generation.

## Limits, Risks, and Failure Modes

Treating generated code as a live interface surface introduces real constraints that should not be minimized.

The most immediate risk is execution safety. Rendering arbitrary HTML, CSS, and JavaScript—even when produced by an LLM—creates an attack surface. Without sandboxing, strict origin isolation, and disabled network access, the system becomes vulnerable to unintended side effects. This is not a theoretical concern; it is a standard property of executing code, regardless of its source.

A second limitation is reliability. While LLMs are competent front-end code generators, they are not deterministic compilers. Generated interfaces may fail silently, partially render, or degrade over successive turns. As complexity increases, the likelihood of subtle bugs rises. This makes the approach best suited for exploratory tools, prototypes, and conceptual interfaces rather than production-critical systems.

State management presents another constraint. Many conversational rendering loops reset execution context on each turn, either by design or for safety. Without explicit state serialization and rehydration, interactive artifacts can lose continuity. This places the design burden on the wrapper and rendering layer, not on the model itself.

There is also a cognitive failure mode. When interfaces are generated too quickly or too fluidly, users may over-attribute stability or intentionality to what is, in practice, a probabilistic system. The more “alive” an interface feels, the more important it becomes to preserve inspectability and reversibility. Generated tools should remain legible, editable, and discardable.

None of these limits negate the approach. They define its current operating envelope. The point is not to replace conventional software engineering, but to expand the space of immediate, low-friction interaction that sits upstream of it.

{% include ad.html %}

## Conclusion: Text Is the Control Plane, Not the Interface

What changes when generated code is rendered in real time is not the intelligence of the system, but the role of language.

In a text-only chat, language must carry everything: explanation, behavior, and result. Once executable artifacts are allowed to exist alongside text, language can relax into a different function. It becomes a control plane—used to specify intent, adjust parameters, and request transformation—while the primary interaction happens elsewhere.

This reframing resolves a long-standing tension in LLM use. Users are not actually asking models to *describe* tools. They are asking models to help them *use* tools, or to construct new ones on the fly. The frustration many experience with chat interfaces stems from the fact that the model often delivers the logic of a tool, but the interface refuses to host it.

Real-time rendering closes that loop. It allows conversations to accumulate structure, not just context. It turns responses into surfaces that can be tested, manipulated, and evolved. And it does so without waiting for platform roadmaps or model breakthroughs.

Multimodal interaction is already present in today’s systems. The remaining work is not generative. It is architectural.

## Contextual Recommendation

For teams and individuals thinking seriously about how tools, interfaces, and reasoning systems evolve over time, this pattern fits into a broader design concern: preserving continuity between intent, artifact, and use.

Primary Design Co.’s work on documentation as design practice explores this problem from a complementary angle—how reasoning, structure, and artifacts can remain traceable as systems grow. Read more here:

[Documentation as Design Practice](https://www.primarydesignco.com)


## References

^[1]: OpenAI. “Advanced Data Analysis in ChatGPT.” *OpenAI Product Documentation*, updated 2023–2024.  
Describes ChatGPT’s code execution environment, sandboxing model, state reset behavior, and limitations of persistent execution across turns.  
https://platform.openai.com/docs/advanced-data-analysis

^[2]: Google DeepMind. “Introducing Gemini: A Multimodal AI Model.” *Google AI Blog*, December 6, 2023.  
Documents Gemini’s multimodal reasoning capabilities, including code generation, visual output, and inline rendering behavior.  
https://blog.google/technology/ai/google-gemini-ai/

^[3]: Anthropic. “Introducing Artifacts.” *Anthropic Product Updates*, March 2024.  
Explains Claude’s artifact system, separation of generated code/documents from chat text, and interaction constraints.  
https://www.anthropic.com/news/introducing-artifacts

^[4]: xAI. “Grok.” *xAI Product Overview and Public Demonstrations*, 2023–2024.  
Describes Grok’s conversational model, real-time information emphasis, and experimental interface affordances.  
https://x.ai/grok
