# Building Cuculi AI Marketing: What It Takes to Build a Content Engine

> "This blog educates the CEO on all the different pieces and parts that need to happen in order to build this content engine. It communicates that this takes work, it takes time, and sets expectations for when the team can expect the first blog article in Google Drive."

Building an AI-powered content generation system isn't a simple task. It requires careful planning, systematic execution, and clear understanding of what needs to be built. This document serves to educate the CEO and team on what it takes to build **Cuculi AI Marketing**—a content engine that generates strategic, brand-aligned blog posts.

The purpose is clear: **Understand the scope, set realistic expectations, and know when the first blog article will appear in Google Drive.**

## The MVP Approach: Launch Quickly, Systemize Later

We can launch an MVP and get to the first blog article quickly. Here's how:

**The MVP limits scope to focus on what matters most:**
- ❌ **No MongoDB integration initially** - Can be added later to enrich content with event data
- ❌ **No Airtable integration initially** - Can be added later to automate workflow
- ❌ **No LLM fleet integration initially** - Can be added later to systemize content generation

**Instead, the MVP uses a manual workflow:**
- ✅ **Manual document flow**: Brief → Outline → Research → Written Content
- ✅ **Specific instructions for each document**: Every document needs clear instructions on how to generate it following best practices
- ✅ **Templates and guidelines**: Each step has templates and best practices to ensure quality

This manual approach allows us to:
1. **Get to the first blog article faster** - No time spent on integration setup
2. **Validate the workflow** - Ensure the document flow works before automating
3. **Refine the process** - Learn what works before building integrations
4. **Systemize later** - Add integrations once the manual workflow is proven

The key is that **every document in the workflow needs specific instructions and best practices**. We can't just "write a blog post." We need:
- A template for the brief
- Best practices for creating outlines
- Guidelines for research gathering
- Instructions for writing and editing

Once we have these, we can execute the manual workflow. Then, we can systemize it with integrations.

## Three Parts of the System

Building the content engine requires three main components: **Integration**, **Agents**, and **Workflow**. Each part has specific requirements and deliverables.

### Part 1: Integration

Integration connects the content engine to external services and data sources. This enables automation, data enrichment, and streamlined workflows.

#### Airtable Integration

**Purpose**: Airtable serves multiple critical functions:
- **Pull latest ideas**: Content ideas are entered in Airtable and pulled for content generation
- **Web database**: Airtable serves as the web database where content can be rendered from
- **Copy source**: Content can be copied from Airtable for use in other systems
- **Google Docs creation**: Airtable is used to create documents within Google Drive (this is a key requirement)

**What's needed**:
- Airtable API credentials and setup
- Base and table configuration
- Field mapping for content artifacts (brief, research, outline, draft, final)
- Integration script to pull ideas and push generated content
- Google Docs creation workflow from Airtable

**Timeline impact**: Airtable integration is essential for the final step (creating Google Docs), but can be deferred in MVP if manual upload is acceptable.

#### MongoDB Integration

**Purpose**: Enrich content with real platform data:
- **Pull recent events**: Query events from the past 7-30 days for blog plugs
- **Pull upcoming events**: Query events in the next 7-30 days for content references
- **Event details**: Venue, cuisine, attendee count, host information

**What's needed**:
- MongoDB connection credentials and setup
- Database and collection configuration
- Query scripts for recent/upcoming events
- Integration with Research Agent to pull event data

**Timeline impact**: MongoDB integration enriches content but isn't required for MVP. Can be added later to enhance content quality.

#### LLM Integration (Claude and OpenAI)

**Purpose**: Enable agents to tap into LLM services for content generation:
- **Claude**: Primary LLM for structured, brand-aligned writing (Writer and Editor agents)
- **OpenAI/ChatGPT**: Alternative LLM for research and information gathering (Researcher agent)
- **Multi-LLM support**: Different agents can use different LLM services based on task requirements

**What's needed**:
- Claude API credentials and setup
- OpenAI API credentials and setup
- LLM integration wrappers for API calls
- Rate limiting and error handling
- Agent-to-LLM mapping configuration

**Timeline impact**: LLM integration is essential for automated content generation, but MVP can use manual LLM interaction (copy-paste prompts) before systemizing.

### Part 2: Agents

Agents are the intelligence layer of the content engine. Each agent has a specific role, defined prompts, and clear responsibilities.

#### Agent Roles

The content generation process uses five key agents:

1. **Planner Agent**: Creates content plan and strategy based on brief
2. **Researcher Agent**: Gathers research and supporting data
3. **Outliner Agent**: Creates content structure and outline
4. **Writer Agent**: Generates first draft of content
5. **Editor Agent**: Refines and improves content

#### Agent Prompts

**Critical requirement**: Each agent needs well-defined prompts that:
- Clearly specify the agent's role and responsibilities
- Define input requirements (what the agent receives)
- Define output requirements (what the agent produces)
- Include examples and best practices
- Ensure brand voice and quality standards

**Research needed**: How to construct `agents.md` files with Cursor so that the process works effectively. The agent files need to be structured in a way that Cursor can understand and execute.

#### Agent Orchestration

**How agents work together**:
- Agents operate in sequence: Planner → Researcher → Outliner → Writer → Editor
- Each agent receives output from previous agents
- Agents reference templates and guidelines
- Orchestration script coordinates agent execution

**What's needed**:
- Agent instruction files (`agents/*.md`) with prompts and guidelines
- Orchestration logic to sequence agents
- Error handling between agents
- Quality gates between agent stages

**Timeline impact**: Agent definition and prompt creation is essential work that must be done. In MVP, agents can be executed manually (following instructions) before automation.

### Part 3: Workflow

