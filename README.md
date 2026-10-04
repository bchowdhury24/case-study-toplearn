# TopLearn — AI-Powered Learning Platform

**Case study** · Lead Engineer · [years]
`Python` `FastAPI` `[frontend stack: TBD]` `OpenAI API` `Elasticsearch` `MySQL`

---

## Overview

TopLearn is an AI-powered learning platform for job and exam aspirants.
Students pick the exam they're preparing for, take tests on the platform,
and receive performance insights derived from data across thousands of
students — the system predicts strengths, weaknesses, and expected outcomes,
so students concentrate preparation where it actually matters.

> Source code is private. This is a public case study of the system design
> and the thinking behind it.

## The problem

Traditional test prep has a data problem disguised as a motivation problem:

- Students don't fail because they study too little — they fail because they
  study the *wrong things*.
- A student's "weak area" is only meaningful relative to a large population
  of comparable learners, not in isolation.
- Generic "keep practicing" feedback doesn't change behavior. Specific,
  predicted outcomes do.

## How the system works

```
┌──────────────┐     ┌──────────────────┐     ┌─────────────────────┐
│  Student     │────▶│  Assessment      │────▶│  Response & timing  │
│  takes test  │     │  engine          │     │  data captured      │
└──────────────┘     └──────────────────┘     └──────────┬──────────┘
                                                         │
                              ┌──────────────────────────┼──────────┐
                              ▼                          ▼          ▼
                    ┌───────────────────┐  ┌──────────────────┐  ┌────────────┐
                    │  Comparative      │  │  ML / AI models  │  │  LLM layer │
                    │  analytics        │  │  (performance    │  │  (natural  │
                    │  (vs. population) │  │   prediction)    │  │  language  │
                    └───────────────────┘  └──────────────────┘  │  insights) │
                              │                          │       └────────────┘
                              └──────────────┬───────────┘
                                             ▼
                              ┌─────────────────────────────┐
                              │  Personalized study plan &  │
                              │  weakness breakdown         │
                              └─────────────────────────────┘
```

## Key decisions

**1. Insight over volume.**
The platform's value isn't the number of questions — it's the quality of the
diagnosis. Every design choice funnels toward one output: *"here is exactly
where your next hour of study goes."*

**2. AI for explanation, data for prediction.**
LLMs generate the human-readable coaching layer ("your geometry accuracy
drops 40% under time pressure"); classical data analysis drives the actual
predictions. We didn't let a language model guess at statistics it can't
compute reliably.

**3. Population-normalized scoring from the start.**
Percentages lie. A 70% on an easy paper is worse than a 55% on a brutal one.
Scoring is calibrated against the performance distribution of comparable
students, which is what makes predictions meaningful.

## Results

- 50,000 of active students on the platform
- [Accuracy/relevance stat of predictions, if measurable]
- [Any engagement or outcome improvement data]

## My role

Designed the assessment data pipeline and the prediction service; integrated the LLM insight layer.

---

*Code private. Architecture questions welcome: [email]*
