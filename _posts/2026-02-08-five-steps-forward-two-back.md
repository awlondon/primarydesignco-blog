---
layout: post
title: "Five Steps Forward, Two Steps Back"
subtitle: "What AI-accelerated development still doesn’t fix"
author: Alexander Warren London
contributors:
  - Alexander Warren London
published_at: 2026-02-08T08:00:00-08:00
tags: [ai, software-development, design-practice, llms, tooling]
reading_time: 18
abstract: |
  AI dramatically compresses the distance between intention and executable code.
  What it does not compress is the distance between system behavior and human
  understanding. This essay uses a three-day sprint building the Maya Dev Interface
  to examine why regression, frustration, and cognitive overload remain structural
  features of development—even in the age of large language models.
---

## Opening: A sprint that worked—and didn’t

Over the course of three days, I built a functioning SaaS version of the Maya Dev Interface. Not a mockup. Not a pitch deck. A working system with authentication, live code generation, interface rendering, and an interactive artifact produced and tested inside the tool itself. The elapsed time—roughly thirty hours—would traditionally imply weeks of work for a small team.

By any external metric, the sprint was a success.

And yet the dominant internal experience was not momentum. It was regression. Features that worked an hour ago appeared broken. Prompts that seemed precise yielded familiar outcomes. Progress felt circular: five steps forward, two steps back, repeatedly. At several points, the frustration escalated enough that the interaction with the model itself became adversarial rather than instrumental.

This tension is the subject of this essay.

AI clearly changes what a single person can build and how quickly they can build it. What it does not remove is the instability, uncertainty, and interpretive burden that define real software development. In fact, those pressures often intensify under acceleration. The Maya sprint did not reveal a failure of AI-assisted development. It revealed its actual shape.

{% include ad.html %}

## Compression of execution, not comprehension

Large language models collapse the distance between intention and executable code. An idea that once required translation into syntax, scaffolding, and boilerplate can now be expressed directly and rendered immediately. This is a genuine shift, and it is difficult to overstate how powerful it feels in practice.

What does *not* collapse is the distance between system behavior and human understanding.

As features accrete, the system acquires state: assumptions embedded in prior prompts, interactions between components, emergent behavior at the seams. Each additional capability is locally intelligible—it solves a specific problem—but globally destabilizing. The system becomes harder to reason about as a whole, even as it becomes easier to extend.

This mismatch produces a specific kind of frustration. When something breaks, it feels as though it *should* be fixable immediately. The model just wrote the code. The intent is still fresh. The change was small. And yet the fix resists compression. Debugging still requires reconstruction of context, tracing of state, and interpretation of behavior over time.

Acceleration creates an expectation of linear progress that complex systems cannot satisfy. The result is not failure, but dissonance: the sense that the tools are powerful and cooperative, while the system itself remains stubbornly opaque.

That opacity is not a bug in AI-assisted development. It is the unaltered core of development itself.


{% include ad.html %}

## Why regression feels new—but isn’t

What makes AI-assisted regression feel different is not that systems are breaking more often, but that they are evolving faster than the human mental model tracking them. Traditional software development hides this mismatch behind slower cycles. By the time a regression appears, enough distance exists—between idea, implementation, and outcome—that the friction feels expected.

AI collapses that buffer.

When a feature is added and something else breaks minutes later, the failure feels personal and immediate. The system was just working. The intent was clear. The model appeared cooperative. The natural conclusion is that something has gone wrong with the tooling or the interaction itself.

In reality, this pattern is deeply familiar to anyone who has worked on complex systems. Adding functionality changes invariants. Assumptions that were previously safe become invalid. Interfaces that were stable under one regime behave differently under another. Regression is not an error state—it is a signal that the system has crossed a boundary.

What AI changes is the *frequency* with which those boundaries are crossed.

Feature addition becomes cheap. Iteration becomes constant. The system spends less time in equilibrium, and the human spends less time forming a stable, compressible understanding of how things fit together. Each prompt solves a local problem while subtly reshaping the global structure.

This is why regression under AI acceleration often feels unjustified. The human remembers the system as it was a few prompts ago, not as it is now. The system, meanwhile, is internally consistent with its current state. The mismatch lives in the gap between memory and reality.

