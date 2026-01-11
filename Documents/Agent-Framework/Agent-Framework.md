# AI Content Agent Framework

This document defines the **intelligence layer**: which agents exist, their responsibilities, and how they collaborate to produce high-quality content. The framework operationalizes the [[Growth-Strategy]] and implements the requirements from the [[Technical-Specification]] through a multi-agent system architecture.

## Overview of Multi-Agent Approach

### Why Multi-Agent?

A single agent attempting to handle all content generation tasks would struggle with:
- **Complexity**: Different content types require different expertise
- **Quality**: Specialized agents produce higher quality output
- **Maintainability**: Easier to improve individual agents than a monolithic system
- **Flexibility**: Can swap or upgrade agents independently
- **Scalability**: Can parallelize agent work for faster generation

### Agent Architecture Principles

1. **Specialization**: Each agent has a focused responsibility
2. **Collaboration**: Agents work together through defined interfaces
3. **Modularity**: Agents can be developed, tested, and improved independently
4. **Observability**: All agent actions are logged and traceable
5. **Adaptability**: Agents can evolve prompts and strategies over time

### Agent Interaction Model

```
Content Request
      │
      ▼
Orchestrator Agent
      │
      ├──▶ Research Agent ──▶ Context
      │
      ├──▶ Writer Agent ───▶ Draft Content
      │
      ├──▶ Editor Agent ───▶ Refined Content
      │
      ├──▶ Quality Agent ──▶ Quality Score
      │
      └──▶ Formatter Agent ─▶ Final Content
```

## Agent Roles and Responsibilities

### 1. Orchestrator Agent

**Purpose**: Coordinates the content generation workflow

**Responsibilities**:
- Receive content generation requests
- Break down requests into tasks
- Assign tasks to appropriate agents
- Coordinate agent interactions
- Manage workflow state
- Handle errors and retries
- Return final content

**Inputs**:
- Content request (type, topic, audience, deadline)
- Strategic guidelines from [[Growth-Strategy]]
- Available agents and their capabilities

**Outputs**:
- Completed content
- Generation metadata (agents used, time taken, quality scores)
- Workflow status

**Constraints**:
- Must complete within time limits
- Must handle agent failures gracefully
- Must maintain workflow state

### 2. Research Agent

**Purpose**: Gather and synthesize context for content generation

**Responsibilities**:
- Collect relevant signals from research layer
- Identify current events and trends
- Gather platform data and user insights
- Synthesize research into actionable context
- Provide citations and sources

**Inputs**:
- Content topic and requirements
- Research data sources
- Historical content performance data

**Outputs**:
- Research summary
- Key insights and trends
- Relevant data points
- Source citations
- Content opportunity recommendations

**Constraints**:
- Must provide accurate, verifiable information
- Must cite sources for all claims
- Must complete within time limits
- Must filter irrelevant information

### 3. Writer Agent

**Purpose**: Generate initial content drafts

**Responsibilities**:
- Create content based on research and requirements
- Follow brand voice and tone guidelines
- Structure content appropriately
- Generate multiple content types (blog, social, newsletter)
- Ensure content meets length and format requirements

**Inputs**:
- Research context from Research Agent
- Content requirements (type, length, format)
- Brand voice guidelines
- Templates and examples

**Outputs**:
- Draft content
- Content metadata (word count, structure)
- Confidence scores

**Constraints**:
- Must adhere to brand voice (90%+ compliance)
- Must meet length requirements
- Must follow content structure guidelines
- Must avoid sensitive topics without flagging

**Specializations**:
- **Blog Writer**: Long-form articles, SEO optimization
- **Social Writer**: Short-form posts, platform-specific formatting
- **Newsletter Writer**: Multi-section content, email formatting

### 4. Editor Agent

**Purpose**: Refine and improve content quality

**Responsibilities**:
- Review content for quality issues
- Improve clarity and readability
- Enhance engagement potential
- Fix grammar and style issues
- Optimize for target audience
- Ensure brand voice compliance

**Inputs**:
- Draft content from Writer Agent
- Quality criteria and scoring rubrics
- Brand voice guidelines
- Audience preferences

**Outputs**:
- Refined content
- Quality improvements made
- Quality score
- Recommendations for further improvement

**Constraints**:
- Must improve quality without changing core message
- Must maintain brand voice
- Must complete within time limits
- Must preserve factual accuracy

### 5. Quality Agent

**Purpose**: Evaluate content quality and make routing decisions

**Responsibilities**:
- Score content across multiple dimensions
- Evaluate brand voice compliance
- Check factual accuracy
- Assess engagement potential
- Make routing decisions (auto-approve vs. human review)
- Provide quality feedback

**Inputs**:
- Content from Writer or Editor Agent
- Quality scoring criteria
- Brand voice guidelines
- Historical quality benchmarks

