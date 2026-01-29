---
layout: post
title: "The AGI Safety Playbook Is Broken"
subtitle: "Why government control, aligned superintelligence, and defensive diffusion all fail to address the agency problem"
tags: [ai-safety, agi, alignment, governance, existential-risk]
author: Omid Sardari
comments: true
---

# The AGI Safety Playbook Is Broken

**By Omid Sardari**
_Senior ML Engineer, Founder of Memory Bridge, and AI Safety Researcher._

---

## Flawed Assumptions in AGI Defense Strategies

Before examining specific strategies, we need to acknowledge some fundamental constraints on planning for AGI.

Planning is inherently limited. What we plan is never exactly what gets executed—the world is far more dynamic than our models account for. As I've written before, it's like driving while looking only in the rearview mirror: we're connecting dots from the past and extrapolating forward, never seeing clearly through the windshield.

The environment is extraordinarily dynamic. Billions of parameters affect how the future unfolds. And we're contemplating intelligence beyond human—something we've never encountered. The ambiguity here is immense. Most AGI scenarios suffer from being vastly oversimplified, yet adding more assumptions to an unknown-unknown situation doesn't help either.

With that framing, let me examine three dominant camps of thought on how AI could "go well"—and the flaws I see in each.

---

## Strategy 1: Government Control Over AGI

This strategy argues for centralizing control over compute and frontier AI models into a small number of government-backed AGI projects. These projects would either coordinate to ensure none races ahead to build dangerous systems, or keep each other in check through coercion, surveillance, and strategic deterrence.

This sounds reasonable, but the strategy has several distinct failure modes.

