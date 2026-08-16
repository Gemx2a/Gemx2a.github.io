---
title: "What Makes an Agent 'Agentic'"
category: ai
tags: [agents, llm]
date: 2026-08-15
summary: "The difference between a chatbot and something that can plan, act, and check its own work."
---

## The idea

A plain LLM call answers one prompt. An "agent" adds a loop: the model can
decide to use a tool, look at the result, and decide what to do next — on its
own, across multiple steps — until the task is done or it asks for help.

## The core ingredients

- **Tools** — ways for the model to act on the world (search, run code, call an API)
- **State** — memory of what's happened so far in the task
- **A loop** — the model deciding the *next* step, not just answering once

## Open questions I still have

- Where's the right line between "autonomous" and "needs a human to confirm"?
- How do you evaluate an agent's judgment, not just its final output?

*(Replace this with your own notes — this is just a placeholder showing the format.)*
