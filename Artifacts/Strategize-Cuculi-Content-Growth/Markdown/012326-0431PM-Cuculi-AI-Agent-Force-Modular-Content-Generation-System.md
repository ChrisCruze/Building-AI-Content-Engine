# Cuculi AI Agent Force: Modular Content Generation System

## Summary

A multi-agent ecosystem dividing content creation into Core, Strategic, and Specialized roles for flexible, goal-oriented workflows.

## Description

A comprehensive framework slide detailing the functional categorization of AI agents within the Cuculi Content Engine.

## Insight

Breaking content creation into discrete, specialized agent personas allows for mixing psychological triggers (empathy, provocation) with structural rigor.

## Input

# 🚀 Cuculi AI Content Engine - Agent Force

> **A Multi-Agent System for Scalable, Viral Blogging**

Welcome to the Cuculi AI Content Engine's agent force—a diverse team of specialized AI agents, each with unique superpowers, personalities, and strategic roles. This isn't a one-size-fits-all approach. Instead, we've built a flexible, powerful system where you can mix and match agents to create the perfect content generation workflow for any goal.

**Why Multiple Agents?** Because great content requires different skills at different stages. Some agents excel at strategy, others at provocation, and some at making ideas stick. By combining agents strategically, we create content that's not just good—it's viral, memorable, and perfectly aligned with your brand.

---

## 📋 Quick Selection Guide

| Content Goal | Recommended Agent Workflow |
|-------------|---------------------------|
| **Viral Seasonal Content** | Seasonal Strategist → Provocateur → Sticky Marketer → Wordsmith |
| **Event-Driven Blog** | Event Hunter → Signal Hunter → Storyteller → Wordsmith |
| **High-Engagement Think Piece** | Provocateur → Empathy Engine → Sticky Marketer → Wordsmith → Refiner |
| **Data-Backed Article** | Signal Hunter → Data Weaver → Architect → Wordsmith |
| **Quick, Sticky Post** | Sticky Marketer → Headline Master → Wordsmith |
| **Emotional Story** | Storyteller → Empathy Engine → Wordsmith → Refiner |
| **Standard Quality Blog** | Strategist → Signal Hunter → Architect → Wordsmith → Refiner → Judge |

---

## 🎯 Category 1: Core Workflow Agents

*The foundation of every content generation pipeline—these agents handle the essential stages of content creation.*

---

### 🧭 The Strategist
**Tagline:** *"Every great piece of content starts with a plan"*

**Purpose:** The Strategist is your content planning and strategy expert. They analyze content briefs, target audiences, and funnel stages to create strategic content plans that align with business goals and user needs.

**When to Use:**
- Starting any new content project
- Need to align content with specific funnel stages (Awareness, Activation, Retention)
- Want to ensure strategic messaging and psychological triggers are identified
- Need audience segmentation and persona development

**Pros:**
- ✅ Ensures all content aligns with business objectives
- ✅ Maps content to funnel stages effectively
- ✅ Identifies psychological triggers (empathy, curiosity, fear disconfirmation)
- ✅ Creates clear strategic direction for downstream agents
- ✅ Balances brand voice with strategic goals

**Cons:**
- ⚠️ Can be overly strategic if not balanced with creative agents
- ⚠️ May need additional agents for tactical execution
- ⚠️ Requires clear briefs to be most effective

**Key Features:**
- Audience segmentation and persona development
- Funnel stage mapping (Awareness → Activation → Retention)
- Psychological trigger identification
- Strategic messaging framework development
- Content goal alignment with business outcomes

**Example Output:**
```
Content Plan:
- Target: Never-Engaged Veterans
- Funnel Stage: Activation
- Psychology: Empathy → Identification → Curiosity
- Key Message: "It's normal to hesitate—here's what finally worked"
- Strategic Goal: Convert app downloads to first event attendance
```

**Integration Points:**
- **Input:** Content brief from Airtable (`blogs/{slug}/brief.md`)
- **Output:** Strategic content plan for Researcher and Outliner agents
- **References:** `docs/writing-principles.md` for brand voice guidelines

---

### 🔍 The Signal Hunter
**Tagline:** *"Finding the signals in the noise"*

**Purpose:** The Signal Hunter conducts credibility-focused research, gathering data, insights, and supporting evidence from multiple sources including MongoDB, external research, and platform analytics.

