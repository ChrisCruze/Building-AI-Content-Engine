# Outline

## Logline
Building Cuculi AI Marketing is a comprehensive system for generating engaging, strategic content at scale. This outline documents the three main parts required to build the content engine: Integration, Agents, and Workflow.

## Structure

### 1. Integration - Connecting the Content Engine to External Services

Integration connects the content engine to external services and data sources, enabling automation, data enrichment, and streamlined workflows.

#### 1.1 Airtable Integration
- **Purpose**: Pull latest ideas, serve as web database, render from, create Google Docs
- **Requirements**: 
  - Airtable API credentials and setup
  - Base and table configuration
  - Field mapping for content artifacts (brief, research, outline, draft, final)
  - Integration script to pull ideas and push generated content
  - Google Docs creation workflow from Airtable
- **MVP Status**: Can be deferred if manual upload is acceptable
- **Systemized Status**: Essential for automated workflow and Google Docs creation

#### 1.2 MongoDB Integration
- **Purpose**: Pull recent/upcoming events for blog plugs
- **Requirements**:
  - MongoDB connection credentials and setup
  - Database and collection configuration
  - Query scripts for recent events (past 7-30 days)
  - Query scripts for upcoming events (next 7-30 days)
  - Event details: venue, cuisine, attendee count, host information
  - Integration with Research Agent to pull event data
- **MVP Status**: Not required for MVP, enriches content
- **Systemized Status**: Enhances content quality with real platform data

#### 1.3 LLM Integration (Claude and OpenAI)
- **Purpose**: Enable agents to tap into LLM services for content generation
- **Requirements**:
  - Claude API credentials and setup (primary for Writer and Editor agents)
  - OpenAI API credentials and setup (for Researcher agent)
  - LLM integration wrappers for API calls
  - Rate limiting and error handling
  - Agent-to-LLM mapping configuration
  - Multi-LLM support for different agent tasks
- **MVP Status**: Can use manual LLM interaction (copy-paste prompts)
- **Systemized Status**: Essential for automated content generation

### 2. Agents - The Intelligence Layer

Agents are the intelligence layer of the content engine. Each agent has a specific role, defined prompts, and clear responsibilities.

#### 2.1 Agent Roles
- **Planner Agent**: Creates content plan and strategy based on brief
- **Researcher Agent**: Gathers research and supporting data
- **Outliner Agent**: Creates content structure and outline
- **Writer Agent**: Generates first draft of content
- **Editor Agent**: Refines and improves content

#### 2.2 Agent Prompts
- **Critical Requirement**: Each agent needs well-defined prompts
- **Prompt Requirements**:
  - Clearly specify the agent's role and responsibilities
  - Define input requirements (what the agent receives)
  - Define output requirements (what the agent produces)
  - Include examples and best practices
  - Ensure brand voice and quality standards
- **Research Needed**: How to construct `agents.md` files with Cursor so that the process works effectively
- **Agent Files**: Structure agent instruction files in a way that Cursor can understand and execute

#### 2.3 Agent Orchestration
- **How agents work together**:
  - Agents operate in sequence: Planner → Researcher → Outliner → Writer → Editor
  - Each agent receives output from previous agents
  - Agents reference templates and guidelines
  - Orchestration script coordinates agent execution
- **Requirements**:
  - Agent instruction files (`agents/*.md`) with prompts and guidelines
  - Orchestration logic to sequence agents
  - Error handling between agents
  - Quality gates between agent stages
- **MVP Status**: Agents can be executed manually (following instructions)
- **Systemized Status**: Automated agent orchestration with script execution

### 3. Workflow - The Step-by-Step Process

The workflow defines the step-by-step process from content idea to published blog in Google Drive.

#### 3.1 Brief Creation
- **Requirement**: Need a template for the brief document
- **Brief Contents**:
  - Content goals and objectives
  - Target audience and funnel stage
  - Key messaging points
  - Strategic requirements
- **Requirements**:
  - Brief template (`templates/brief.md`)
  - Best practices for brief creation
  - Instructions on how to generate a brief from Airtable idea
- **MVP**: Manual brief creation following template
- **Systemized**: Automated brief generation from Airtable

#### 3.2 Outline Creation
- **Requirement**: Need best practices for outline creation
- **Outline Contents**:
  - Logical content structure
  - Key points and supporting details
  - Strategic alignment with brief
- **Requirements**:
  - Outline template (`templates/outline.md`)
  - Best practices for outline creation
  - Instructions on how to create an outline from brief
- **MVP**: Manual outline creation following best practices
- **Systemized**: Automated outline generation by Outliner Agent

#### 3.3 Research Phase
- **Researcher Agent** finds surprising, interesting research to support claims made in the blog
- **Research Contents**:
  - Supporting data and statistics
  - Relevant examples and case studies
  - External sources and citations
  - Platform data (when MongoDB is integrated)
- **Requirements**:
  - Research template (`templates/research.md`)
  - Research guidelines and best practices
  - Instructions for Research Agent (or manual research process)
- **MVP**: Manual research following guidelines
- **Systemized**: Automated research gathering by Researcher Agent

#### 3.4 Writing Phase
- **Writer Agent** synthesizes the outline with research to create the first draft
- **Writing Requirements**:
  - Follow the outline structure
  - Incorporate research findings
  - Maintain brand voice
  - Apply strategic messaging
- **Requirements**:
  - Draft template (`templates/draft.md`)
  - Writing guidelines and brand voice
  - Instructions for Writer Agent (or manual writing process)
- **MVP**: Manual writing following guidelines
- **Systemized**: Automated draft generation by Writer Agent

#### 3.5 Editing Phase
- **Editor Agent** reviews the work for:
  - Clarity and readability
  - Brand voice compliance
  - Strategic alignment
  - Quality and engagement
- **Requirements**:
  - Editing guidelines and checklist
  - Instructions for Editor Agent (or manual editing process)
- **MVP**: Manual editing following guidelines
- **Systemized**: Automated editing by Editor Agent

#### 3.6 Final Upload to Airtable
- Upload to Airtable along with all documents:
  - Brief
  - Research
  - Outline
  - Draft
  - Final blog post
- **Requirements**:
  - Airtable integration to push all documents
  - Field mapping for each document type
  - Status update workflow
- **MVP**: Manual upload to Airtable
- **Systemized**: Automated upload via Airtable integration

#### 3.7 Airtable Creates Google Doc
- **Final Step**: Airtable creates the Google Doc from the uploaded content
- **Requirements**:
  - Airtable automation to create Google Doc
  - Google Drive integration
  - Document formatting and structure
- **MVP**: Manual Google Doc creation from Airtable
- **Systemized**: Automated Google Doc creation via Airtable automation

## Related Notes
- [[Growth-Strategy]] - Strategic foundation for all content generation
- [[Technical-Specification]] - Engineering-readable requirements
- [[System-Architecture]] - Technical implementation details
- [[Agent-Framework]] - Multi-agent system design
- [[Templates-Guide]] - Operational templates and examples

## References
- [Building AI Content Engine Repository](https://github.com/ChrisCruze/Building-AI-Content-Engine)
- [Cuculi AI Marketing Repository](https://github.com/Cuculi-Inc/Cuculi-AI-Marketing)

---
title: Building Cuculi AI Marketing Outline
date: 2026-01-19
tags: [#project, #ai-content-engine, #outline]
type: guide
status: complete
aliases: ["Cuculi-AI-Marketing-Outline"]
related: ["[[Growth-Strategy]]", "[[Technical-Specification]]", "[[System-Architecture]]", "[[Agent-Framework]]", "[[Templates-Guide]]"]
---
