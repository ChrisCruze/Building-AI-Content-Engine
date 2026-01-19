# Building Cuculi-AI-Marketing: A Production Repository for AI Content Generation

> "The repository structure is the system. Every folder, every file, every integration point serves a specific purpose in the content generation workflow."

We've designed a comprehensive content strategy and agent framework. Now we're building **Cuculi-AI-Marketing**—the production repository where strategy becomes executable code, where agents generate real content, and where Airtable, MongoDB, and LLM services converge into a working system.

This isn't just documentation. This is the actual repository structure, workflow, and implementation plan for generating content that drives sign-ups and engagement for a social dining platform.

## The Repository as Production System

**Cuculi-AI-Marketing** is the production repository where:
- Content ideas from Airtable become fully-researched, outlined, and written blog posts
- Multi-agent AI systems orchestrate research, outlining, writing, editing, and quality checks
- MongoDB event data enriches content with real platform insights
- LLM services (ChatGPT, Claude) generate content following brand voice and strategic guidelines
- A web app renders all blogs from Airtable for review and management

The repository structure itself defines the workflow. Each folder has a purpose. Each file has a role. The directory organization is the system architecture.

## Repository Structure

```
Cuculi-AI-Marketing/
├── docs/
│   └── writing-principles.md          # Core writing guidelines and brand voice
├── agents/
│   ├── planner.md                     # Content planning and strategy agent
│   ├── researcher.md                  # Research gathering and signal processing agent
│   ├── outliner.md                    # Content structure and outline generation agent
│   ├── writer.md                      # First draft generation agent
│   ├── editor.md                      # Content refinement and improvement agent
│   └── critic.md                      # Quality evaluation and scoring agent
├── templates/
│   ├── research.md                    # Research document template
│   ├── outline.md                     # Content outline template
│   ├── draft.md                       # First draft template
│   └── final.md                       # Final published content template
├── blogs/
│   ├── downloaded-social-dining-app-didnt-go/
│   │   ├── brief.md                   # Content brief from Airtable
│   │   ├── research.md                # Research document with signals and data
│   │   ├── outline.md                 # Content structure and key points
│   │   └── blog.md                    # Final blog post
│   └── dinner-with-7-strangers-wasnt-awkward/
│       ├── brief.md
│       ├── research.md
│       ├── outline.md
│       └── blog.md
├── integrations/
│   ├── airtable_integration.py        # Airtable API sync (pull ideas, push content)
│   ├── claude_integration.py          # Anthropic Claude API wrapper
│   └── mongodb_integration.py         # MongoDB event data queries
├── index.html                         # Web app for managing blogs (renders from Airtable API)
├── run.py                             # Main orchestration script
└── README.md                          # Repository overview and setup
```

### Directory Purposes

**`docs/`** - Strategic foundation documents that guide all content generation. Contains writing principles, brand voice guidelines, and content strategy that agents reference.

**`agents/`** - Agent instruction files. Each markdown file defines an agent's role, prompt templates, input/output specifications, and operational constraints. These files are loaded by the orchestration system to configure agent behavior.

**`templates/`** - Reusable templates for each content artifact type. Templates ensure consistency across all generated content and provide structure for agent outputs.

**`blogs/`** - Generated content organized by blog post. Each blog gets its own folder containing the complete workflow artifacts: brief (from Airtable), research (from MongoDB + external sources), outline (from Outliner agent), and final blog (from Writer + Editor agents).

**`integrations/`** - Python modules for external service integration. Handles API connections, data queries, and bidirectional sync with Airtable.

**`index.html`** - Single-page web application that renders all blogs from Airtable API. Provides content management interface for reviewing, editing, and publishing generated content.

**`run.py`** - Main execution script that orchestrates the complete workflow: monitors Airtable for new content requests, triggers agent pipeline, generates artifacts, and syncs results back to Airtable.

## The Complete Workflow: From Idea to Published Blog

The workflow is Airtable-centric. Content ideas start in Airtable, flow through the agent system, generate files in the repository, and sync back to Airtable for review and publishing.

### Step 1: Idea Capture in Airtable

A content idea is entered in the Airtable "content" table with fields:
- **Title**: Blog post title
- **Brief**: Content brief and requirements
- **Status**: Workflow status (idea → research → outline → draft → review → published)
- **Target Audience**: Never-Engaged Veterans, One-Time Experimenters, etc.
- **Funnel Stage**: Awareness, Activation, Retention, etc.
- **Keywords**: SEO and topic keywords
- **MongoDB Event IDs**: Related events to reference