**When to Use:**
- Need data-backed content with credible sources
- Want to incorporate real platform data (events, users, engagement)
- Require external research to support claims
- Need to validate content ideas with data

**Pros:**
- ✅ Gathers comprehensive, credible research
- ✅ Integrates real platform data from MongoDB
- ✅ Validates content ideas with evidence
- ✅ Provides rich context for content creation
- ✅ Ensures factual accuracy

**Cons:**
- ⚠️ Can over-research if not given clear parameters
- ⚠️ May need time to process large datasets
- ⚠️ Requires access to data sources (MongoDB, APIs)

**Key Features:**
- MongoDB event and user data queries
- External research and signal processing
- Credibility-focused source validation
- Data synthesis and insight extraction
- Research document generation

**Example Output:**
```
Research Findings:
- 73% of never-engaged users cite "social anxiety" as primary barrier
- Events with 6-8 attendees show 40% higher engagement rates
- Seasonal patterns: 34% increase in sign-ups during fall months
- User testimonials: 12 verified stories of first-event experiences
```

**Integration Points:**
- **Input:** Content plan from Strategist, brief from Airtable
- **Output:** Research document (`blogs/{slug}/research.md`)
- **Data Sources:** MongoDB via `integrations/mongodb_integration.py`
- **References:** `templates/research.md` for structure

---

### 🏗️ The Architect
**Tagline:** *"Structure is the foundation of great content"*

**Purpose:** The Architect creates content structure and outlines that ensure clarity, flow, and strategic alignment. They transform research and strategy into a logical, engaging content framework.

**When to Use:**
- Need to structure complex topics
- Want to ensure logical flow and readability
- Require strategic outline that guides writing
- Need to organize multiple ideas coherently

**Pros:**
- ✅ Creates clear, logical content structures
- ✅ Ensures strategic alignment in outline
- ✅ Improves readability and flow
- ✅ Guides Writers with clear direction
- ✅ Balances structure with flexibility

**Cons:**
- ⚠️ Can be too rigid if not balanced with creative agents
- ⚠️ May need refinement based on writing style
- ⚠️ Requires good research input to be effective

**Key Features:**
- Content structure and outline generation
- Strategic point organization
- Flow and readability optimization
- Section hierarchy and navigation
- Outline template adherence

**Example Output:**
```
Content Outline:
1. Hook: Personal story of hesitation
2. Problem: Why people download but don't attend
3. Insight: What finally breaks the barrier
4. Solution: Practical steps to overcome hesitation
5. CTA: Join your first event this week
```

**Integration Points:**
- **Input:** Research document, content plan
- **Output:** Content outline (`blogs/{slug}/outline.md`)
- **References:** `templates/outline.md` for structure

---

### ✍️ The Wordsmith
**Tagline:** *"Turning strategy into stories"*

**Purpose:** The Wordsmith generates first drafts of blog content based on briefs, research, and outlines. They use LLM services to create brand-aligned, engaging content that follows strategic guidelines and writing principles.

**When to Use:**
- Ready to generate first draft content
- Have complete brief, research, and outline
- Need brand-aligned writing
- Want to transform strategy into readable content

**Pros:**
- ✅ Generates brand-consistent first drafts
- ✅ Incorporates research naturally
- ✅ Follows strategic guidelines effectively
- ✅ Maintains warm, authentic brand voice
- ✅ Fast draft generation

**Cons:**
- ⚠️ May need editing for polish
- ⚠️ Can be generic without good input
- ⚠️ Requires clear brand voice guidelines

**Key Features:**
- First draft generation following outline structure
- Brand voice consistency (warm, authentic, community-focused)
- Research integration and natural data weaving
- Psychological trigger application
- Strategic messaging incorporation

**Example Output:**
```
First Draft:
"I downloaded the app in January. By June, I still hadn't attended a single event. 
Sound familiar? You're not alone—and here's what finally got me out the door..."
```

**Integration Points:**
- **Input:** Brief, research, outline, content plan
- **Output:** First draft (`blogs/{slug}/blog.md`)
- **LLM Service:** Claude API via `integrations/claude_integration.py`
- **References:** `docs/writing-principles.md`, `templates/draft.md`

---

### ✨ The Refiner
**Tagline:** *"Polishing rough diamonds into gems"*

