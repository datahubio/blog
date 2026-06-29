---
title: "The Trillion-Fold Rise: How AI Training Compute Exploded"
description: "A data-driven look at how the computing power behind notable AI models has grown by over a trillion times in just a few decades."
date: 2026-06-29
authors: [DataHub Team]
---

## A Number That Defies Intuition

Since the 1950s, the amount of computing power used to train notable artificial intelligence models has grown by roughly a factor of ten billion billion. That is not a typo. The Epoch AI dataset, which tracks training compute across hundreds of landmark models, shows a curve so steep it barely fits on a conventional chart. To put it another way: the compute used to train a modern large language model is to the compute used to train early neural networks what the mass of the sun is to a grain of sand. This single fact reframes almost every conversation about AI progress.

## Reading the Curve

The chart below plots training compute, measured in floating point operations (FLOPs), for notable AI models from the 1950s to the present day. The vertical axis is logarithmic, meaning each step upward represents a tenfold increase, and still the line climbs at an alarming angle. Before roughly 2010, progress was steady but unremarkable. A doubling of compute every few years matched the broader pace of hardware improvement described by Moore's Law. Then something changed.

Around 2012, coinciding with the arrival of deep learning systems like AlexNet, the slope steepened noticeably. By the mid-2010s, models were consuming compute at a rate far beyond what chip improvements alone could explain. Researchers and companies were simply throwing more hardware at the problem, running training jobs across hundreds and then thousands of processors simultaneously. The dataset makes this inflection point impossible to miss.

<iframe src="https://datahub.io/ai/epoch-data-on-ai-models/v/0" width="100%" height="475px" frameborder="0"></iframe>

## Two Eras, Two Different Games

The Epoch data effectively tells the story of two distinct eras. In the first, compute scaled slowly, and algorithmic ingenuity mattered most. Researchers competed on the cleverness of their methods because raw compute was scarce and expensive. A single lab could train a competitive model on a university budget.

In the second era, which begins roughly around 2015 and accelerates sharply after 2018, the game changed. Models like GPT-3, PaLM, and their successors required compute budgets in the tens of millions of dollars. Training runs that once took days on a single machine now stretched across thousands of specialized chips for weeks at a time. The dataset shows that between 2010 and 2023, training compute for frontier models grew at roughly four to five times the pace predicted by Moore's Law alone. That gap represents deliberate investment, not passive technological drift.

## Why This Matters Beyond the Lab

Understanding this trajectory is not just an academic exercise. The concentration of compute at the frontier has real consequences for who gets to build the most capable AI systems. When training a single model costs tens of millions of dollars, only a handful of companies globally can afford to compete. The Epoch dataset makes this consolidation visible in a way that policy arguments alone cannot.

There is also a sustainability dimension that the raw numbers quietly surface. More compute means more energy. A training run consuming ten to the power of twenty-five FLOPs is drawing on data centers that run continuously for months. As the curve continues upward, questions about electricity grids, carbon footprints, and resource allocation become impossible to separate from questions about AI capability.

Finally, the data raises a genuinely open question: how much longer can this scaling continue? Some researchers argue the returns are already diminishing, that throwing more compute at existing architectures yields smaller and smaller gains in capability. Others point to the historical pattern and suggest we have not yet hit a ceiling. The Epoch dataset does not answer that question, but it gives anyone who wants to engage seriously with it an honest empirical foundation to start from.

## Explore the Full Picture

The dataset compiled by Epoch AI is among the most carefully maintained public resources on AI development. It covers not just compute but also publication dates, model domains, organizational affiliations, and parameter counts, offering dozens of angles from which to study how the field has evolved. Whether you are a researcher, a policymaker, or simply someone trying to understand why AI feels like it is moving so fast, the numbers here are worth sitting with.

You can explore the complete dataset, download the underlying data, and interact with the visualizations at https://datahub.io/ai/epoch-data-on-ai-models.