The workflow defines the step-by-step process from content idea to published blog in Google Drive.

#### Step 1: Pull Content Idea from Airtable

Content idea is entered in Airtable with:
- Title
- Brief description
- Target audience
- Funnel stage
- Keywords

**MVP**: Manual - Copy idea from Airtable or enter directly into workflow
**Systemized**: Automated - Script pulls new ideas from Airtable

#### Step 2: Create Brief Document

**Requirement**: Need a template for the brief document

The brief should include:
- Content goals and objectives
- Target audience and funnel stage
- Key messaging points
- Strategic requirements

**What's needed**:
- Brief template (`templates/brief.md`)
- Best practices for brief creation
- Instructions on how to generate a brief from Airtable idea

#### Step 3: Create Outline

**Requirement**: Need best practices for outline creation

The outline should include:
- Logical content structure
- Key points and supporting details
- Strategic alignment with brief

**What's needed**:
- Outline template (`templates/outline.md`)
- Best practices for outline creation
- Instructions on how to create an outline from brief

#### Step 4: Research Phase

**Researcher Agent** finds surprising, interesting research to support claims made in the blog.

Research should include:
- Supporting data and statistics
- Relevant examples and case studies
- External sources and citations
- Platform data (when MongoDB is integrated)

**What's needed**:
- Research template (`templates/research.md`)
- Research guidelines and best practices
- Instructions for Research Agent (or manual research process)

#### Step 5: Writing Phase

**Writer Agent** synthesizes the outline with research to create the first draft.

Writing should:
- Follow the outline structure
- Incorporate research findings
- Maintain brand voice
- Apply strategic messaging

**What's needed**:
- Draft template (`templates/draft.md`)
- Writing guidelines and brand voice
- Instructions for Writer Agent (or manual writing process)

#### Step 6: Editing Phase

**Editor Agent** reviews the work for:
- Clarity and readability
- Brand voice compliance
- Strategic alignment
- Quality and engagement

**What's needed**:
- Editing guidelines and checklist
- Instructions for Editor Agent (or manual editing process)

#### Step 7: Final Upload to Airtable

Once the blog is written, upload to Airtable along with all documents:
- Brief
- Research
- Outline
- Draft
- Final blog post

**What's needed**:
- Airtable integration to push all documents
- Field mapping for each document type
- Status update workflow

#### Step 8: Airtable Creates Google Doc

**Final step**: Airtable creates the Google Doc from the uploaded content.

**What's needed**:
- Airtable automation to create Google Doc
- Google Drive integration
- Document formatting and structure

## Timeline and Expectations

**When can the CEO and team expect the first blog article in Google Drive?**

### MVP Timeline (Manual Workflow)

**Week 1-2: Foundation**
- Create templates for brief, outline, research, draft
- Define best practices for each document type
- Create agent instruction files with prompts
- Set up manual workflow process

**Week 2-3: First Blog Article**
- Execute manual workflow for first blog:
  - Create brief from idea
  - Create outline following best practices
  - Conduct research manually
  - Write first draft
  - Edit and refine
- Upload all documents to Airtable manually
- Create Google Doc from Airtable

**Expected delivery**: **Week 3** - First blog article in Google Drive

### Systemized Timeline (With Integrations)

**Week 3-4: Integration Setup**
- Set up Airtable API integration
- Set up MongoDB integration (if needed)
- Set up LLM integrations (Claude, OpenAI)
- Test integrations

**Week 4-5: Agent Automation**
- Implement agent orchestration
- Test automated workflow
- Refine prompts and instructions

**Week 5-6: Full System**
- End-to-end automated workflow
- Airtable → Agents → Files → Airtable → Google Doc
- First automated blog article

**Expected delivery**: **Week 6** - Fully automated system producing blog articles

## The Work Required

**This takes work. This takes time.**

Building a content engine isn't a quick task. It requires:

1. **Template Creation**: Every document type needs a template and best practices
2. **Agent Definition**: Each agent needs well-defined prompts and instructions
3. **Integration Setup**: Each integration requires credentials, configuration, and testing
4. **Workflow Design**: The step-by-step process must be clearly defined
5. **Quality Assurance**: Each step needs validation and quality checks
6. **Iteration**: The system will need refinement based on real output

**The MVP approach allows us to:**
- Get to the first blog article faster (Week 3)
- Validate the workflow before investing in integrations
- Learn what works and what doesn't
- Systemize once the manual process is proven

**The systemized approach enables:**
- Automated content generation
- Scalable workflow
- Consistent quality
- Reduced manual effort

Both approaches are valid. The MVP gets us to results faster. The systemized approach enables scale.

## The Commitment

**MVP Commitment**: Deliver first blog article in Google Drive by Week 3 using manual workflow.

**Systemized Commitment**: Deliver fully automated content engine by Week 6 with all integrations and agent automation.

**Quality Commitment**: Every blog article meets brand voice, strategic alignment, and quality standards—whether manual or automated.

## Related

- [[Growth-Strategy]] - Strategic foundation for all content generation
- [[Technical-Specification]] - Engineering-readable requirements
- [[System-Architecture]] - Technical implementation details
- [[Agent-Framework]] - Multi-agent system design
- [[Templates-Guide]] - Operational templates and examples

---
title: Building Cuculi AI Marketing: What It Takes to Build a Content Engine
date: 2026-01-19
tags: [#blog, #ai-content-engine, #content-marketing, #ceo-education, #mvp]
type: analysis
status: complete
aliases: ["Cuculi AI Marketing Blog", "Content Engine Education"]
related: ["[[Growth-Strategy]]", "[[Technical-Specification]]", "[[System-Architecture]]", "[[Agent-Framework]]", "[[Templates-Guide]]"]
---