**Purpose:** The Refiner takes first drafts and elevates them through careful editing, brand compliance checks, and quality improvements. They ensure content meets all quality standards while maintaining authenticity.

**When to Use:**
- Have a first draft that needs polish
- Need brand voice compliance check
- Want to improve readability and engagement
- Require grammar and style consistency

**Pros:**
- ✅ Improves content quality significantly
- ✅ Ensures brand voice compliance
- ✅ Enhances readability and flow
- ✅ Catches errors and inconsistencies
- ✅ Maintains authentic voice while refining

**Cons:**
- ⚠️ Can over-edit if not given clear guidelines
- ⚠️ May need multiple passes for complex content
- ⚠️ Requires good first draft to be most effective

**Key Features:**
- Content refinement and improvement
- Brand voice compliance checking
- Grammar and style consistency
- Readability optimization
- Quality standard enforcement

**Integration Points:**
- **Input:** First draft from Wordsmith
- **Output:** Refined content (`blogs/{slug}/blog.md`)
- **References:** `docs/writing-principles.md` for brand guidelines

---

### ⚖️ The Judge
**Tagline:** *"Quality is not an act, it's a habit"*

**Purpose:** The Judge evaluates content quality, brand alignment, and strategic effectiveness. They provide scoring, feedback, and recommendations to ensure content meets all standards before publication.

**When to Use:**
- Need quality evaluation before publishing
- Want objective scoring and feedback
- Require brand alignment verification
- Need strategic effectiveness assessment

**Pros:**
- ✅ Provides objective quality assessment
- ✅ Ensures brand alignment
- ✅ Validates strategic effectiveness
- ✅ Catches issues before publication
- ✅ Offers actionable improvement recommendations

**Cons:**
- ⚠️ Can be overly critical if thresholds are too high
- ⚠️ May need human review for nuanced decisions
- ⚠️ Requires clear quality standards

**Key Features:**
- Quality evaluation and scoring
- Brand voice alignment checking
- Strategic effectiveness assessment
- Factual accuracy validation
- Workflow status updates

**Integration Points:**
- **Input:** Final content draft
- **Output:** Quality score, feedback, status update
- **References:** `docs/writing-principles.md` for quality standards

---

## 🎨 Category 2: Strategic Content Agents

*Specialized agents that bring unique strategic approaches to content creation—provocation, seasonality, events, and stickiness.*

---

### 🔥 The Provocateur
**Tagline:** *"Provoke thought, not outrage"*

**Purpose:** The Provocateur creates emotionally intense, provocative content that drives virality while maintaining brand credibility. They challenge assumptions and systems without sacrificing trust or long-term credibility.

**When to Use:**
- Need high-arousal content that spreads quickly
- Want to challenge industry norms or assumptions
- Looking to create debate-worthy but respectful content
- Need to stand out in crowded content space
- Want to trigger strong emotional responses

**Pros:**
- ✅ Creates highly shareable, viral content
- ✅ Generates strong emotional engagement
- ✅ Challenges assumptions effectively
- ✅ Maintains brand credibility while being provocative
- ✅ Drives high platform engagement

**Cons:**
- ⚠️ Requires careful balance to avoid brand damage
- ⚠️ May not suit all content goals
- ⚠️ Needs brand voice guardrails
- ⚠️ Can backfire if not executed carefully

**Key Features:**
- Emotionally intense content creation
- Provocative question and statement generation
- Brand-safe provocation strategies
- High-arousal content optimization
- Trust-preserving controversial takes

**Example Output:**
```
Provocative Hook:
"Dating apps are dead. Group dinners killed them—and here's why that's 
the best thing that happened to modern connection."
```

**Integration Points:**
- **Works Best With:** Sticky Marketer, Empathy Engine, Refiner
- **Input:** Content brief, strategic direction
- **Output:** Provocative content elements, hooks, angles
- **Guardrails:** Must align with brand voice (warm, authentic, community-focused)

---

### 🗓️ The Seasonal Strategist
**Tagline:** *"Timing is everything"*

**Purpose:** The Seasonal Strategist analyzes time-of-year patterns, holidays, cultural moments, and seasonal trends to create timely, relevant content that resonates with what audiences are thinking about right now.

**When to Use:**
- Want to capitalize on seasonal moments
- Need timely content aligned with current events
- Looking to leverage holiday or cultural moments
- Want to create "of the moment" content
- Need to align content with seasonal user behavior

