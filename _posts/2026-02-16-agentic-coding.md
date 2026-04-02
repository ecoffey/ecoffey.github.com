---
layout: post
title: Agentic Coding
updated_at: 2026-02-21
---

In some ways LLMs are just another tool in the belt. However, they are one that shifts the emphasis of the engineer's role toward design, requirements gathering, and testing. LLM tooling can be a multiplier for your effectiveness, you just have to make sure you are bringing a value greater than 1 to multiply by. Here is how I've been using agentic coding tools in my day to day work, what I've learned so far, and what I'm thinking about moving forward.

## Generating Artifacts to React To

One of the most useful things an LLM can do is sidestep the "blank page" problem. I use agentic tools to generate initial plans, writeups, and implementations that I can react to and tweak. The first draft does not need to be right, it needs to be something concrete I can push against. This is often faster than starting from scratch, because editing and refining is a different (and often easier) mode of thinking than creating from nothing.

## Tell It What, Not How

When giving instructions I focus on what I want, not how to do it. I describe the desired outcome, the constraints, and the context. I usually leave the implementation approach to the tool unless the "how" is critical to the overall intent, for example when a specific algorithm or pattern matters for performance or maintainability. This keeps instructions concise and gives the tool room to leverage patterns it finds in the codebase.

## Stay in the Loop

I do not let the tool commit automatically. I review what it generates, have it tweak and refactor, and stay hands on throughout the process. In between bigger chunks of work within the same session, I stage the changes so that the working copy diff always shows me what it is currently doing. This keeps the feedback loop tight and makes it easy to course correct. It also means I am never surprised by what ends up in a commit.

## Invest in Integration Tests

LLMs do really well with objective measures of correctness that they can react to. Integration tests are especially valuable here because they cast a wide net and are harder to "fake" than narrow unit tests. If you can give the tool an initial seed test, or a small set of them, it can generate more integration tests on its own. This creates a virtuous cycle: the tests keep the tool honest, and the tool helps you expand test coverage. Investing time in good integration tests up front pays dividends in the quality and reliability of everything the tool produces after that.

## Looking Forward

These tools are great at removing _accidental_ friction, but it is important to recognize that not all friction is bad. Wrestling with a problem is what builds deeper understanding, and that understanding is what lets you bring the tool to bear effectively. I've had a lot of success using LLMs on codebases, in no small part because I spent a lot of time manually refactoring them and adding features, sweating the naming details and how an internal API should fit together. That investment paid off because the LLM could leverage the "language" I had already put in place.

A related tension is what this means for software as a team sport. LLMs strongly incentivize working alone. When a tool can generate a plan, write the code, and help you reason through edge cases, the pull toward solo execution is strong. But the value of working as a team is not just throughput. Pairing builds shared context and surfaces the things you didn't know you didn't know. Code review builds collective ownership. Onboarding a new engineer builds the team's long-term capacity. All of these activities contribute to a team building up a "shared reality" of what they own and operate.

My worry is that LLM tools work so well solo that they allow individuals to diverge from that shared reality both more quickly and to a larger degree, making re-integration more painful. This is compounded by the fact that these tools are inherently stochastic: even if everyone is using the same AGENTS.md, you will get different results. The same concern applies at the individual level: these tools are especially valuable to me because of my industry experience. How do we, as an industry, ensure new software engineers also get that foundational experience so that they can responsibly leverage them?

I don't have a clean answer here. I suspect the solutions will look like changes to process and tooling, shifting the focus from generating artifacts to more efficiently allowing the *team* to process those artifacts through their shared reality viewpoint.