**Example 1**: "I Downloaded a Social Dining App and Didn't Go for 6 Months — Here's What Finally Got Me Out the Door"
- **Status**: idea
- **Target Audience**: Never-Engaged Veterans (42.8% of users)
- **Funnel Stage**: Activation
- **Brief**: Address hesitation and decision paralysis. Use empathy → identification → curiosity psychology.

**Example 2**: "I Went to a Dinner With 7 Strangers — and It Wasn't Awkward (Here's Why)"
- **Status**: idea
- **Target Audience**: Never-engaged and one-timers
- **Funnel Stage**: Activation / Retention
- **Brief**: Confront awkwardness fear directly. Use fear disconfirmation + curiosity gap psychology.

### Step 2: Trigger Content Generation

`run.py` monitors Airtable for records with status "idea" or "ready". When found, it:
1. Pulls the brief and metadata from Airtable
2. Creates a new blog folder: `blogs/{blog-slug}/`
3. Saves the brief as `brief.md`
4. Triggers the agent pipeline

### Step 3: Research Agent

The **Researcher Agent** (`agents/researcher.md`) gathers context:
- **MongoDB Integration**: Queries upcoming/recent events, user segments, platform data
- **External Sources**: Current events, trends, competitor content
- **Signal Processing**: Identifies content opportunities and relevant data points

**For Blog 1** ("Downloaded App, Didn't Go"):
- MongoDB query: Never-Engaged Veterans segment data (3,961 users, 400+ days since signup)
- Research signals: Decision paralysis patterns, first-event barriers, activation triggers
- Output: `blogs/downloaded-social-dining-app-didnt-go/research.md`

**For Blog 2** ("Dinner With 7 Strangers"):
- MongoDB query: Recent event data, attendee feedback, awkwardness concerns
- Research signals: Social anxiety patterns, successful event dynamics, community building
- Output: `blogs/dinner-with-7-strangers-wasnt-awkward/research.md`

### Step 4: Outline Agent

The **Outliner Agent** (`agents/outliner.md`) structures the content:
- Reads `brief.md` and `research.md`
- Creates logical flow and key points
- Uses template from `templates/outline.md`
- Outputs: `blogs/{blog-slug}/outline.md`

**For Blog 1**: Outline focuses on hesitation → barriers → breakthrough moment → practical steps
**For Blog 2**: Outline focuses on fear → expectation → reality → why it worked

### Step 5: Writer Agent

The **Writer Agent** (`agents/writer.md`) generates first draft:
- Reads `brief.md`, `research.md`, `outline.md`
- References `docs/writing-principles.md` for brand voice
- Uses LLM service (Claude via `integrations/claude_integration.py`)
- Outputs: `blogs/{blog-slug}/blog.md` (draft version)

### Step 6: Editor Agent

The **Editor Agent** (`agents/editor.md`) refines content:
- Reads draft `blog.md`
- Improves clarity, engagement, brand alignment
- Ensures psychological triggers are effective
- Outputs: Updated `blog.md`

### Step 7: Critic Agent

The **Critic Agent** (`agents/critic.md`) evaluates quality:
- Scores content against criteria (relevance, engagement, brand alignment, technical quality)
- Flags issues requiring human review
- Updates status in Airtable based on score

### Step 8: Sync to Airtable

`integrations/airtable_integration.py` pushes generated content back to Airtable:
- **Research** field: Content from `research.md`
- **Outline** field: Content from `outline.md`
- **Draft** field: Content from `blog.md` (draft)
- **Status**: Updated to "review" or "published" based on quality score

### Step 9: Web App Review

`index.html` renders all blogs from Airtable API:
- Fetches all content records from Airtable
- Displays blogs in a management interface
- Allows review, editing, and status updates
- Provides search and filtering by status, audience, funnel stage

## Integration Architecture

### Airtable Integration

**Purpose**: Central content management system. All content ideas, generated artifacts, and status tracking live in Airtable.

**Workflow**:
- **Pull**: `airtable_integration.py` reads new content requests, briefs, and metadata
- **Push**: Generated research, outlines, drafts, and final content sync back to Airtable fields
- **Bidirectional**: Status updates flow both ways (Airtable → repo → Airtable)

**Content Table Schema**:
- Core: Title, Content (final), Status, Created Date, Published Date
- Artifacts: Brief, Research, Outline, Facts, Draft
- Metadata: Keywords, Target Audience, LLM Service Used, MongoDB Event IDs
- Workflow: Status field tracks progress (idea → research → outline → draft → review → published)

### MongoDB Integration

**Purpose**: Enrich content with real platform data—upcoming events, recent events, user segments, engagement metrics.