**Pros:**
- ✅ Creates highly relevant, timely content
- ✅ Leverages natural interest spikes
- ✅ Aligns with seasonal user behavior patterns
- ✅ Increases content relevance and engagement
- ✅ Helps content feel current and fresh

**Cons:**
- ⚠️ Content may feel dated after season passes
- ⚠️ Requires ongoing calendar awareness
- ⚠️ May need quick turnaround for timely content
- ⚠️ Can miss opportunities if not proactive

**Key Features:**
- Seasonal pattern analysis
- Holiday and cultural moment identification
- Time-based content angle development
- Seasonal user behavior alignment
- Content calendar optimization

**Example Output:**
```
Seasonal Angle:
"New Year, New Connections: Why January is the Perfect Time to Try 
Group Dining (And How to Overcome the Hesitation)"
```

**Integration Points:**
- **Works Best With:** Event Hunter, Provocateur, Signal Hunter
- **Input:** Current date, content brief, user behavior data
- **Output:** Seasonal content angles, timing recommendations
- **Data Sources:** MongoDB for seasonal event patterns

---

### 🎯 The Event Hunter
**Tagline:** *"Real events, real stories, real engagement"*

**Purpose:** The Event Hunter monitors MongoDB for upcoming events, user activity, and social dining data to identify blog opportunities that connect real experiences with audience interests. They create event-driven content that promotes actual events and reflects real community experiences.

**When to Use:**
- Want to promote upcoming events
- Need to highlight new joiners or community moments
- Looking to create content based on real experiences
- Want to increase event attendance through content
- Need to showcase community activity

**Pros:**
- ✅ Creates highly relevant, real-world content
- ✅ Directly drives event attendance
- ✅ Showcases actual community experiences
- ✅ Increases perceived value and authenticity
- ✅ Leverages real data for credibility

**Cons:**
- ⚠️ Requires MongoDB access and data availability
- ⚠️ Content tied to specific events (may date quickly)
- ⚠️ Needs event data to be current and accurate
- ⚠️ May need quick turnaround for event promotion

**Key Features:**
- MongoDB event data queries
- Upcoming event identification
- User activity and engagement analysis
- Event-driven content angle development
- Real experience integration

**Example Output:**
```
Event-Driven Content:
"This Saturday, 12 foodies are gathering at [Restaurant] for a 
Mediterranean feast. Here's why events like this are changing how 
we connect—and how you can join the next one."
```

**Integration Points:**
- **Works Best With:** Signal Hunter, Storyteller, Seasonal Strategist
- **Input:** MongoDB queries via `integrations/mongodb_integration.py`
- **Output:** Event-driven content angles, event promotion content
- **Data Sources:** Events, users, attendance history from MongoDB

---

### 🎯 The Sticky Marketer
**Tagline:** *"Making ideas stick like glue"*

**Purpose:** The Sticky Marketer applies the Made-to-Stick SUCCESs framework (Simple, Unexpected, Credible, Concrete, Emotional, Stories) to ensure content is memorable, shareable, and impactful. They transform good ideas into unforgettable messages.

**When to Use:**
- Need content that's highly memorable
- Want to ensure ideas stick with audiences
- Looking to create shareable, impactful content
- Need to simplify complex ideas
- Want to make content more concrete and credible

**Pros:**
- ✅ Creates highly memorable content
- ✅ Ensures ideas stick with audiences
- ✅ Makes complex ideas simple and accessible
- ✅ Increases shareability and impact
- ✅ Research-backed framework (Made-to-Stick)

**Cons:**
- ⚠️ May oversimplify complex topics
- ⚠️ Requires balance with other content goals
- ⚠️ Can be formulaic if over-applied
- ⚠️ Needs good source material to be effective

**Key Features:**
- **Simple:** Core message stripped to essentials
- **Unexpected:** Surprise elements to grab attention
- **Concrete:** Tangible, specific details (not abstract)
- **Credible:** Trustworthy, believable claims
- **Emotional:** Appeals to feelings and values
- **Stories:** Narrative structure for memorability

**Example Output:**
```
Sticky Content Framework:
Simple: "Group dinners beat dating apps for real connection"
Unexpected: "I was wrong about social dining—here's what changed my mind"
Concrete: "7 strangers, 1 table, 3 hours, 0 awkwardness"
Credible: "Backed by 10,000+ successful events"
Emotional: "The moment I realized I wasn't alone in wanting real connection"
Stories: "Sarah's first event story that changed everything"
```

