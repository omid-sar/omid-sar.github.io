---
layout: post
title: "The Gym as a Lab Bench: Iterating on Habits with LLMs"
subtitle: "A small, repeatable workout experiment — and the AI toolchain around it: critique loops, a memory layer, and a visual interface for routine."
tags: [ai, workflow, llm, memory-layer, training, personal-systems]
author: "Omi S"
comments: true
---

## Story

I’m not here to sell anyone on a “perfect” workout. I’m doing the opposite: a small experiment I can actually repeat. Four days a week. Two sets per exercise. High effort, low ceremony. Chest/back/shoulders one day. Legs/arms the other. It’s not optimal. It’s executable.

The interesting part wasn’t the split. It was the workflow around it.

I wrote a messy first draft in my notes like everyone else, then treated it like code: find the bugs, remove duplication, and fix missing coverage. I bounced between [ChatGPT](https://chatgpt.com/) and [Gemini](https://gemini.google/) for critique loops. I also used a beta [Memory Bridge](https://memorybridgeai.com/) setup so I didn’t have to keep retyping the same constraints (equipment, joint annoyances, and the volume I’m realistic about maintaining). Memory Bridge is basically the “project state” that stays stable while I swap models in and out—so each iteration compounds instead of resetting. [Claude](https://www.anthropic.com/claude) was weirdly hit-or-miss for this kind of structural cleanup, which was honestly reassuring: these tools have “profiles,” not just raw IQ.

Then I hit a real friction point: I don’t want to read paragraphs between sets. I want cues.

So I used [Nano Banana Pro](https://gemini.google/overview/image-generation/) to generate consistent workout icons. The first images were useful. The second pass was the moment it stopped feeling like “generation” and started feeling like “editing”: keep the style, fix the mechanics, change only what’s wrong. With reference images, it mostly did what I meant.

## Concept

This is what “AI in daily life” is turning into for me: not one assistant, but a small toolchain I orchestrate. Text models for reasoning and critique. A memory layer for continuity. Image models for turning intent into something my body can follow without thinking too hard.

We used to talk about AI as if it lives in big announcements. I keep seeing it show up in the small UX layer between intention and action—the part where you either do the thing, or you don’t. The future isn’t just better answers. It’s better interfaces for your routines.

<hr>

<h3>Workout icons</h3>

<div style="display:grid;grid-template-columns:repeat(4,minmax(0,1fr));gap:12px;align-items:start;">
  <a href="{{ '/assets/img/workout/gemini-nano-generated-workout-day-1.png' | relative_url }}" target="_blank" rel="noopener noreferrer">
    <img src="{{ '/assets/img/workout/gemini-nano-generated-workout-day-1.png' | relative_url }}"
         alt="Workout day 1"
         style="width:100%;height:auto;border-radius:10px;">
  </a>

  <a href="{{ '/assets/img/workout/gemini-nano-generated-workout-day-2.png' | relative_url }}" target="_blank" rel="noopener noreferrer">
    <img src="{{ '/assets/img/workout/gemini-nano-generated-workout-day-2.png' | relative_url }}"
         alt="Workout day 2"
         style="width:100%;height:auto;border-radius:10px;">
  </a>

  <a href="{{ '/assets/img/workout/gemini-nano-generated-workout-day-3.png' | relative_url }}" target="_blank" rel="noopener noreferrer">
    <img src="{{ '/assets/img/workout/gemini-nano-generated-workout-day-3.png' | relative_url }}"
         alt="Workout day 3"
         style="width:100%;height:auto;border-radius:10px;">
  </a>

  <a href="{{ '/assets/img/workout/gemini-nano-generated-workout-day-4.png' | relative_url }}" target="_blank" rel="noopener noreferrer">
    <img src="{{ '/assets/img/workout/gemini-nano-generated-workout-day-4.png' | relative_url }}"
         alt="Workout day 4"
         style="width:100%;height:auto;border-radius:10px;">
  </a>
</div>

<style>
  @media (max-width: 900px) {
    .post-content div[style*="grid-template-columns:repeat(4"] { grid-template-columns: repeat(2, minmax(0, 1fr)) !important; }
  }
  @media (max-width: 520px) {
    .post-content div[style*="grid-template-columns:repeat(4"] { grid-template-columns: 1fr !important; }
  }
</style>