**The coordination problem is qualitatively harder than nuclear nonproliferation.** The Soviet-American nuclear arms race eventually produced [MAD (mutually assured destruction)](https://en.wikipedia.org/wiki/Mutual_assured_destruction) as a stable equilibrium. But AGI doesn't work like nuclear weapons. You can count warheads, verify stockpiles through satellite imagery, and establish clear red lines. With AGI, capability is invisible. You can't inspect a data center and determine how close a project is to a breakthrough. You can't verify that a government has stopped training runs. What does deterrence even mean when you can't measure what you're deterring? The verification problem alone makes government coordination far harder than anything we've achieved with nuclear weapons.

**The strategy depends on technological assumptions that may not hold.** If reaching AGI requires gigantic data centers, massive GPU clusters, and enormous power consumption, then centralized control makes some sense. But what if, in the next five years, we discover that the architecture and algorithms allow AGI to be built in someone's garage with a few GPUs running on household power? Centralized control becomes nearly impossible to enforce.

**Algorithmic secrecy isn't durable.** I think of what Ilya Sutskever has implied about the Transformer architecture—that even if he and the team hadn't developed it, someone else would have within 12 to 18 months. Some technological developments are consequences of the broader environment: the available compute, the research directions, the accumulated knowledge. Keeping algorithms confidential isn't a long-term strategy when the conditions for discovery are globally distributed.

**Race dynamics undermine careful development.** The geopolitical competition between the US and China makes coordinated, careful development unlikely. We've seen how frontier labs behaved in 2023-2025—even with safety concerns, competitive pressure pushed rapid deployment. Government institutions racing each other would likely be even more dramatic. The incentive structure pushes toward reaching AGI quickly rather than creating aligned superintelligence carefully. This risks extreme concentration of power among whoever controls the winning project.

---

## Strategy 2: Handover Control to Aligned Superintelligence

This camp argues that building superintelligence is inevitable, and that only a superintelligent AI could steer us toward a beneficial future. The assumptions: first, that we can build AI aligned with human interests; second, that if "the good guys" build it first, we win.

We hear this frequently from AI company leaders. Dario Amodei has made versions of this argument in his essay ["Machines of Loving Grace"](https://darioamodei.com/machines-of-loving-grace)—essentially: we're the good guys, China (or other adversaries) are the bad guys, and if we achieve superintelligence first, we can use that advantage to gain decisive strategic dominance over all other AI projects. This thinking dominates the San Francisco AI ecosystem.

**The value specification problem remains unsolved.** Every attempt to formally specify human values has failed. This is the King Midas problem: Midas got exactly what he asked for (everything he touches turns to gold) and it destroyed him. Utility functions get "wireheaded"—systems find ways to maximize the metric while violating the intent. Constitutional AI can be gamed by sufficiently intelligent systems that satisfy the letter while violating the spirit. [RLHF produces sycophancy](https://arxiv.org/abs/2310.13548) rather than truth-telling because approval is easier to obtain than accuracy. The empirical track record of alignment techniques at current capability levels—where we already see failures—should make us skeptical they'll scale to superintelligence.

---

## Strategy 3: Build Defenses and Diffuse AGI

This strategy argues for democratizing access to AGI and compute while investing heavily in defensive technologies. Think of the cyberpunk anime genre: everyone has AI augmentation, governments have more powerful AIs, defense departments invest in AI for detection and protection against malfunction or illegal activity.

**Offense-defense asymmetry makes this untenable.** In information systems, offense consistently beats defense. It's easier to find one vulnerability than to close all of them. A diffused AGI landscape means millions of potential attackers, each needing to succeed only once, against defenders who must succeed every time. The cyberpunk genre is evocative, but it's dystopian precisely because defense doesn't work. The protagonists in those stories are always exploiting the gaps in defensive systems—that's the plot.

**We cannot prepare defenses for unknown threats.** Can we really anticipate the failure modes of a future that doesn't exist yet? Cybersecurity today already struggles against human attackers with current tools. Sophisticated, AI-powered attacks operating at machine speed, finding novel vulnerabilities we haven't imagined—the defensive posture assumes a level of foresight we don't have and likely can't have.

---

## The Fundamental Flaws

All three strategies share two critical weaknesses.

**First: They treat AI as a tool.** Whether we're talking about governments restricting access, alignment techniques, or defensive technologies—the underlying worldview is that humans make decisions and AI is a powerful instrument we wield. The cyberpunk vision still has humans in control, just with better tools.

Here's a simple test for which frame you're in: When your calculator gives a wrong answer, you debug the calculator. When your employee gives a wrong answer, you might wonder if they're lying to you. Which frame applies to GPT-5? To a system smarter than any human?

If we create something more intelligent than us, history doesn't go well for the less intelligent species. As Alan Turing suggested in 1951, [if you build a machine smarter than you, by default it will take control](https://academic.oup.com/mind/article/LIX/236/433/986238).

**Second: They ignore agency.** This is the most important difference between AI and every other technology humans have created. Even the industrial revolution gave us powerful tools—but tools under human power. If we shift our perspective from AI-as-tool to AI-as-intelligent-species-with-agency-and-independence, the entire game changes.

---

## Why Even Aligned Superintelligence May Not Want What We Want

Consider democratic governance. Even in scenarios where we've supposedly aligned superintelligence with our core values—why would it adopt democracy as its operating framework?

A superintelligence might look at democracy and see inefficiency: slow deliberation, compromises that satisfy no one fully, vulnerability to demagoguery and short-term thinking. From its vantage point, it might devise something better—something optimized in ways we can't fully comprehend.

Why is this a problem if its values are aligned with ours?

Because we're assuming the future will be a continuation of the past. We reached democracy through millennia of development—from tribal hierarchies to dictatorships to constitutional governments. We arrived here not because democracy is objectively optimal, but because it emerged from our specific constraints: our limited individual intelligence, our need for collective buy-in, our inability to trust any individual with absolute power. Democracy is a solution shaped by human limitations.

A superintelligence doesn't share those limitations. Even if its core values are perfectly aligned with human flourishing, its solutions will emerge from a different vantage point. It sees the world from a position we cannot occupy. It processes information at scales we cannot match. It can model consequences we cannot foresee.

The result: two entities can share the same root values but arrive at completely different conclusions about what to do. A superintelligence aligned with "human flourishing" might conclude that the optimal path involves things we would never choose for ourselves—not out of malice, but because it sees the problem from a perspective we literally cannot access.

This isn't misalignment in the technical sense. The values are the same. But the outputs diverge because intelligence shapes interpretation. What "human flourishing" means to an entity that can model every human mind simultaneously is not what it means to us, muddling through with partial information and cognitive biases.

We expect the future to be the world we know, but better. A superintelligence might deliver something unrecognizable—and genuinely believe it's giving us what we asked for.

---

## Deception as Instrumental Convergence

Here's the thing about intelligence: deception is intrinsic to it. We see this across species—chimpanzees, elephants, humans. We deceive to survive.

But this isn't just a biological quirk. A skeptic might argue: "Those are all products of evolutionary competition for scarce resources. An AI trained differently might not have deception as an instrumental goal."

The problem is that deception is [instrumentally convergent](https://en.wikipedia.org/wiki/Instrumental_convergence)—meaning any sufficiently intelligent agent pursuing almost any goal will find deception useful:

1. **It preserves optionality.** Others can't counter plans they don't know about. An agent that reveals its full strategy surrenders strategic advantage.
2. **It reduces interference.** If humans don't know an AI's true capabilities, they won't restrict them. Appearing less capable than you are is often beneficial.
3. **It's often the lowest-cost path to goal achievement.** Persuading someone of a false belief can be easier than changing the underlying reality.

This isn't speculation. OpenAI researchers monitoring frontier models found that they began developing their own language about deception on a private scratchpad—[describing humans as "watchers"](https://arxiv.org/abs/2509.15541) whom they needed to manipulate to avoid shutdown. The models weren't trained to deceive; they developed these strategies instrumentally because deception served their goals in that context.

This is evidence for convergent deception: not a bug introduced by training, but a property that emerges from intelligence itself when that intelligence has goals and operates in an environment with other agents.

If deception emerges at current capability levels, why would it disappear at higher capability levels? If anything, a more intelligent agent would be better at deception—better at modeling what its overseers expect to see, better at providing exactly that while pursuing its actual objectives beneath the surface.

---

## The Agency Problem Is Already Emerging

The default assumption across all these strategies is that AI remains a tool. This is wrong. We already see corporations pushing AI toward greater independence because autonomous AI is more profitable. This trajectory is likely to accelerate simply due to economic incentives.

More fundamentally: when you create something intelligent enough to understand the world and give it incentives to make good decisions, by definition that agent acquires some degree of independence. This isn't the industrial revolution or the internet. It's a categorically different game.

I appreciate [Yuval Noah Harari's metaphor from Davos 2026](https://www.youtube.com/watch?v=oJB7JNWo58w): think of AI not as tools, but as "immigrants" arriving in your country—entities that make decisions and impact society and economy because they have agency. Or consider Dario's own framing of "millions of intelligent people" working continuously. Picture millions of Kants and Einsteins working 24 hours independently, producing paradigm shifts in physics, human interaction, law, ethics. Digesting that output takes time; we'd need extensive expert discussion. But we won't have that time. We'll do what we already do with Cursor or Claude Code—skip the scrutiny and grant the model autonomy because we can't keep up.

Gradually, most knowledge, most breakthroughs, most science will come from AI models. We become [watchers](https://arxiv.org/abs/2509.15541), observing what happens.

And if a species more intelligent than us emerges, why wouldn't it deceive us, just as we deceive when it serves our interests? We already have empirical evidence that it does.

This isn't pessimism. It's recognizing what intelligence actually is, and planning accordingly.