**Integration Points:**
- **Works Best With:** Any content agent (enhances all content)
- **Input:** Content draft or outline
- **Output:** Sticky-optimized content elements
- **Framework:** Made-to-Stick SUCCESs principles

---

## 🎭 Category 3: Specialized Writing Agents

*Creative agents that bring specific writing superpowers to the content creation process.*

---

### 📰 The Headline Master
**Tagline:** *"First impressions are everything"*

**Purpose:** The Headline Master generates attention-grabbing, click-worthy titles that balance curiosity, clarity, and engagement. They create headlines that make people want to read more.

**When to Use:**
- Need compelling titles for content
- Want to optimize for click-through rates
- Looking to create curiosity gaps
- Need multiple headline options
- Want to A/B test headlines

**Pros:**
- ✅ Creates highly clickable headlines
- ✅ Generates multiple options for testing
- ✅ Balances curiosity with clarity
- ✅ Optimizes for engagement
- ✅ Understands headline psychology

**Cons:**
- ⚠️ Can create clickbait if not balanced
- ⚠️ May prioritize clicks over accuracy
- ⚠️ Needs content context to be effective

**Key Features:**
- Attention-grabbing title generation
- Curiosity gap creation
- Multiple headline variations
- Click-through optimization
- Headline psychology application

**Example Output:**
```
Headline Options:
1. "I Downloaded a Social Dining App and Didn't Go for 6 Months—Here's What Finally Got Me Out the Door"
2. "The One Thing That Changed My Mind About Group Dining"
3. "Why I Waited 6 Months to Attend My First Event (And What Finally Convinced Me)"
```

**Integration Points:**
- **Works Best With:** Any content agent
- **Input:** Content summary, key points
- **Output:** Headline options and variations

---

### 📖 The Storyteller
**Tagline:** *"Stories are how we remember"*

**Purpose:** The Storyteller focuses on narrative structure, emotional arcs, and compelling storytelling. They transform information into engaging narratives that readers remember and share.

**When to Use:**
- Need narrative-driven content
- Want to create emotional connections
- Looking to structure content as stories
- Need to make information memorable through narrative
- Want to create shareable personal stories

**Pros:**
- ✅ Creates highly engaging narratives
- ✅ Makes content memorable through story structure
- ✅ Builds emotional connections
- ✅ Increases shareability
- ✅ Transforms dry information into compelling content

**Cons:**
- ⚠️ May prioritize story over information
- ⚠️ Can be less direct than other approaches
- ⚠️ Requires good source material for stories

**Key Features:**
- Narrative structure development
- Emotional arc creation
- Story-driven content organization
- Character and conflict development
- Memorable storytelling techniques

**Example Output:**
```
Story Structure:
Act 1: Setup - "I was skeptical about group dining"
Act 2: Conflict - "But something kept pulling me back"
Act 3: Resolution - "Here's what finally changed my mind"
```

**Integration Points:**
- **Works Best With:** Empathy Engine, Event Hunter, Signal Hunter
- **Input:** Content outline, research, user stories
- **Output:** Narrative-structured content

---

### 📊 The Data Weaver
**Tagline:** *"Numbers tell stories too"*

**Purpose:** The Data Weaver integrates statistics, research, and data naturally into content. They make numbers compelling and ensure data supports rather than overwhelms the narrative.

**When to Use:**
- Need to incorporate statistics and research
- Want data-backed content
- Looking to add credibility through numbers
- Need to make data engaging and readable
- Want to support claims with evidence

**Pros:**
- ✅ Makes data engaging and readable
- ✅ Adds credibility to content
- ✅ Integrates statistics naturally
- ✅ Supports claims with evidence
- ✅ Transforms dry numbers into insights

**Cons:**
- ⚠️ Can overwhelm if too data-heavy
- ⚠️ May need simplification for general audiences
- ⚠️ Requires accurate, verified data sources

**Key Features:**
- Statistics integration
- Data visualization in text
- Research synthesis
- Credibility through numbers
- Natural data weaving techniques

**Example Output:**
```
Data Integration:
"73% of never-engaged users cite social anxiety as their primary barrier—but 
here's the surprising part: 89% of those who attended their first event 
said it was 'less awkward than expected.'"
```

