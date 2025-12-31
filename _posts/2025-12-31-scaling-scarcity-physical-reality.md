---
layout: post
title: "Scaling, Scarcity, and the Physical Reality of AI Progress"
subtitle: "Why 'diminishing returns' is a pricing signal, not a doom forecast"
tags: [ai, scaling, hardware, economics, machine-learning, infrastructure]
author: Omid Sardari
comments: true
---

# Scaling, Scarcity, and the Physical Reality of AI Progress

**By Omid Sardari**
_Senior ML Engineer, Founder of Memory Bridge, and AI Safety Researcher._

> **Note:** This piece isn't a direct reply to anyone's article. It's an independent reflection inspired by overlapping arguments from Demis Hassabis, Dario Amodei, and Tim Dettmers about scaling, limits, and the economic reality of frontier AI.

---

### The Oil Well Analogy

In the early days of oil extraction, you'd punch a hole in the ground in Texas and crude would practically leap out at you. The economics were simple: drill more, get more. Then the easy reserves depleted. The industry didn't die—it evolved. Horizontal drilling, offshore platforms, fracking, tar sands. Each technique unlocked new resources, but at higher cost and complexity. The barrel of oil still had value; extracting it just required more engineering per barrel.

AI scaling is entering its horizontal drilling phase.

The pattern is showing up across very different voices. Demis Hassabis has recently pointed to signs of diminishing returns on today's large-scale AI investment while still arguing that scaling should be pushed aggressively as a key ingredient on the path to AGI ([Axios AI+ Summit](https://www.axios.com/2025/12/05/ai-deepmind-hassabis-gemini)). Tim Dettmers (CMU/AI2) frames it more mechanically: if hardware and systems stop improving fast enough, the industry drifts from "roughly linear spend for linear gains" toward rapidly rising costs for smaller improvements ([Why AGI Will Not Happen](https://timdettmers.com/2025/12/10/why-agi-will-not-happen/)). Dario Amodei has emphasized that progress is not guaranteed to be smooth or predictable ([Dwarkesh interview](https://www.dwarkesh.com/p/dario-amodei); [Big Technology transcript](https://singjupost.com/transcript-anthropic-ceo-dario-amodeis-interview-on-big-technology-podcast/)).