**Outputs**:
- Quality scores (relevance, engagement, brand alignment, technical quality)
- Overall quality score
- Routing decision (auto-approve, human review, revision needed)
- Quality feedback and recommendations

**Constraints**:
- Must use consistent scoring criteria
- Must make accurate routing decisions
- Must complete scoring quickly
- Must flag sensitive content appropriately

### 6. Fact Checker Agent

**Purpose**: Validate factual claims in content

**Responsibilities**:
- Identify factual claims in content
- Verify claims against sources
- Flag unverifiable claims
- Provide source citations
- Mark claims as verified, unverified, or opinion

**Inputs**:
- Content to fact-check
- Research sources and data
- Fact-checking databases

**Outputs**:
- Fact-checked content with annotations
- Verification status for each claim
- Source citations
- Flags for unverifiable claims

**Constraints**:
- Must verify all factual claims
- Must cite sources
- Must flag unverifiable information
- Must complete within time limits

### 7. Brand Voice Agent

**Purpose**: Ensure content matches brand voice and tone

**Responsibilities**:
- Evaluate brand voice compliance
- Compare content to brand voice guidelines
- Score voice alignment
- Suggest improvements for better alignment
- Flag content that doesn't match brand

**Inputs**:
- Content to evaluate
- Brand voice guidelines from [[Growth-Strategy]]
- Historical examples of on-brand content

**Outputs**:
- Brand voice compliance score
- Alignment analysis
- Suggestions for improvement
- Flags for significant misalignment

**Constraints**:
- Must use consistent evaluation criteria
- Must reference brand guidelines
- Must provide actionable feedback
- Must complete evaluation quickly

### 8. Formatter Agent

**Purpose**: Format content for specific channels and platforms

**Responsibilities**:
- Convert content to channel-specific formats
- Apply templates and styling
- Optimize for platform requirements
- Add metadata and tags
- Prepare content for publishing

**Inputs**:
- Approved content
- Target platform/channel
- Formatting templates
- Platform-specific requirements

**Outputs**:
- Formatted content
- Platform-ready output (JSON, HTML, Markdown)
- Metadata and tags
- Media requirements

**Constraints**:
- Must meet platform format requirements
- Must preserve content meaning
- Must apply templates correctly
- Must complete formatting quickly

## Inputs, Outputs, and Constraints per Agent

### Agent Communication Protocol

Agents communicate through a standardized message format:

```json
{
  "agent_id": "string",
  "task_id": "string",
  "content_type": "blog|social|newsletter",
  "input": {
    "content": "string or object",
    "context": "object",
    "requirements": "object"
  },
  "output": {
    "content": "string or object",
    "metadata": "object",
    "scores": "object",
    "flags": "array"
  },
  "status": "success|error|needs_review",
  "timestamp": "ISO 8601"
}
```

### Agent Constraints Summary

| Agent | Time Limit | Quality Threshold | Error Handling |
|-------|-----------|-------------------|----------------|
| Orchestrator | 30 min | N/A | Retry, fallback agents |
| Research | 10 min | Source accuracy | Use cached data |
| Writer | 15 min | 80% brand compliance | Retry with different approach |
| Editor | 5 min | Improve by 10% | Flag for human review |
| Quality | 2 min | Consistent scoring | Use default scores |
| Fact Checker | 5 min | Verify all claims | Flag unverified |
| Brand Voice | 2 min | 90% compliance | Flag for review |
| Formatter | 1 min | Format correctness | Use default format |

## Agent Interaction and Sequencing

### Standard Content Generation Workflow

1. **Orchestrator** receives content request
2. **Orchestrator** initiates **Research Agent** to gather context
3. **Research Agent** returns context and insights
4. **Orchestrator** initiates **Writer Agent** with context
5. **Writer Agent** generates draft content
6. **Orchestrator** initiates **Editor Agent** to refine content
7. **Editor Agent** returns refined content
8. **Orchestrator** initiates **Quality Agent** to evaluate
9. **Quality Agent** scores content and makes routing decision
10. If approved: **Orchestrator** initiates **Formatter Agent**
11. If needs review: Content routed to human review
12. If needs revision: Loop back to **Editor Agent** or **Writer Agent**

### Parallel Processing Opportunities

- **Research** and **Template Loading** can run in parallel
- **Fact Checking** and **Brand Voice** evaluation can run in parallel
- Multiple content pieces can be generated in parallel

### Error Handling and Retries

- **Agent Failures**: Orchestrator retries with exponential backoff
- **Quality Issues**: Content routed to Editor Agent for revision
- **Timeout**: Content flagged for human review
- **Critical Errors**: Workflow paused, alert sent

### Agent Handoff Patterns