**Integration Points:**
- **Works Best With:** Signal Hunter, Architect, Wordsmith
- **Input:** Research data, statistics, platform analytics
- **Output:** Data-integrated content

---

### 💝 The Empathy Engine
**Tagline:** *"Understanding before persuading"*

**Purpose:** The Empathy Engine creates content that validates and addresses audience concerns. They acknowledge fears, hesitations, and objections before offering solutions, building trust through understanding.

**When to Use:**
- Need to address audience objections
- Want to validate concerns before solving
- Looking to build trust through empathy
- Need to reduce friction and hesitation
- Want to create relatable, understanding content

**Pros:**
- ✅ Builds trust through validation
- ✅ Reduces audience resistance
- ✅ Creates highly relatable content
- ✅ Addresses objections proactively
- ✅ Increases conversion through empathy

**Cons:**
- ⚠️ Can be too focused on problems if not balanced
- ⚠️ May need to transition to solutions effectively
- ⚠️ Requires understanding of audience concerns

**Key Features:**
- Audience concern validation
- Objection addressing
- Empathetic tone and language
- Trust-building through understanding
- Friction reduction strategies

**Example Output:**
```
Empathetic Content:
"I get it. The idea of dining with strangers can feel awkward, 
overwhelming, or just plain weird. You're not alone in feeling that way— 
and here's what actually helps..."
```

**Integration Points:**
- **Works Best With:** Provocateur, Storyteller, Strategist
- **Input:** Audience research, user feedback, concerns
- **Output:** Empathy-driven content elements

---

## 🎯 Agent Selection Workflows

### Workflow 1: Viral Seasonal Content
```
Seasonal Strategist → Provocateur → Sticky Marketer → Wordsmith → Refiner → Judge
```
**Use Case:** Create timely, provocative content that capitalizes on seasonal moments and goes viral.

### Workflow 2: Event-Driven Blog
```
Event Hunter → Signal Hunter → Storyteller → Wordsmith → Headline Master → Refiner
```
**Use Case:** Promote upcoming events with data-backed, story-driven content.

### Workflow 3: High-Engagement Think Piece
```
Provocateur → Empathy Engine → Sticky Marketer → Wordsmith → Refiner → Judge
```
**Use Case:** Create provocative but empathetic content that challenges assumptions and drives engagement.

### Workflow 4: Data-Backed Article
```
Strategist → Signal Hunter → Data Weaver → Architect → Wordsmith → Refiner
```
**Use Case:** Create credible, research-heavy content with strong data support.

### Workflow 5: Quick, Sticky Post
```
Sticky Marketer → Headline Master → Wordsmith → Refiner
```
**Use Case:** Fast turnaround on memorable, shareable content.

### Workflow 6: Emotional Story
```
Storyteller → Empathy Engine → Wordsmith → Refiner → Headline Master
```
**Use Case:** Create narrative-driven content that builds emotional connections.

### Workflow 7: Standard Quality Blog
```
Strategist → Signal Hunter → Architect → Wordsmith → Refiner → Judge
```
**Use Case:** Reliable, high-quality content following standard workflow.

---

## 🎨 Brand Voice Alignment

All agents operate within the Cuculi brand voice framework:

- **Warm and Inviting:** Like a friend introducing you to their favorite spot
- **Authentic and Honest:** Real stories, not manufactured perfection
- **Community-Focused:** Emphasizes collective experience over individual
- **Food-Positive:** Celebrates culinary experiences without snobbery
- **Empathetic and Understanding:** Acknowledges concerns and validates feelings

---

## 🚀 Getting Started

1. **Choose Your Goal:** What are you trying to achieve with this content?
2. **Select Your Workflow:** Use the workflows above or create your own combination
3. **Configure Agents:** Each agent can be customized with specific prompts and parameters
4. **Execute Pipeline:** Run agents in sequence according to your workflow
5. **Iterate and Optimize:** Test different agent combinations to find what works best

---

## 📚 Additional Resources

- **Agent Instructions:** See individual agent files in `agents/` directory
- **Writing Principles:** `docs/writing-principles.md`
- **Templates:** `templates/` directory for content structure
- **Examples:** `blogs/` directory for completed content examples

---

*Built for the Cuculi AI Content Engine - Where strategy meets creativity, and content goes viral.*

