# Cuculi-AI-Marketing: Automated Multi-Agent Content Production Architecture

## Summary

A comprehensive workflow transforming strategy into execution using a repository-based multi-agent system integrated with Airtable and MongoDB. The system leverages specialized agents for research, writing, and editing.

## Description

An architectural overview of the Cuculi-AI-Marketing repository, detailing the agent pipeline, tech stack integrations, and file structure.

## Insight

The repository's directory structure itself functions as the executable logic and system architecture, rather than just code organization.

## Input

````markdown
# Cuculi-AI-Marketing: A Production Repository for AI Content Generation

## From Strategy to Execution — A Complete AI Content Workflow

> *"The repository structure is the system. Every folder, every file, every integration point serves a specific purpose in the content generation workflow."*

- **Purpose-Built Repository**: The structure *is* the system—folders and files mirror the content generation pipeline[^1]
- **Airtable-Centric Workflow**: Airtable is the single source of truth and drives the agent orchestration[^2]
- **Multi-Agent System**: Specialized LLM agents handle planning, research, writing, editing, and quality evaluation[^3]
- **Integrated Stack**: MongoDB for user/event data, LLMs (Claude & ChatGPT), and a web app interface[^4]
- **Scalable, Maintainable Architecture**: Modular design enables easy expansion and iteration[^5]

---

## 📁 Repository as a Production System

### ✅ Goals

- Turn strategy into **executable workflows**
- Generate content using **multi-agent AI orchestration**
- Enrich with real-world data from **MongoDB**
- Manage and review through **Airtable and web interface**

### 🎯 Content Lifecycle

1. Idea input via **Airtable**
2. Agent pipeline: *Planner → Researcher → Outliner → Writer → Editor → Critic*
3. Content rendered, reviewed, and published from **index.html**

---

## 🗂️ Repository Structure

