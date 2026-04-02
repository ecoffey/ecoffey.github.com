---
layout: post
title: Shared Reality and LLMs
---

Teams build and maintain a shared model of what they own and operate. Call it a shared reality. It is not stored anywhere explicitly; it lives in the team, built up through code reviews, pairing, and accumulated context. I wrote about this tension in my [agentic coding post]({% post_url 2026-02-16-agentic-coding %}): LLMs are most productive in a solo, heads-down mode, but that mode is insular. Individuals can diverge from the team's shared reality more quickly and to a larger degree than before.

There is a subtler version of the problem. Before agentic tools, a lot of engineering thinking happened *in the code*: in naming decisions, structural choices, the shape of an internal API. That thinking was legible to teammates through code review. Now that energy moves upstream to the prompt, the plan, and how you guide the agent. The code that lands in a PR may be just as readable as before, but the thinking behind it has become invisible.

Code review still matters: it is how bugs get caught and collective ownership gets built. But it is no longer a complete picture of what happened. If I want to understand a teammate's decisions, I do not just want to see the code. I want to see what they told the LLM to do, and how they shaped it.

Design documents have always been a place to cultivate and share this kind of thinking. But in practice, the Agile era set a high bar for when they were warranted: a feature had to feel large enough to justify the investment. Most code never got a design doc, and even when it did, the document typically covered the initial design and not the non-trivial decisions that accumulated during implementation. LLMs change that calculus. The planning workflow is lightweight enough to use for much more of the work, not just the marquee features, which means more thinking can be made visible, more of the time.

## Plans as Artifacts

One response is to make the upstream work visible. I have been experimenting with keeping plan files in the repo alongside the code. A plan is written before implementation starts and describes what is being built and why. Feedback on it, inline comments and review notes, gets incorporated before any code exists. The plan becomes a durable record of intent, committed with the code: linkable, reviewable, and available to future LLM sessions working in the same codebase.

I built a Claude Code plugin to make this workflow concrete: [plan-impl-skills](https://github.com/ecoffey/plan-impl-skills). It provides a `plan` → `process-feedback` → `implement` loop. Plans collect in a `_plans/` directory and are committed alongside the code. The `process-feedback` skill reads inline comments directly from the plan file, so feedback left during review round-trips back into Claude without any copy-paste.

## The CU Boulder Talk

I developed and presented these ideas in a guest lecture for the University of Colorado Boulder's ATLS 4214 (Big Data Architecture). The [talk materials are on GitHub](https://github.com/ecoffey/agentic-coding-talk): slide deck and a demo project built for the talk using this workflow. The demo project, `logpipe`, was built using the plan-impl-skills loop: plans first, black-box integration tests as the contract, agent-driven implementation second.

The core argument of the talk: agentic tools do not change what good software looks like. They change how fast you can get there, and where you spend your attention. The challenge for teams is making sure that attention stays visible. It now happens at the plan level, not just in the code.