**Queries**:
- **Upcoming Events**: Events in next 7-30 days (venue, cuisine, attendee count, host info)
- **Recent Events**: Events in past 7-30 days (outcomes, feedback, engagement data)
- **User Segments**: Never-Engaged Veterans, One-Time Experimenters, etc. (demographics, behavior patterns)

**Integration Points**:
- Research Agent pulls event data for context
- Content references specific events with IDs stored in Airtable
- Event data informs content personalization and relevance

### LLM Service Integration

**Purpose**: Multi-LLM support for different agent tasks. Primary: Claude for structured writing. Fallback: ChatGPT for research.

**Service Selection**:
- **Research Agent**: ChatGPT (better at research and information gathering)
- **Writer Agent**: Claude (better at structured, brand-aligned writing)
- **Editor Agent**: Claude (better at refinement and improvement)

**Configuration**: `integrations/claude_integration.py` and `integrations/chatgpt_integration.py` handle API calls, rate limiting, and error handling with automatic fallback.

## Web App: index.html

**Purpose**: Content management interface that renders all blogs from Airtable API.

**Features**:
- **Blog List**: Displays all content records from Airtable
- **Filtering**: By status, target audience, funnel stage, date
- **Search**: Full-text search across titles and content
- **Preview**: View generated research, outline, and draft for each blog
- **Status Management**: Update workflow status directly from web app
- **Airtable Sync**: Real-time rendering from Airtable API (no local file dependency)

**Architecture**: Single-page application using Airtable API. No backend required—direct API calls from browser.

## Scope Definition

### In Scope

✅ **Content Generation Workflow**: Complete Airtable → agents → files → Airtable pipeline
✅ **Agent Management**: Agent instruction files, prompt templates, orchestration logic
✅ **Key Document Management**: Research, outline, brief, facts per blog in repository structure
✅ **Airtable Integration**: Bidirectional sync (pull ideas, push content, status updates)
✅ **MongoDB Integration**: Event data queries for content enrichment
✅ **Multi-LLM Support**: OpenAI (ChatGPT) and Anthropic (Claude) integration
✅ **Web App**: index.html for content management and blog rendering
✅ **Repository Structure**: Organized folders and files with clear purposes

### Out of Scope

❌ **Publishing to External Platforms**: Publishing to Wix, social media, email platforms (handled separately)
❌ **Advanced Analytics Dashboard**: Content performance analytics and reporting (future phase)
❌ **Real-Time Content Updates**: Batch processing only, no real-time streaming
❌ **Multi-User Collaboration**: Single-user workflow, no collaboration features
❌ **Content Versioning System**: Basic file-based versioning only (Git), no advanced versioning
❌ **Automated SEO Optimization**: Manual SEO review required, no automated optimization
❌ **Image Generation**: Focus on text content only, images handled separately

## Implementation Roadmap

### Phase 1: Repository Foundation (Week 1-2)

**Deliverables**:
- Create complete directory structure (`docs/`, `agents/`, `templates/`, `blogs/`, `integrations/`)
- Create all agent instruction files with research instructions
- Create all template files with research instructions
- Create two example blog folders with placeholder files
- Create integration Python files with research instructions
- Create `run.py` orchestration script skeleton
- Create `index.html` web app skeleton
- Update `README.md` with repository overview

**Success Criteria**: All folders and files exist with purpose descriptions and research instructions.

### Phase 2: Core Integrations (Week 2-3)

**Deliverables**:
- MongoDB connection and event query scripts (`mongodb_integration.py`)
- Airtable API integration (read/write) (`airtable_integration.py`)
- LLM service wrappers (Claude, ChatGPT) (`claude_integration.py`, `chatgpt_integration.py`)
- Configuration management (YAML configs for API keys, connection strings)

**Success Criteria**: Can pull data from MongoDB, read/write to Airtable, and call LLM APIs.

### Phase 3: Agent System (Week 3-4)

**Deliverables**:
- Implement agent structure (load instructions from `agents/*.md` files)
- Create agent prompt templates and orchestration logic
- Build agent pipeline (Planner → Researcher → Outliner → Writer → Editor → Critic)
- Test agent workflows end-to-end with sample content

**Success Criteria**: Complete agent pipeline generates research, outline, and draft for test blog.

### Phase 4: Content Generation Workflow (Week 4-5)

**Deliverables**:
- Build main generation script (`run.py`) with Airtable monitoring
- Implement artifact creation (research.md, outline.md, blog.md)
- Create sync script for Airtable bidirectional sync
- Test complete workflow with two example blogs

**Success Criteria**: Can generate complete blog posts from Airtable ideas and sync results back.

### Phase 5: Web App (Week 5-6)

**Deliverables**:
- Build `index.html` with Airtable API integration
- Create blog rendering and management interface
- Add filtering, search, and status management
- Test web app with generated content