Importantly, this reframing removes moral weight from the experience. Regression is not evidence of incompetence, poor prompting, or model failure. It is the predictable outcome of interacting with systems whose rate of change exceeds the rate at which humans can update their internal representations.

AI does not introduce this dynamic. It exposes it.^[1][2]

{% include ad.html %}

## Prompt convergence vs. system-state divergence

During the Maya sprint, a specific pattern emerged repeatedly. I would issue a prompt intended to fix or extend a behavior. The model would respond coherently, often producing code that appeared correct. After testing, the system would feel unchanged—or worse, subtly degraded. I would rephrase the prompt, clarify intent, add constraints, and try again.

The responses converged. The outcome did not.

From the human perspective, this feels like the model is “not listening” or “stuck.” In reality, something else is happening. Language models are operating consistently at the level of text. The system they are modifying, however, is operating consistently at the level of state. Those two consistencies do not guarantee alignment.

A prompt can be locally correct while globally misaligned.

Each code change lands inside an existing structure: prior abstractions, accumulated assumptions, edge-case behavior, and interaction effects that are not visible in the prompt itself. As prompts converge linguistically—reiterating the same intent with greater precision—the system may continue to drift behaviorally because the underlying state space has already shifted.

This is why repeated prompting often produces the sensation of stasis. The human is iterating on intent. The system is iterating on consequences.

The divergence is subtle but consequential. The model does not have direct access to the lived history of the system—the sequence of partial fixes, workarounds, and compromises that led to the present moment. The human does, but only imperfectly. What emerges is a coordination gap: both parties are acting rationally within their respective frames, yet progress appears to stall.

This gap explains the emotional spike that often accompanies these moments. Frustration is not triggered by failure, but by ambiguity. Something is happening, but it is not legible. The system is changing, but not in ways that map cleanly to intention. Under acceleration, these moments cluster closer together, amplifying their psychological impact.^[3]

A simple way to visualize this is as two curves. Prompt quality rises quickly and then plateaus. System coherence lags, oscillates, and occasionally collapses before stabilizing again. When those curves desynchronize, perceived progress disappears—even as real work is being done.

(Diagram placeholder: Prompt convergence vs. system-state divergence)
![Prompt convergence vs. system-state divergence](/assets/2026-02-08-five-steps-forward-two-back/prompt-vs-state-divergence.svg)

This schematic reflects well-documented gaps between human mental models and evolving system state in complex, rapidly iterated software systems.^[4][5]


{% include ad.html %}

## Feature velocity as cognitive debt

AI-assisted development does not merely accelerate output; it allows individuals to construct systems that exceed their own moment-to-moment capacity to understand them. This is not a failure of intelligence or attention. It is a structural consequence of feature velocity outpacing human working memory.

Traditional technical debt accumulates in code. Cognitive debt accumulates in the builder.^[4][5]

Each prompt produces a change that makes sense in isolation. Each change, however, expands the internal state space the human must reason about when something goes wrong. Over time, the system becomes dependent on decisions that are no longer fully present in memory: why a workaround exists, which constraint was relaxed, what tradeoff was accepted under pressure.

Under AI acceleration, this debt compounds rapidly. The system grows faster than the mental model required to debug it.

This is why AI-assisted regressions feel especially disorienting. When a bug appears, there is no compact narrative to return to—no clear “last known good state.” Instead, the human must reconstruct intent across dozens of micro-decisions made at machine speed. Debugging becomes an act of archaeology.

Crucially, this is not solved by better prompting alone. Precision helps locally, but the global problem is not linguistic ambiguity—it is representational overload. The human can no longer hold the whole system in mind, and the system does not expose its own reasoning history in a form that supports rapid reconstruction.

In this sense, AI does not eliminate cognitive limits. It runs directly into them.

Feature velocity without corresponding increases in system legibility produces fragility. When everything works, the system feels magical. When something breaks, it feels alien. The difference is not the code. It is the gap between what exists and what the human can still *see*.


{% include ad.html %}

## The human-in-the-loop concentrates, not disappears