```plaintext
Cuculi-AI-Marketing/
├── docs/                  # Strategic content guidelines
├── agents/                # Markdown-defined agent logic
├── templates/             # Content generation templates
├── blogs/                 # Generated blog artifacts
├── integrations/          # Python integrations (Airtable, MongoDB, LLMs)
├── index.html             # Web app UI for reviewing blogs
├── run.py                 # Main orchestration pipeline
└── README.md              # Project overview and usage
````

| Folder          | Purpose                                 |
| --------------- | --------------------------------------- |
| `docs/`         | Strategy, writing principles            |
| `agents/`       | Markdown instructions per agent         |
| `templates/`    | Standardized generation formats         |
| `blogs/`        | Individual blog content folders         |
| `integrations/` | API sync with Airtable, MongoDB, Claude |
| `index.html`    | Web interface for blog review           |
| `run.py`        | Main entry point and agent orchestrator |

---

## 🧠 Agent Roles & Templates

Each agent performs a specific content task:

| Agent           | Function                           |
| --------------- | ---------------------------------- |
| `planner.md`    | Decides strategy and content theme |
| `researcher.md` | Gathers signals and context        |
| `outliner.md`   | Structures blog outline            |
| `writer.md`     | Drafts the blog post               |
| `editor.md`     | Refines tone, flow, clarity        |
| `critic.md`     | Evaluates and scores output        |

🔁 These agents use structured templates:

* `research.md`: MongoDB + external sources
* `outline.md`: Skeleton of blog
* `draft.md`: First LLM draft
* `final.md`: Reviewed and refined copy

---

## 🚀 The Workflow: Idea → Published Blog

### 📌 Step-by-Step Flow

1. **Idea Entry**
   Captured in Airtable with fields: `title`, `brief`, `audience`, `status`, `keywords`, `event IDs`

2. **Trigger (`run.py`)**
   Detects new ideas → creates `blogs/{slug}` folder → saves `brief.md` → starts agent pipeline

3. **Research Agent**
   Uses MongoDB + external sources to generate `research.md`

4. **Outliner Agent**
   Reads `brief.md` + `research.md` → outputs `outline.md`

5. **Writer Agent**
   Generates `blog.md` using Claude, guided by brand guidelines

6. **Editor Agent**
   Refines style, adds clarity, optimizes for user psychology

7. **Critic Agent**
   Scores blog and updates Airtable with status

8. **Airtable Sync**
   Pushes all artifacts back to Airtable for team review

9. **Web App Review**
   `index.html` renders Airtable data for management, filtering, and publishing

---

## 🔌 Integration Architecture

### Airtable

* **Content Table** contains:

  * Title, brief, research, outline, draft, final content
  * Status (`idea → published`)
  * Metadata: keywords, target audience, LLM used, event references

* **Bidirectional sync** via `airtable_integration.py`

---

### MongoDB

* Event + user data enriches content:

  * Never-Engaged Veterans (400+ days idle)
  * One-Time Experimenters (conversion targets)
  * Recent event stats and feedback

* Queried by the Researcher Agent via `mongodb_integration.py`

---

### LLM Services

| Agent      | Preferred LLM |
| ---------- | ------------- |
| Researcher | ChatGPT       |
| Writer     | Claude        |
| Editor     | Claude        |

Integrated via:

* `claude_integration.py`
* `chatgpt_integration.py`

Features: automatic fallback, rate limit handling, configuration via YAML

---

## 🖥️ Web App: `index.html`

Airtable-driven interface with:

* 🔍 Full-text search
* 🔃 Status filtering
* 👁️ Preview of research, outline, and draft
* 📝 Inline editing (optional)
* 🚦 Status updates (review, publish, etc.)

**Architecture**: Pure frontend, no backend — uses Airtable API directly.

---

## ✅ Scope & ❌ Exclusions

### ✅ In Scope

* Agent-driven content generation
* Airtable + MongoDB integrations
* Modular agent files and templates
* Web interface for review
* Multi-LLM orchestration

### ❌ Out of Scope

* Publishing to platforms (e.g., Medium, Substack)
* Real-time collaboration
* Analytics dashboards
* Image generation
* Full SEO automation

---

## 📅 Implementation Roadmap

| Phase | Focus                               | Timeline |
| ----- | ----------------------------------- | -------- |
| **1** | Repository setup & structure        | Week 1–2 |
| **2** | MongoDB, Airtable, LLM integrations | Week 2–3 |
| **3** | Agent instructions + orchestration  | Week 3–4 |
| **4** | Workflow automation via `run.py`    | Week 4–5 |
| **5** | Build frontend UI `index.html`      | Week 5–6 |
| **6** | Test with real content + refine     | Week 6–7 |

---

## ✍️ Blog Examples (In Progress)

### Blog 1: *"I Downloaded a Social Dining App and Didn’t Go for 6 Months"*

* **Target Audience**: Never-Engaged Veterans
* **Focus**: Hesitation, activation triggers
* **Psychology**: Empathy → identification → curiosity
* **Data**: 3,961 users, 400+ days since signup

📝 Status: `outline.md` complete
🧠 Research: Decision paralysis patterns
🎯 Goal: Convert dormant users through relatable narrative

---

### Blog 2: *"I Went to Dinner With 7 Strangers — and It Wasn’t Awkward"*

* **Target Audience**: Never-engaged & one-time experimenters
* **Focus**: Breaking social fear, post-event positivity
* **Psychology**: Fear disconfirmation + curiosity gap
* **Data**: Event feedback from recent dinners

📝 Status: `research.md` complete
🧠 Signals: Social anxiety, positive feedback loops
🎯 Goal: Encourage first-timers to attend an event

---

## 🧾 Final Thoughts

The **Cuculi-AI-Marketing** repository is:

* 🧩 **Composable**: Each file contributes to an automated content system
* 🧠 **Intelligent**: Uses agents guided by markdown files and prompt templates
* 🔁 **Integrated**: Airtable + MongoDB + LLMs in harmony
* 🔍 **Transparent**: Clear flow from idea to execution

---

## 🫱 Invitation to Builders

**Lessons from building this:**

* Structure *is* strategy.
* Markdown can power agent logic.
* Airtable is an underrated CMS.
* MongoDB data personalizes and grounds content.
* Simplicity wins — even in AI workflows.

> Ready to build your own AI-powered content engine? Start with folders, files, and clarity.

---

## 📚 References & Footnotes

[^1]: The directory structure reflects the content generation pipeline and agent orchestration system.

[^2]: Airtable acts as the central coordination point — inputs, outputs, and metadata all live there.

[^3]: Each agent is designed as a markdown-configured, prompt-template-based autonomous unit.

[^4]: MongoDB provides behavioral data; LLMs (Claude, ChatGPT) perform generation; web app reviews.

[^5]: Clear modular design allows easy addition of new blogs, agents, or integration services.

```
```

