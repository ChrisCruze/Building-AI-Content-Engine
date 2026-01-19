# Modular AI Agent Stack for High-Quality Content Production

## Summary

A three-stage AI orchestration framework separating Research, Outlining, and Writing to ensure content originality and SEO depth.

## Description

A framework slide illustrating the data flow, inputs, and outputs between three specialized AI agents.

## Insight

Separating the 'Researcher' (insight extraction) from the 'Writer' (prose generation) is the critical step to avoiding generic AI content.

## Input


# Spec: Researcher, Outline & Writer Agents for Social Dining Content

## How to Orchestrate AI Content Agents for Original, SEO-Rich Work

> "Each agent should work from a small, consistent set of documents so you can chain them cleanly and prompt them for originality, surprising insights, and real social‑dining flavor."

- **Modular document-driven system** enables clean handoffs between Researcher → Outline → Writer agents[^1]
- **Each agent uses specific inputs/outputs** and follows a structured prompt template[^2]
- **Emphasis on originality, SEO, and emotional relevance** to stand out in saturated content markets[^3]
- **Researcher focuses on insights, not prose**; **Writer focuses on scenes, not summaries**[^4]
- **Outlines bridge data and narrative**—turning raw research into story-ready scaffolding[^5]

---

## 🧠 Researcher Agent

### 📥 Inputs
- `idea_brief.md`: topic, audience, goal, working titles, target format
- `voice_guidelines.md` *(optional)*: tone, banned phrases, brand/style cues

### 📤 Outputs
- `YYYY-MM-DD-topic-research.md`
- Optional: `surprising_insights.md` (separate doc of hooks/angles)

---

### 🗂️ Research Doc Contents

| Section | Description |
|--------|-------------|
| `Search landscape` | 5–10 URLs + notes (angle, strength, content gaps) |
| `Keywords & intent` | Primary + secondary keywords, search intents, real phrasing |
| `Surprising insights` | At least 5 counter-intuitive ideas relevant to social/group dining |
| `Data & stats` | Bite-sized data with sources and relevance |
| `Event scan` | Real or typical dining events (e.g., Meetup, supper clubs) |
| `Anecdote prompts` | Prompts, not full anecdotes, for the writer to expand |

---

### 💡 Prompt Template

```prompt
You are a **content researcher** for a mobile social dining app.
Goal: prepare a research pack so another agent can write a deeply original, engaging article.

1. Read this brief:
– Topic: [paste]
– Audience: [paste]
– Goal: [paste]
– Cities: [paste]

2. Do SERP and audience research. Do **not** write the article.
3. Create a structured doc with:
- `Search landscape`
- `Keywords & intent`
- `Surprising insights`
- `Data & stats`
- `Event scan`
- `Anecdote prompts`

Constraints:
- Emphasize originality, insight density
- Focus on in-app behaviors (RSVPs, hosting, last-minute joins)
- Use bullet points, not prose
- Include sources as plain URLs
````

---

### 📄 Research Template

```markdown
# Research – [Working title]

## 1. Brief recap
- Topic:
- Audience:
- Goal:
- City / focus area:

## 2. Search landscape
- [URL] – [angle, strength, gap]
...

## 3. Keywords & intent
- Primary keyword:
- Secondary keywords:
- Search intent:
- Notes:

## 4. Surprising / non-obvious insights
1. Insight:
   - Why it matters:
   - Use in social dining:

## 5. Data & stats
- Stat:
  - Source:
  - Why it’s compelling:

## 6. Event scan
- Event name:
  - City / format:
  - Why it matters:
  - Article angle:

## 7. Anecdote prompts
- “The first time I went to a dinner where I knew no one…”
...
```

---

## 🧱 Outline Agent

### 📥 Inputs

* `idea_brief.md`
* `topic-research.md`
* Optional: `brand_story_bank.md` (real/fictional stories, character types)

### 📤 Output

* `YYYY-MM-DD-topic-outline.md`

---

### 🧩 Outline Contents

| Section                 | Details                                                      |
| ----------------------- | ------------------------------------------------------------ |
| `Working title options` | 2–5 curiosity-driven, keyword-aligned titles                 |
| `Hook ideas`            | Surprising stat, mini-anecdote, big question                 |
| `Section structure`     | H2s/H3s with bullets: key ideas, insights, events, anecdotes |
| `Anecdote slots`        | Mark where stories go (from story bank or generated)         |
| `SEO plan`              | Keywords, meta title, meta description, slug                 |

---

### 💡 Prompt Template

```prompt
You are an **outline architect** for long-form content about social dining and community.
Input: research doc + brief.
Output: a detailed outline that maximizes engagement, originality, and SEO. Don’t write the article.