What looks like disagreement is often just framing. Optimists describe this as non-systematic progress that can be extended with new techniques; pessimists call it diminishing returns. Either way, the discussion points to the same toolkit: specialized hardware like Tensor Cores ([NVIDIA Volta whitepaper](https://images.nvidia.com/content/volta-architecture/pdf/volta-architecture-whitepaper.pdf)), lower-precision math, KV-cache and serving optimizations ([vLLM PagedAttention](https://arxiv.org/abs/2309.06180)), and test-time compute scaling.

---

### "Diminishing Returns" Is Not One Claim—It's a Family of Claims

When people say "scaling is slowing," they often mean different things:

- **"Not systematic improvement"** — progress continues, but it's uneven and dependent on clever hacks.
- **"Diminishing returns on spending"** — improvements cost more each cycle.
- **"Scaling is not enough"** — bigger models alone no longer guarantee breakthroughs.

When leaders like Hassabis and Amodei talk about progress getting harder, I don't hear "AI is over." I hear something more concrete: **the easy phase is ending**. Early gains came from scaling on abundant web text plus rapidly improving hardware—the equivalent of that Texas gusher. Now the marginal gains increasingly depend on *where* you spend, *what* data you can still obtain, and *how* you turn compute into reliable capability rather than flashy demos.

---

### The Library of Babel Problem: Why Data Scarcity Is Real

Imagine you're training a model to be a better doctor. The entire public internet contains maybe a few thousand high-quality clinical reasoning examples written by actual physicians explaining their thought process. Meanwhile, there are hundreds of thousands of Reddit comments about whether pineapple belongs on pizza.

"Data scarcity" doesn't mean we're running out of bytes. It means we're running out of *the right* bytes.

There's credible analysis that high-quality, human-written text could become a binding constraint on pretraining as early as 2026-2028 ([Epoch AI report](https://epoch.ai/blog/will-we-run-out-of-data-limits-of-llm-scaling-based-on-human-generated-data)). But Hassabis argues the ceiling is higher if you widen the lens: multimodal data (especially video) expands the frontier, and synthetic data can fill gaps when you can verify correctness.

Here's where it gets interesting. The pivot to synthetic data is often framed as a clever workaround—and it is. But it also reveals a deeper truth: **if you can't just scrape more internet, you have to manufacture learning signals.**

Consider how AlphaGo worked. DeepMind didn't need millions of human Go games. They had the game engine generate millions of self-play games where correctness was verifiable (did you win or lose?). The system learned from synthetic experience because the domain allowed it.

But here's the crucial caveat: Go is a closed system. The board is 19×19. The rules are fixed. The state space, while large, is finite and fully observable. There's no ambiguity about whether a move is legal or who won. AlphaGo's search space and complexity are orders of magnitude smaller than what LLMs face when navigating real-world roles and open-ended tasks. You can't "self-play" your way to better medical diagnosis or legal reasoning because the rules aren't fixed, the state isn't fully observable, and "winning" isn't cleanly defined.

Now consider medicine. You can't "self-play" a cancer diagnosis. You can't simulate whether a treatment works without actual patients and actual time. The verification loop is years, not milliseconds.

This is why synthetic data has a known failure mode: training on model-generated text can degrade diversity ("model collapse") ([Nature paper](https://www.nature.com/articles/s41586-024-07566-y)). It's like a library that keeps photocopying its own photocopies—each generation loses fidelity.

But the impact of synthetic data varies dramatically by domain. In programming and mathematics, you can generate millions of problems and verify solutions automatically—the compiler or proof checker closes the loop. Same with games, puzzles, and any environment where correctness is mechanically verifiable. In these closed-loop domains, synthetic data can be genuinely high-quality.

Contrast that with medicine, creative writing, or wedding film editing. There's no compiler that tells you whether a diagnosis is correct, whether a paragraph is beautiful, or whether a cut lands emotionally. The feedback loop requires expensive human judgment, real-world outcomes, or both. Synthetic data in these domains risks amplifying whatever biases and errors already exist in the training set.

So the "synthetic future" demands careful curation, filtering, and evaluation. It's not free lunch; it's a more expensive lunch with extra steps—and the bill varies wildly depending on whether your domain has a closed loop or not.

---

### Computation Is Physical: What Chip Design Taught Me

My first degree is in electrical engineering, and I've worked close enough to IC design to know that "computation is physical" isn't a philosophical statement. It's just the job.

Here's what non-hardware folks often miss: **Moore's Law was never magic. It was a temporary alignment of multiple improving curves.**

Consider the efficiency gap: the human brain operates on roughly 20 watts—the power of a dim lightbulb—while our attempts to approximate its capabilities require datacenters consuming gigawatts. This isn't just an engineering problem to be optimized away; it suggests our current "scaling" approach is a brute-force approximation that may be hitting fundamental physical limits.

Transistor counts kept growing. But Dennard scaling—the era when you could raise clock speeds without blowing the power budget—broke down around 2005 ([Berkeley EECS report](https://www2.eecs.berkeley.edu/Pubs/TechRpts/2016/EECS-2016-89.pdf)). That's why your laptop doesn't run at 10 GHz today. The industry pivoted to multicore and accelerators because the old trick stopped working.

Here's a concrete example. In the 1990s, a CPU engineer could assume: "If I shrink the transistor, it runs faster AND uses less power." That let Intel just keep cranking clock speeds. But around 65nm, physics intervened. Shrinking transistors started causing current to *leak* even when the transistor was "off"—like a faucet that drips no matter how hard you close it. Suddenly, smaller meant *hotter*, not cooler. The free lunch ended.

Now apply this lens to AI. The sexy metric is FLOPs—how many floating-point operations per second. But the actual bottleneck in modern AI serving is often **moving data**, not doing math. This is the classic "memory wall" problem ([Wulf & McKee 1995](https://libraopen.lib.virginia.edu/downloads/4b29b598d)).

Picture a chef (the compute unit) and a pantry (memory). The chef can chop vegetables at superhuman speed. But if the pantry is across the street and the chef has to walk there for every ingredient, the actual meal prep is slow. Modern GPUs are that chef: incredibly fast at math, constantly waiting for data. This is why software optimizations like vLLM's PagedAttention—which applies virtual memory paging to LLM serving—can deliver 2-4x throughput improvements without touching the hardware at all.

This is why I appreciated Tim Dettmers's framing of transformers as a tight compromise between local computation (the chopping) and global information movement (fetching from the pantry). The MLP layers do local transformation. The attention layers pool global information. The architecture isn't just a clever idea—it's a **physically efficient compromise** for current silicon.

I'm not claiming transformers are optimal forever. But if a new architecture wins, it probably wins partly because it rebalances physical costs—especially memory movement—not because it's clever in isolation.

---

### The Land Rush: When Strategy Becomes a Trap

Since ChatGPT's launch in late 2022 ([OpenAI announcement](https://openai.com/blog/chatgpt)), the industry has operated on a simple thesis: **first mover wins, winner takes most.**

This isn't crazy. Network effects are real. If everyone uses ChatGPT, developers build for ChatGPT, which makes more people use ChatGPT. We've seen this movie before with Google Search, Facebook, and Amazon.

But the thesis creates a specific behavior pattern:

- Subsidize usage to prevent churn (even at a loss)
- Over-provision capacity to ensure uptime
- Prioritize adoption metrics over profit metrics
- Spend aggressively because *not* spending looks like falling behind

Here's the trap: **this logic assumes the capability curve keeps bending upward fast enough to justify the spend.** If model gains slow, the calculus flips. Huge infrastructure becomes a liability, not an asset.

The numbers are staggering. AI infrastructure spending surged from roughly $15 billion in 2024 to $125 billion in 2025—a 733% increase—much of it financed by external capital rather than retained earnings ([Reuters via Yahoo Finance](https://finance.yahoo.com/news/bridgewater-warns-big-techs-reliance-152235389.html)). And the "bubble" conversation isn't fringe anymore:

- Hassabis has warned about overpricing and a correction for AI startups ([Business Insider](https://www.businessinsider.com/demis-hassabis-google-deepmind-ai-startup-valuation-correction-bubble-2025-12))
- Amodei has warned that forecasting real demand is guesswork and bubble dynamics are possible ([The Verge](https://www.theverge.com/column/837779/anthropic-ai-bubble-warning))
- Bridgewater has flagged big tech's reliance on external capital to fund the AI boom as a risk ([Reuters via Yahoo Finance](https://finance.yahoo.com/news/bridgewater-warns-big-techs-reliance-152235389.html))

This reminds me of the fiber-optic boom of the late 1990s. Companies laid vast networks anticipating exponential bandwidth demand. The demand eventually materialized—but not before most of those companies went bankrupt. The infrastructure got built. The builders didn't survive to profit from it.

---

### The Atoms Problem: Why Software Speed ≠ Deployment Speed

Even if AGI-level systems emerged tomorrow, the physical world has its own clock speed.

Amodei makes this explicit in [*Machines of Loving Grace*](https://www.darioamodei.com/essay/machines-of-loving-grace): breakthroughs that affect the physical world still require real-world feedback loops.

Consider drug discovery. An AI might identify a promising cancer compound in hours instead of years. Great. But you still need:

- Synthesis and testing (months)
- Animal trials (months to years)
- Phase I/II/III human trials (years)
- Regulatory review (months to years)
- Manufacturing scale-up (months)
- Distribution and training (months)

The AI accelerates *one step* in a pipeline where other steps have irreducible physical latency. You can't simulate whether a drug causes liver damage in humans over five years—you have to wait five years and check.

Now, there's a compelling counterargument here: what if we could simulate the cell itself? If we had accurate enough models of cellular behavior, we could run virtual trials and escape the physical bottleneck entirely. This is a real research direction, and it's not crazy.

But here's the catch: building a simulator that faithfully mimics real cell behavior faces the same data constraints we've been discussing. You need enormous amounts of high-quality biological data to train and validate such a model—experimental measurements, omics data, clinical outcomes. That data is finite, expensive to generate, and often proprietary. You're not escaping the data wall; you're just hitting it in a different place.

Michael Levin, whose work on developmental biology and bioelectricity at the Allen Discovery Center is some of the most fascinating in the field, calls this the "inverse problem": even if you had a perfect molecular simulation, you'd still face the near-impossible task of figuring out *which* of millions of possible interventions produces the outcome you want. As he puts it, complex biological systems "are simply too complex to micromanage" ([Levin et al., 2022](https://www.mdpi.com/1099-4300/24/6/819)). The search space is combinatorially explosive. (If you're curious about the boundary between computation and living systems, [his work](https://drmichaellevin.org/) is worth exploring.)

Until we reach a tipping point where we have both the right architecture to simulate real-world systems *and* enough data to train those simulators reliably, we remain bounded by physical feedback loops. The simulation escape hatch is plausible in the long run, but it doesn't change the near-term calculus.

The same physical constraints apply to manufacturing (you can't simulate metal fatigue without actual stress cycles), construction (concrete cures at the speed of chemistry), and regulation (bureaucracies move at bureaucracy speed).

So when someone says "AGI is imminent," I translate it into an operational question: **how fast can capability turn into deployed productivity, under real constraints?** That's not philosophy. It's engineering plus procurement plus regulation plus organizational change management.

---

### A Pragmatic Synthesis: The Boring Future Might Be the Right Bet

The argument isn't that progress stops. It's that **progress gets priced correctly.**

Three constraints shape the frontier:

- **Physical constraints** limit compute, memory, and energy
- **Economic constraints** limit how long you can fund unprofitable scale  
- **Data constraints** limit where scaling continues smoothly

Yet value can still explode. Small benchmark jumps can yield major productivity gains. Diffusion across industries can multiply impact even without "AGI."

The center of gravity shifts from "more of everything" toward "better pipelines": verified synthetic data where possible, simulation where it actually adds new experience, human-in-the-loop where the target is narrow or high-stakes. That's what "linear progress needs exponential resources" looks like in practice.

If I had to bet on the next phase, I'd bet less on "one model to rule them all" and more on:

- **Better inference economics** (the boring work of making models cheaper to run)
- **Better data pipelines** (targeted human feedback plus selective synthetic generation)
- **Better integration** (workflow embedding, tool use, distribution)
- **More "good enough" models** deployed in thousands of specific contexts

The core mistake is treating AGI narratives as if they erase economics and implementation. Even if capabilities keep improving, the winners may be organizations that convert capability into reliable, affordable, widely adopted systems—not the ones chasing maximal capability at any cost.

The oil industry didn't die when the gushers stopped. It got more sophisticated. AI is doing the same thing—and that's not a tragedy. It's just engineering.

> This connects to themes from [*The Uniqueness Economy*](https://omid-sar.github.io/the-uniqueness-economy-part-1/) series—particularly how the economics of AI capability intersect with the economics of human agency. If scaling gets harder, the question of *who benefits* from incremental progress becomes sharper, not duller.
