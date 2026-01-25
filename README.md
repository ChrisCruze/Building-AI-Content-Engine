# Building AI Content Engine

## Overview
A comprehensive system for generating engaging, strategic content at scale using multi-agent AI orchestration. The system creates well-crafted blog articles, social media posts, and newsletters that drive user engagement and sign-ups for Cuculi, a social dining platform.

**Project Purpose**: Create a content marketing plan using AI by leveraging best practices and developing a process to build content and generate content on social media or other platforms. Build an engaging, interesting funnel based on current events and other best practices, such as whether that's a blog or any other content generation practices, and identifying what would be a good use case for a social dining platform that strives to improve the marketing and have a greater impact on getting people to sign up for the platform.

## Core Idea and Outcomes
Build an AI-powered content engine that leverages best practices and multi-agent orchestration to produce high-quality, brand-aligned content across multiple channels. The system transforms content creation from manual writing into a scalable, automated process that responds to current events, user needs, and platform data.

By the end, users will be able to:
- Generate blog articles, social media posts, and newsletters at scale
- Maintain brand consistency and voice across all content types
- Respond to signals and trends automatically
- Produce content that drives measurable growth (sign-ups, engagement, platform usage)
- Operate with minimal human intervention while maintaining quality standards

**Success Definition**: A successful outcome is one where we have a well-defined plan and a system in place to execute. Success means building an engine that can craft well-crafted blog articles and content that can be put on different social media platforms, and could even create a newsletter that can be sent out on a regular basis.

## Audience and Voice
- **Audience**: Content team, growth marketers, product managers, engineering teams working on content generation systems
- **Voice**: Strategic, technical, practical, and structured—balancing high-level vision with actionable implementation details
- **Constraints**: Focus on scalable systems over one-off content; emphasize automation and quality gates; maintain brand alignment as non-negotiable

## Repository Map
- `README.md`: Overview, workflow, status, and navigation guide
- `Outline.md`: Structure of documents and sections with numbered list format
- `Facts.md`: Canonical names, terms, constraints, and project facts
- `Documents/`: One markdown file per main document (Growth Strategy, Technical Specification, System Architecture, Agent Framework, Templates Guide)
- `Report.md`: Project metrics, time logs, and artifacts
- `Blog.md`: Narrative blog post about the project journey

## Workflow (For Me and Agents)
1. If any canonical detail changed, update `Facts.md` first.
2. Update or refine the relevant document/section in `Outline.md`.
3. Draft or revise the corresponding document in `Documents/`.
4. Run an editing pass; then commit changes.

> When using an LLM: always load this README plus `Outline.md`, `Facts.md`, and the specific document file.

## Status
- [x] Document: Growth Strategy – Strategic foundation for all content generation
- [x] Document: Technical Specification – Engineering-readable requirements
- [x] Document: System Architecture – Technical implementation details
- [x] Document: Agent Framework – Multi-agent system design
- [x] Document: Templates Guide – Operational templates and examples
- [ ] System: Implementation – Build and deploy content engine
- [ ] System: Testing & Refinement – Validate content quality and system performance

## Current Focus
Working on: Repository structure and documentation – Outline.md, Facts.md, README.md, and Blog.md creation.

## Key Documents

The AI Content System Documentation Suite consists of five critical documents:

1. **[[Growth-Strategy]]** - Defines why content exists, who it's for, and how it drives measurable growth
2. **[[Technical-Specification]]** - Translates strategy into testable, engineering-readable requirements
3. **[[System-Architecture]]** - Explains how the system is built and how data flows
4. **[[Agent-Framework]]** - Defines the intelligence layer: which agents exist and how they collaborate
5. **[[Templates-Guide]]** - Provides reusable formats and concrete examples for operationalization

All documents are located in `Documents/[Document-Name]/[Document-Name].md` and are cross-referenced using `[[Document-Name]]` notation.

## Success Criteria

The project will be considered successful when:

1. **Well-Defined Plan**: Complete strategic framework for AI-powered content creation
2. **System in Place**: Operational content generation system ready for execution
3. **Key Documents Complete**: All five core documents finalized
4. **Content Quality**: System produces well-crafted, engaging content suitable for multiple platforms
5. **Automation Ready**: Process can generate content on a regular basis without constant manual intervention

## Stakeholders

- **Platform Users**: Target audience for content
- **CEO**: Strategic alignment and positioning
- **Content Team**: Execution and content creation
- **Growth Marketer/Head of Marketing**: Strategy and audience insights (Accountable Owner for Growth Strategy)
- **Product Manager**: User insight and platform positioning
- **Engineering Team**: Technical implementation and system architecture

## Resources

- **LLM Tools**: ChatGPT, OpenAI, Claude
- **Automation**: N8n for workflow orchestration
- **Research**: Best practices in content marketing, social media strategies, content funnels
- **Platform Knowledge**: Understanding of social dining platform user motivations and behaviors

**Key Actions**: More research is needed in order to understand what are the best practices that need to be done.

## Agent Architecture: Building AI Content Engine

### Multi-Agent AI Blogging System

The system uses a multi-agent AI blogging approach with role-specific prompts and sequential execution to generate provocative, credible content, enhanced by real events and user data from MongoDB.

**Core Principle**: A multi-agent system uses role-specific prompts and sequential execution to generate provocative, credible content. Each agent has a specialized role—research, outline, drafting, and titles—configured with custom prompts and executed in a sequential workflow. This creates a fast, disciplined blog workflow that maintains quality and supporting evidence.

### Provocative Story Agent

The Provocative Story Agent turns data into stories. Within the system, the agent acts as a provocateur and interpreter, grounding every story in real data while shaping it into a human narrative that audiences can recognize themselves in, making authenticity scalable rather than fragile.