Steps:
1. Extract top insights, stats, events.
2. Brainstorm 3–5 working titles (with primary keyword).
3. Write 2–3 hooks (stat, anecdote, question).
4. Create a hierarchical outline with:
   - Purpose, key bullets, insight/event/anecdote placement, app tie-in
5. Add SEO plan:
   - Keywords, meta title, meta description, URL slug

Constraints:
- Move narrative: problem → tension → insight → action
- Use at least one surprising insight in intro and outro
- Flag generic sections and suggest how to make them sharper
```

---

### 📄 Outline Template

```markdown
# Outline – [Working title]

## 1. Brief recap
- Audience:
- Goal:
- Primary keyword:
- Secondary keywords:

## 2. Title ideas
1. ...
2. ...

## 3. Hook ideas
- Hook A – Stat:
- Hook B – Mini anecdote:
- Hook C – Big question:

## 4. Structure

### H2: [Section]
- Purpose:
- Key points:
- Insights:
- Data:
- Event:
- Anecdote slot:
- App tie-in:

...

## 5. Conclusion plan
- Takeaway:
- Emotional close:
- CTA:

## 6. SEO notes
- Primary keyword:
- Secondary keywords:
- Meta title:
- Meta description:
- Suggested URL:
```

---

## ✍️ Writer Agent

### 📥 Inputs

* `idea_brief.md`
* `topic-research.md`
* `topic-outline.md`
* `voice_guidelines.md` *(tone, banned phrases, examples)*
* Optional: `story_bank.md`

### 📤 Output

* `YYYY-MM-DD-topic-draft-v1.md` (full blog/newsletter draft)

---

### 🧾 Writer Requirements

* **Follow outline exactly**
* **Hook**: Use and polish one proposed hook
* **Each section**:

  * Add a **concrete example** or **anecdote**
  * Explain stats in plain language
  * Reference real or relevant events
  * Mention app features where appropriate
* **Format for mobile**:

  * Short paragraphs
  * Bullet lists
  * Descriptive subheads
* **End with CTA** tied to the app

---

### 💡 Prompt Template

```prompt
You are a **long-form writer** for a mobile social dining app.
Your job: turn this outline into a vivid, emotionally compelling article.

Inputs:
- Brief: [paste]
- Research: [paste or reference]
- Outline: [paste]
- Voice: [paste key notes]

Instructions:
1. Follow the structure exactly.
2. Start with one polished hook.
3. Add story or concrete example in every section.
4. Integrate data/events naturally ("That means...")
5. Use bullets & short paras.
6. No generic filler. Replace vague claims with scenes or storylets.
7. End with specific CTA related to app.

Style: Friendly, smart, adult, local.
```

---

### 📄 Draft Template

```markdown
# [Working or final title]

> Meta title:  
> Meta description:  
> URL slug:

## Intro

[Hook: stat, anecdote, or question → leads into core problem]

## H2: [Section Title]
[1–2 line intro to section]

- [Paragraphs and bullets]
- [Anecdote where marked]
- [Data explained in human terms]
- [App example]

## H2: [Next Section]
...

## Conclusion

[Summarize core idea or shift]

**Call to action:** [Concrete, app-linked next step]
```

---

## ✅ Summary: How to Use This Stack

| Agent             | Input                      | Output              | Purpose                                |
| ----------------- | -------------------------- | ------------------- | -------------------------------------- |
| 🧠 **Researcher** | `idea_brief.md`            | `topic-research.md` | Extract original, usable insights      |
| 🧱 **Outliner**   | Brief + research           | `topic-outline.md`  | Translate insights into narrative flow |
| ✍️ **Writer**     | Outline + research + voice | `topic-draft-v1.md` | Turn outline into publishable story    |

Each agent is **narrow, structured, and reusable**. With small prompt tweaks and doc changes, this system scales from **SEO blogs** to **emotional newsletters**.

---

## References & Footnotes

[^1]: Modular doc formats ensure clarity and versioning across agents.

[^2]: Each agent is prompted for structure-first, prose-second work.

[^3]: SEO trends prioritize originality, usefulness, and insight density in 2025 and beyond: [source](https://www.siteimprove.com/blog/seo-content-optimization-best-practices/)

[^4]: Writer and researcher separation reduces generic fluff and repetitive conclusions.

[^5]: Outlines anchor the article’s logic and ensure content doesn't drift.
