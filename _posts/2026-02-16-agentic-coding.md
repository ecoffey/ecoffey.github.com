---
layout: post
title: Agentic Coding
---

In my [philosophy]({{ "/philosophy.html#ai--llm-tooling" | relative_url }}) I talk about how LLM tooling can be a multiplier for your effectiveness, and how these tools shift the emphasis of the engineer's role toward design, requirements gathering, and testing. Agentic coding is where that plays out in practice. What follows is how I've been using agentic coding tools in my day to day work, and what I've learned so far.

## Generating Artifacts to React To

One of the most useful things an LLM can do is sidestep the "blank page" problem. I use agentic tools to generate initial plans, writeups, and implementations that I can react to and tweak. The first draft does not need to be right, it needs to be something concrete I can push against. This is often faster than starting from scratch, because editing and refining is a different (and often easier) mode of thinking than creating from nothing.

## Tell It What, Not How

When giving instructions I focus on what I want, not how to do it. I describe the desired outcome, the constraints, and the context. I usually leave the implementation approach to the tool unless the "how" is critical to the overall intent, for example when a specific algorithm or pattern matters for performance or maintainability. This keeps instructions concise and gives the tool room to leverage patterns it finds in the codebase.

## Stay in the Loop

I do not let the tool commit automatically. I review what it generates, have it tweak and refactor, and stay hands on throughout the process. In between bigger chunks of work within the same session, I stage the changes so that the working copy diff always shows me what it is currently doing. This keeps the feedback loop tight and makes it easy to course correct. It also means I am never surprised by what ends up in a commit.

## Invest in Integration Tests

LLMs do really well with objective measures of correctness that they can react to. Integration tests are especially valuable here because they cast a wide net and are harder to "fake" than narrow unit tests. If you can give the tool an initial seed test, or a small set of them, it can generate more integration tests on its own. This creates a virtuous cycle: the tests keep the tool honest, and the tool helps you expand test coverage. Investing time in good integration tests up front pays dividends in the quality and reliability of everything the tool produces after that.