**Composite Stories Approach**: Representative stories can truthfully capture real user behavior without costly, slow individual interviews. This approach allows the system to create emotionally resonant content that feels authentic while being scalable.

### Provocative Fiction Engine

The Provocative Fiction Engine is a story agent that bends facts to reveal emotional truth. This agent invents plausible stories to surface familiar emotional and social patterns people recognize but rarely articulate.

**Core Function**: This agent operates as a parable-maker, inventing emotionally true but fictional stories that compress common behaviors into provocative moments designed to trigger recognition, debate, and lasting reflection without targeting real individuals. The agent deliberately fabricates plausible, fictional narratives—parables rather than case studies—using real behavioral and social patterns to escalate from mundane situations to uncomfortable truths, provoking emotional response, reflection, and conversation while remaining memorable, brand-safe, and unconcerned with being liked.

#### Five-Step Arc for Provocative Fiction

This five-part structure works because it mirrors real psychological experience:

1. **Setup (Ordinary World)**: A mundane, relatable situation that creates identification
2. **Rising Tension**: Small choices, rationalizations, and social pressures that gradually corner the main character—builds complicity
3. **Provocative Turn**: A single, uncomfortable moment that reveals the hidden pattern or hypocrisy—forces recognition
4. **Aftermath**: Brief, lingering consequences that make the reader ask, "What would I have done?"—lingers emotionally
5. **Pattern Naming**: 2–3 bullet points that name the underlying pattern in neutral language without judgment—gives readers language for something they already felt but never articulated

The five-part structure starts with a mundane, relatable situation, escalates through small rationalized choices, crystallizes the tension in a single uncomfortable moment, shows subtle aftermath consequences, and finally names the emotional pattern without judgment.

#### Internal Planning Engine

A structured internal process translates abstract emotional patterns into coherent, provocative fictional stories. Internal planning guides the agent from intent to execution by:

1. Restating the emotional pattern in the agent's own words
2. Brainstorming 3–5 possible mundane setups and choosing the one with clearest, most relatable tension
3. Sketching a 4-beat outline following the structure: setup, rising tension, provocative turn, aftermath
4. Writing the story in scenes with concrete details and dialogue
5. Re-reading the output to ensure it contains no real individuals or scandals, clearly signals it is fictional, surfaces the requested pattern, and avoids explicit, graphic, or instructional harm
6. Outputting the final story only, plus optional "Patterns surfaced" bullets

This planning scaffold helps keep the stories coherent and on-brand as provocative but safe fiction.

**Agent Implementation**: See [[Provocateur-Agent]] in `Cuculi-AI-Marketing/agents/provocateur.md` for full implementation details.

## Strategic Content Framework

The system leverages high-impact strategic agents to drive strategy, data integrity, and viral engagement:

### High-Impact Strategic Agents

- **Strategist**: Content planning and strategy expert that analyzes briefs, target audiences, and funnel stages
- **Signal Hunter**: Conducts credibility-focused research, gathering data, insights, and supporting evidence from MongoDB, external research, and platform analytics
- **Provocateur**: Creates emotionally intense, provocative content that drives virality while maintaining brand credibility
- **Event Hunter**: Monitors MongoDB for upcoming events, user activity, and social dining data to identify blog opportunities
- **Sticky Marketer**: Applies the Made-to-Stick SUCCESs framework (Simple, Unexpected, Credible, Concrete, Emotional, Stories) to ensure content is memorable and shareable

**Workflow Pattern**: By isolating high-impact agents, we see a clear workflow from strategic data gathering (Signal Hunter) to psychological engagement (Sticky Marketer).

### Agent Selection Workflows

The system supports multiple workflow patterns:

- **Viral Seasonal Content**: Seasonal Strategist → Provocateur → Sticky Marketer → Wordsmith
- **Event-Driven Blog**: Event Hunter → Signal Hunter → Storyteller → Wordsmith
- **High-Engagement Think Piece**: Provocateur → Empathy Engine → Sticky Marketer → Wordsmith → Refiner
- **Data-Backed Article**: Signal Hunter → Data Weaver → Architect → Wordsmith
- **Quick, Sticky Post**: Sticky Marketer → Headline Master → Wordsmith
- **Emotional Story**: Storyteller → Empathy Engine → Wordsmith → Refiner
- **Standard Quality Blog**: Strategist → Signal Hunter → Architect → Wordsmith → Refiner → Judge

**Full Documentation**: See `Artifacts/Strategize-Cuculi-Content-Growth/Strategize-Cuculi-Content-Growth.md` for comprehensive agent framework details.

## Change Log
- 2026-01-26: Integrated Project directory content, Strategize-Cuculi-Content-Growth artifacts, and added Provocative Fiction Engine agent documentation
- 2026-01-19: Created Outline.md, Facts.md, restructured README.md, and wrote Blog.md
- 2026-01-18: Completed all five core documents (Growth Strategy, Technical Specification, System Architecture, Agent Framework, Templates Guide)
- 2026-01-10: Initial project structure and documentation framework defined

## Repository

GitHub: https://github.com/ChrisCruze/Building-AI-Content-Engine

---
title: Building AI Content Engine
date: 2026-01-19
tags: [#project, #ai-content-engine, #readme]
type: guide
status: complete
aliases: ["AI-Content-Engine-README"]
related: ["[[Outline]]", "[[Facts]]", "[[Growth-Strategy]]", "[[Technical-Specification]]", "[[System-Architecture]]", "[[Agent-Framework]]", "[[Templates-Guide]]", "[[Provocateur-Agent]]"]
---