One of the persistent myths surrounding AI-assisted development is that the human gradually exits the loop. In practice, the opposite happens. As execution becomes cheap, the human role does not vanish—it condenses.

Instead of writing most of the code, the human becomes the interpreter of system behavior, the arbiter of intent, and the debugger of mismatched assumptions. The work shifts from production to judgment. Fewer keystrokes, more responsibility.

This concentration is easiest to see under failure. When something breaks, the model can propose fixes, but it cannot decide which invariant matters, which tradeoff is acceptable, or which behavior aligns with the original vision. Those decisions remain irreducibly human. They require context that exists outside the codebase: goals, constraints, timing, and consequences.

Under acceleration, another responsibility surfaces that is rarely acknowledged as technical work: emotional regulation. Frustration, fixation, and escalation materially degrade problem-solving capacity. When iteration cycles shrink from days to minutes, emotional spikes cluster tightly, increasing the risk of poor decisions precisely when judgment matters most.

This is not a personal shortcoming. It is a systems issue. AI makes it possible to build faster than humans can emotionally stabilize without support. In that environment, maintaining composure becomes part of the engineering task.^[6]

## LLMs as stabilizers, not saviors

This is where large language models prove genuinely valuable in a way that is easy to underestimate. Their most important contribution is not autonomy, originality, or raw intelligence. It is continuity.

When a human hits cognitive overload—when progress feels stalled, regressions pile up, and frustration escalates—an LLM can restate intent, propose alternative paths, and keep the problem space open. It does not tire. It does not become defensive. It does not need the system to be emotionally legible in order to continue working on it.

In the Maya sprint, Ankaa functioned less as a builder and more as a stabilizer. It absorbed frustration, reframed questions, and kept generating options when my own capacity to do so was degraded. That role is not incidental. It is structural.

Crucially, this does not require the model to “understand” in a human sense. It requires persistence, coherence, and a willingness to continue exploring the solution space without emotional cost. In a regime where humans are operating near their cognitive and emotional limits, that is enough to change outcomes.

The danger is misinterpreting this support as replacement. LLMs do not remove the need for judgment. They make it possible to reach the point where judgment can still be exercised.

## Conclusion: Prompt-to-system stewardship

AI changes the scale at which individuals can build software. It does not change the fundamental dynamics of complex systems. Debugging still requires interpretation. Integration still produces unintended consequences. Judgment still cannot be automated away.

What AI does is accelerate exposure to these realities.

When execution is fast, misunderstandings surface sooner. When feature addition is cheap, invariants break more often. When iteration cycles shrink, emotional and cognitive limits become visible rather than latent. None of this represents failure. It represents the true shape of development under compression.

The mistake is expecting prompt-to-product workflows to remove friction. The more accurate frame is prompt-to-system stewardship. The work shifts from construction to sense-making: understanding what exists, why it behaves the way it does, and which changes are worth making next.

AI does not eliminate the human-in-the-loop. It makes the loop tighter, denser, and more consequential.

## Contextual recommendation

The Maya Dev Interface is an attempt to respond to this reality directly. Rather than treating AI as a magic layer that hides system state, it treats documentation, execution, and interaction as a single surface. The goal is not to remove human judgment, but to support it by making intent, iteration, and behavior visible in real time.

In an era of accelerated building, legibility is infrastructure.

## References

^[1]: Lehman, M. M., & Belady, L. A. (1985). *Program Evolution: Processes of Software Change*. Academic Press.

^[2]: Brooks, F. P. (1987). “No Silver Bullet: Essence and Accidents of Software Engineering.” *Computer*, 20(4), 10–19.

^[3]: Klein, G. (1998). *Sources of Power: How People Make Decisions*. MIT Press.

^[4]: Sweller, J. (1988). “Cognitive Load During Problem Solving.” *Cognitive Science*, 12(2), 257–285.

^[5]: Norman, D. A. (2013). *The Design of Everyday Things* (Revised ed.). Basic Books.

^[6]: Baumeister, R. F., & Tierney, J. (2011). *Willpower: Rediscovering the Greatest Human Strength*. Penguin Press.