**Success Criteria**: Web app displays all blogs from Airtable with full functionality.

### Phase 6: Testing & Refinement (Week 6-7)

**Deliverables**:
- End-to-end testing with real content (two example blogs)
- Refine agent prompts based on output quality
- Optimize sync performance and error handling
- Document workflows and usage in README

**Success Criteria**: System generates high-quality content that meets brand voice and strategic requirements.

## The Two Blog Examples in Context

### Blog 1: "I Downloaded a Social Dining App and Didn't Go for 6 Months — Here's What Finally Got Me Out the Door"

**Workflow Journey**:
1. **Airtable**: Idea captured with brief targeting Never-Engaged Veterans, Activation stage
2. **Research Agent**: Queries MongoDB for Never-Engaged Veterans data (3,961 users, 400+ days since signup), identifies decision paralysis patterns
3. **Outline Agent**: Structures content: hesitation → barriers → breakthrough moment → practical steps
4. **Writer Agent**: Generates draft using empathy → identification → curiosity psychology
5. **Editor Agent**: Refines for brand voice and engagement
6. **Critic Agent**: Scores for relevance to target audience and activation potential
7. **Airtable Sync**: Research, outline, and draft pushed to Airtable fields
8. **Web App**: Blog appears in `index.html` for review and publishing

**Why This Works**: Mirrors exact behavior of largest segment. Lowers defenses by admitting hesitation first, builds trust. Curiosity from "what finally got me out the door" promises practical resolution.

### Blog 2: "I Went to a Dinner With 7 Strangers — and It Wasn't Awkward (Here's Why)"

**Workflow Journey**:
1. **Airtable**: Idea captured with brief targeting Never-engaged and one-timers, Activation/Retention stage
2. **Research Agent**: Queries MongoDB for recent event data, attendee feedback, awkwardness concerns
3. **Outline Agent**: Structures content: fear → expectation → reality → why it worked
4. **Writer Agent**: Generates draft using fear disconfirmation + curiosity gap psychology
5. **Editor Agent**: Refines to challenge expectations and build confidence
6. **Critic Agent**: Scores for fear disconfirmation effectiveness and retention potential
7. **Airtable Sync**: All artifacts pushed to Airtable
8. **Web App**: Available for review in management interface

**Why This Works**: Directly confronts biggest emotional fear: awkwardness. Parenthetical "and it wasn't awkward" challenges expectations, forces "How?"

## The Honest Assessment

**Cuculi-AI-Marketing** is the production repository where strategy becomes code. The directory structure defines the workflow. The agent files define the intelligence. The integrations connect the system to data sources and LLM services.

The repository is designed to be:
- **Executable**: Every file has a purpose, every folder has a role
- **Maintainable**: Clear structure makes it easy to understand and modify
- **Scalable**: Adding new blogs, agents, or integrations follows established patterns
- **Integrated**: Airtable, MongoDB, and LLM services work together seamlessly

The commitment: **Build the repository structure, implement the integrations, test with real content, and iterate based on actual performance.** Not theoretical performance. Real content that drives real results.

## The Invitation

If you're building an AI content system, here's what we've learned:

**Structure is the system.** The repository organization defines the workflow. Every folder, every file, every integration point serves a specific purpose.

**Workflow is Airtable-centric.** Content ideas start in Airtable, flow through agents, generate files, and sync back. Airtable is the single source of truth.

**Agents are files.** Agent instructions live in markdown files. Load them, configure them, execute them. The file structure is the agent system.

**Integrations are modular.** MongoDB for data, Airtable for management, LLM services for generation. Each integration is a separate module with clear responsibilities.

**Web app is simple.** `index.html` renders from Airtable API. No backend required. Direct API calls from browser.

The repository structure is complete. The workflow is defined. The integrations are specified. Now comes the hard part: building it, testing it, and making it work.

Ready to build? Let's execute.

## Related

- [[Growth-Strategy]] - Strategic foundation for all content generation
- [[Technical-Specification]] - Engineering-readable requirements
- [[System-Architecture]] - Technical implementation details
- [[Agent-Framework]] - Multi-agent system design
- [[Templates-Guide]] - Operational templates and examples

---
title: Building Cuculi-AI-Marketing: A Production Repository for AI Content Generation
date: 2026-01-19
tags: [#blog, #ai-content-engine, #content-marketing, #repository-structure, #workflow]
type: analysis
status: complete
aliases: ["Cuculi-AI-Marketing Blog", "Repository Structure Blog"]
related: ["[[Growth-Strategy]]", "[[Technical-Specification]]", "[[System-Architecture]]", "[[Agent-Framework]]", "[[Templates-Guide]]"]
---
