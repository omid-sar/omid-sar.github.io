---
layout: post
title: "VIbe Coding Tips: Writing Code That Flows"
subtitle: "Practical tips for writing clean, maintainable, and enjoyable code"
date: 2025-06-06 18:00:00
tags: [coding-tips, best-practices, clean-code, python, productivity]
comments: true
author: Omi S
---

# Vibe Coding Tips and Tricks

## Introduction

Inspired by [Andrej Karpathy’s vibe coding tweets](https://x.com/karpathy/status/1886192184808149383) and [Simon Willison’s thoughtful reflections](https://simonwillison.net/2025/Mar/19/vibe-coding/), this post explores the evolving world of coding with LLMs. Karpathy introduced *vibe coding* as a playful, exploratory way to build apps using AI — where you simply “say stuff, see stuff, copy-paste stuff,” and trust the model to get things done. He later followed up with a more structured rhythm for professional coding tasks, showing that both casual *vibing* and disciplined development can work hand in hand.

Simon added a helpful distinction: not all AI-assisted coding should be called vibe coding. That’s true — but rather than separating these practices, we prefer to see them as points on the same creative spectrum. This post leans toward the middle: it shares a set of practical, developer-tested patterns that make working with LLMs more productive and less chaotic.

A big part of this guidance is also inspired by [Tom Blomfield’s tweet thread](https://x.com/t_blom/status/1915803644894826914), where he breaks down a real-world workflow based on his experience live coding with LLMs.

---
### 1. Planning:
- **Create a Shared Plan with the LLM:** Start your project by working collaboratively with an LLM to draft a detailed, structured plan. Save this as a `plan.md` (or similar) inside your project folder. This plan acts as your north star — you’ll refer back to it repeatedly as you build. Treat it like documentation for both your thinking process and your build strategy.
- **Provide Business Context:** Include real-world business context and customer value proposition in your prompts. This helps the LLM understand the "why" behind requirements and make better trade-offs between technical implementation and user experience.
- **Implement Step-by-Step, Not All at Once:** Instead of asking the LLM to generate everything in one shot, move incrementally. Break down your plan into clear steps or numbered sections, and tackle them one by one. This improves quality, avoids complexity creep, and makes bugs easier to isolate.
- **Refine the Plan Aggressively:** After the first draft is written, go back and revise it thoroughly. Delete anything that feels vague, over-engineered, or unnecessary. Don’t hesitate to mark certain features as *“Won’t do”* or *“Deferred for later”*. Keeping a “Future Ideas” or “Out of Scope” section helps you stay focused while still documenting things you may revisit.
- **Explicit Section-by-Section Development:** When you're ready to build, clearly tell the LLM which part of the plan you're working on. Example: *“Let’s implement Section 2 now: user login flow.”* This keeps the conversation clean and tightly scoped, reducing irrelevant suggestions and code bloat.
- **Request Tests for Each Section:** Ask for relevant tests to ensure new features don’t introduce regressions.
- **Request Clarification:** Instruct the model to ask clarifying questions before attempting complex tasks. Add "If anything is unclear, please ask questions before proceeding" to avoid wasted effort on misunderstood requirements.
- **Preview Before Implementing:** Ask the LLM to outline its approach before writing code. For tests, request a summary of test cases before generating actual test code to course-correct early.
### 2. Version Control:
- **Run Your Tests + Commit the Section:** After finishing implementation for a section, run your tests to make sure everything works. Once it's stable, create a Git commit and return to your `plan.md` to mark the section as complete.
- **Commit Cleanly After Each Milestone:** As soon as you reach a working version of a feature, commit it. Then start the next feature from a **clean slate** — this makes it easy to revert back if things go wrong.
- **Reset and Refactor When the Model “Figures It Out”:** Sometimes, after 5–6 prompts, the model finally gets the right idea — but the code is layered with earlier failed attempts. Copy the working final version, reset your codebase, and ask the LLM to re-implement that solution on a fresh, clean base.
- **Provide Focus When Resetting:** Explicitly say: “Here’s the clean version of the feature we’re keeping. Let’s now add [X] to it step by step.” This keeps the LLM focused and reduces accidental rewrites.
- **Create Coding Agent Instructions:** Maintain instruction files (like `cursor.md`) that define how you want the LLM to behave regarding formatting, naming conventions, test coverage, etc.
- **Build Complex Features in Isolation:** Create clean, standalone implementations of complex features before integrating them into your main codebase.
- **Embrace Modularity:** Keep files small, focused, and testable. Favor service-based design with clear API boundaries.
- **Limit Context Window Clutter:** Close tabs unrelated to your current feature when using tab-based AI IDEs to prevent the model from grabbing irrelevant context.
- **Create New Chats for New Tasks:** Start fresh conversations for different features rather than expecting the LLM to maintain context across multiple complex tasks.
### 3. Write Test:
- **Write Tests Before Moving On:** Before implementing a new feature, write tests — or ask your LLM to generate them. LLMs are generally good at writing tests, but they tend to default to low-level unit tests. Focus also on **high-level integration tests** that simulate real user behavior.
- **Prevent Regression with Broad Coverage:** LLMs often make unintended changes in unrelated parts of the code. A solid test suite helps catch these regressions early.
- **Simulate Real User Behavior:** For backend logic, ask: "What would a test look like that mimics a user logging in and submitting a form?" This guides the model toward valuable integration testing.
- **Maintain Consistency:** Paste existing tests and ask the LLM to "write the next test in the same style" to preserve structure and formatting.
- **Use Diff View to Monitor Code Changes:** In LLM-based IDEs, always inspect the diff after accepting code suggestions. Even if the code looks correct, unrelated changes can sneak in.
### 4.Bug Fixes:
- **Start with the Error Message:** Copy and paste the exact error message into the LLM — server logs, console errors, or tracebacks. Often, no explanation is needed.
- **Ask for Root Cause Brainstorming:** For complex bugs, prompt the LLM to propose 3–4 potential root causes before attempting fixes.
- **Reset After Each Failed Fix:** If one fix doesn’t work, revert to the last known clean version. Avoid stacking patches on top of each other.
- **Add Logging Before Asking for Help:** More visibility means better debugging — both for you and the LLM.
- **Watch for Circular Fixes:** If the LLM keeps proposing similar failing solutions, step back and reassess the logic.
- **Try a Different Model:** Claude, GPT-4, Gemini, or Code Llama each have strengths. If one stalls, try another.
- **Reset + Be Specific After Root Cause Is Found:** Once you find the issue, revert and instruct the LLM precisely on how to fix just that one part.
- **Request Tests for Each Fix:** Ensure that fixes don’t break something else.


Vibe coding might sound chaotic, but done right, AI-assisted development can be surprisingly productive. These tips aren’t a complete guide or a perfect workflow — they’re an evolving set of heuristics for navigating LLM-based software building.

> Whether you’re here for speed, creativity, or just to vibe a little smarter, I hope you found something helpful. If not, well… blame the model. 😉
