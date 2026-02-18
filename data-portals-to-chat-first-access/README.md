---
title: "From Data Portals to Chat-First Data Access"
description: "Queryless extends portal thinking into WhatsApp, Telegram, and Slack so users can ask data questions and get analytics-ready answers in chat."
date: 2026-02-18
authors: [Anuar Ustayev]
---

![[hero.png]]

Data portals solved a critical problem: making datasets discoverable, structured, and reusable. But discovery is only half the journey. The next bottleneck is interaction.

Most users still need help turning a business question into a useful answer. Even with dashboards in place, teams often bounce between tools before they can act.

Queryless explores the next step: chat-first data access built on top of governed data foundations.

## The Core Idea

Instead of asking users to enter a BI tool first, let them start in interfaces they already use:

- WhatsApp
- Telegram
- Slack

They ask a question in plain language. Queryless returns a clear answer in chat, with analytics built in (summary + table/chart output). For deeper work, users can open an on-demand report or dashboard view.

Dashboards are still valuable, but they become a second step, not the first.

## Why This Fits the DataHub World

If your organization already invests in quality metadata, governance, and clear models, you can treat chat interfaces as a new interaction layer over those assets.

That means:

- discovery and governance remain in your portal stack
- question-answer interaction moves into everyday chat workflows
- analyst oversight remains a quality and trust control

In other words: this is not a replacement for portal architecture, but an extension of it.

## Practical Workflow

1. A user asks a data question in chat.
2. Queryless generates a structured response (summary + table/chart).
3. The response can be shared in the same conversation.
4. If needed, a deeper report/dashboard view is generated on demand.

This reduces context switching and shortens time-to-first-answer for recurring business questions.

## What To Watch During Adoption

Teams testing this model should define guardrails early:

- metric definition ownership
- acceptable confidence and quality thresholds
- escalation points for analyst review
- which question types stay chat-only vs. require deeper report workflows

The best results come from explicit governance, not improvisation.

## Try It

Queryless is live in Telegram at [@queryless_bot](https://t.me/queryless_bot) with public datasets for experimentation.

If your team runs a DataHub-style stack and wants to evaluate chat-first data access, this is a practical way to test where it adds value first.

Read the original product post: [Talk to your data](https://www.querylessai.com/blog/talk-to-your-data).