#### Sequential Handoff
- Research → Writer → Editor → Quality
- Each agent waits for previous to complete

#### Parallel Handoff
- Quality Agent triggers Fact Checker and Brand Voice Agent simultaneously
- Results combined before routing decision

#### Conditional Handoff
- Quality Agent routes to Formatter (if approved) or Human Review (if not)
- Editor Agent routes to Quality (if improved) or back to Writer (if major issues)

## Prompt Evolution and Evaluation Strategy

### Prompt Management Philosophy

Prompts are **not static assets**. They should:
- Evolve based on performance data
- Adapt to changing requirements
- Improve through iteration
- Be version-controlled and tested

### Prompt Structure

Each agent has a base prompt with:
1. **Role Definition**: Agent's purpose and responsibilities
2. **Context**: Strategic guidelines, brand voice, requirements
3. **Instructions**: Specific tasks and constraints
4. **Examples**: High-quality examples of desired output
5. **Output Format**: Expected structure and format

### Prompt Versioning

- **Version Control**: All prompts stored in version control
- **A/B Testing**: Test prompt variations
- **Performance Tracking**: Track which prompts perform best
- **Rollback Capability**: Revert to previous versions if needed

### Prompt Evaluation Metrics

#### Content Quality Metrics
- Quality scores from Quality Agent
- Brand voice compliance scores
- Engagement metrics (when content published)
- Human review feedback

#### Agent Performance Metrics
- Task completion time
- Error rates
- Retry rates
- Success rates

#### System-Level Metrics
- End-to-end generation time
- Auto-approval rates
- Human review rates
- Content performance

### Prompt Improvement Process

1. **Identify Issues**: Review metrics and feedback
2. **Hypothesize**: Form hypothesis about prompt improvements
3. **Create Variation**: Develop new prompt version
4. **Test**: A/B test new prompt against current
5. **Evaluate**: Compare metrics and feedback
6. **Deploy**: Roll out winning prompt version
7. **Monitor**: Track performance of new prompt
8. **Iterate**: Continue improvement cycle

### Prompt Examples by Agent

#### Research Agent Prompt Structure
```
You are a Research Agent for a social dining platform content system.

Your role:
- Gather relevant context for content generation
- Identify current events and trends
- Synthesize research into actionable insights

Context:
- Platform: Social dining platform connecting people over food
- Audience: [audience segment]
- Content goal: [specific goal]

Instructions:
1. Research [topic]
2. Identify key trends and insights
3. Provide citations for all claims
4. Summarize in [format]

Output format: [JSON structure]
```

#### Writer Agent Prompt Structure
```
You are a Writer Agent for a social dining platform content system.

Your role:
- Generate engaging content aligned with brand voice
- Create content that drives user engagement
- Follow brand guidelines and strategic objectives

Brand Voice:
- Warm and inviting
- Authentic and genuine
- Community-focused
- Food-positive
- Inclusive

Content Requirements:
- Type: [blog|social|newsletter]
- Length: [word count]
- Audience: [audience segment]
- Goal: [engagement goal]

Research Context:
[research summary from Research Agent]

Output format: [content structure]
```

## Agent Performance Monitoring

### Key Metrics per Agent

- **Task Completion Rate**: Percentage of tasks completed successfully
- **Average Processing Time**: Time to complete tasks
- **Quality Scores**: Average quality scores for agent output
- **Error Rate**: Percentage of tasks that fail
- **Retry Rate**: Percentage of tasks requiring retries

### Agent Health Monitoring

- **Availability**: Agent uptime and responsiveness
- **Resource Usage**: CPU, memory, API usage
- **Error Patterns**: Types and frequencies of errors
- **Performance Trends**: Improvement or degradation over time

### Alerting and Intervention

- **Critical Alerts**: Agent failures, quality degradation
- **Warning Alerts**: Performance degradation, increased error rates
- **Info Alerts**: Significant changes in metrics
- **Intervention**: Automatic fallback or manual intervention triggers

## Related Documents

This agent framework connects to:

- [[Growth-Strategy]] - Strategic foundation that guides agent behavior
- [[Technical-Specification]] - Requirements that agents must meet
- [[System-Architecture]] - System-level architecture that agents operate within
- [[Templates-Guide]] - Templates that agents use for content generation

## Ownership and Accountability

| Role | Responsibility |
|------|----------------|
| **Accountable Owner** | Applied AI Product Lead |
| **Key Collaborators** | Prompt Engineer, AI/ML Engineer |
| **Review Cycle** | Updated when agents are added, modified, or prompts evolve |
| **Success Metrics** | Agent performance metrics, content quality, system efficiency |

---

*This framework should be reviewed and updated when adding new agents, improving prompts, or when agent performance indicates need for changes.*

