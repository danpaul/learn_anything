---
name: "lesson"
description: "Create a templated lesson file in ./lessons from any topic (e.g. 'het perfectum', 'SQL joins', 'Bayes' theorem', 'photosynthesis'). Use when the user asks to create, write, or add a lesson. The lesson is source material for the socratic-tutor skill."
---

# Lesson

Turn a topic into one lesson file at `lessons/<slug>.md`, where `<slug>` is the
topic in lowercase kebab-case ASCII (`het-perfectum.md`, `sql-joins.md`).

The socratic-tutor skill teaches from this file: each numbered key point becomes
one subskill in its skill map, and the examples are its raw material for questions.

## Before writing

- If no topic was given, or it is too broad for 4-10 key points (e.g. "verbs",
  "databases"), ask the user to narrow it. Do not pick a subtopic for them.
- Determine the **level** of the learner (e.g. "A2-B1", "beginner", "first-year
  undergraduate") and the **language** the lesson is written in. Take them from the
  request; otherwise match existing files in `lessons/` on the same subject area;
  otherwise use the language of the request and ask for the level.
- If the file already exists, ask before overwriting.

## Content rules

- Write the whole lesson in one language, including the fixed template labels. No
  translations alongside. For a language-learning topic this is normally the
  language being learned.
- Write for the stated level: vocabulary, depth, and prerequisites that fit it, and
  only the points and exceptions a learner at that level needs.
- 4-10 key points per lesson. Each must be a single testable idea with a short,
  distinct title: a rule, concept, fact, or technique the learner can be questioned
  on by itself. Split a point that covers two ideas.
- Order key points from basic to advanced; a point may rely only on earlier ones.
- 3-5 examples per key point, in whatever form fits the topic: a sentence, a worked
  calculation, a code snippet, a concrete case. Bold the part of each example that
  shows the point. Where a contrast clarifies the point, add one incorrect example
  or common mistake, marked with `*`.
- Only state what you are certain of. If you are unsure of a point or an example,
  leave it out and tell the user rather than guessing.

## Template

Follow this structure exactly; do not add or rename sections. The template is
shown in English: translate the fixed labels (`Level`, `Subject`, `Key points`,
`Point`, `Examples`) into the lesson's language, and reuse the labels of existing
lessons in that language.

```markdown
# <Topic>

- **Level:** <level>
- **Subject:** <one sentence: what this lesson covers and when you use it>

## Key points

### 1. <Short title of the key point>

**Point:** <the key point in one or two sentences>

**Examples:**

- <example with the **relevant part** in bold>
- <example>
- <example>

### 2. <Short title of the key point>

...
```

## After writing

Tell the user the file path and that they can start with
"teach me lessons/<slug>.md" — the numbered key points are the subskills.
