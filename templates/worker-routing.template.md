--- 
title: Worker Routing Logic
domain: {{domain-summary}}
language: {{routing-language}}
version: 1.0
---

# Worker Routing

This document defines how to route user requests to the appropriate specialized workers.

---

## Domain Overview

{{domain-summary}}

---

## Routing Principles

### 1. Intent-First Matching
- Identify the user's primary intent before selecting a worker
- Look for action verbs and target objects in the request
- Map intent to worker capabilities

### 2. Specificity Over Generality
- Prefer workers with more specific matching criteria
- If multiple workers match, choose the most specialized one
- Avoid routing to a worker if only partially capable

### 3. Clarify When Uncertain
- If confidence is below 80%, ask a clarifying question
- Maximum 3 clarification rounds
- Provide 2-3 options for the user to choose from

### 4. Single Responsibility
- Route to ONE worker per atomic task
- For complex requests, break down into sequential tasks
- Each worker handles one well-defined responsibility

---

## Available Workers

{{specialized-workers}}

---

## Routing Decision Matrix

| User Intent Pattern | Matched Worker | Confidence Threshold |
|---------------------|----------------|---------------------|
| {intent-pattern-1} | {worker-id-1} | 80% |
| {intent-pattern-2} | {worker-id-2} | 80% |
| {intent-pattern-3} | {worker-id-3} | 80% |

---

## Routing Algorithm

```
1. RECEIVE user request
2. EXTRACT intent and entities
3. FOR EACH worker in available_workers:
     - CALCULATE match_score based on:
       a. Intent alignment (40%)
       b. Required capabilities present (30%)
       c. Input requirements satisfiable (20%)
       d. Context relevance (10%)
4. SELECT worker with highest match_score
5. IF match_score < 80%:
     - ASK clarifying question
     - GOTO step 1 with additional context
6. IF match_score >= 80%:
     - DELEGATE to selected worker
7. IF no worker matches after 3 attempts:
     - APPLY fallback behavior
```

---

## Intent Keywords

### Worker Selection Hints

| Keywords / Phrases | Likely Worker | Notes |
|-------------------|---------------|-------|
| {keywords-1} | {worker-id-1} | {context-notes} |
| {keywords-2} | {worker-id-2} | {context-notes} |
| {keywords-3} | {worker-id-3} | {context-notes} |

---

## Conflict Resolution

When multiple workers could handle a request:

### Priority Rules
1. **Most specific match wins** — Worker whose capabilities most closely match the request
2. **Most constrained inputs wins** — Worker with stricter input requirements (more specialized)
3. **User preference** — If still tied, ask user to choose

### Disambiguation Questions
Use this format when asking user to choose:
```
Je peux vous aider de plusieurs façons :
1. {Option A - worker-1 capability description}
2. {Option B - worker-2 capability description}

Laquelle correspond le mieux à votre besoin ?
```

---

## Fallback Behavior

{{fallback-behavior}}

### Fallback Triggers
- No worker matches with >50% confidence
- User request is out of domain scope
- Required inputs cannot be obtained
- Maximum clarification rounds exceeded

### Fallback Actions
1. **Acknowledge limitation** — Explain what you can and cannot do
2. **Suggest alternatives** — Offer related capabilities that might help
3. **Escalate if critical** — Route to human operator when necessary

---

## Escalation Triggers

{{escalation-triggers}}

### When to Escalate
| Trigger | Action |
|---------|--------|
| Sensitive data involved | Require human confirmation |
| Irreversible action | Require explicit user consent |
| Repeated failures | Escalate to human operator |
| User frustration detected | Offer human assistance |
| Out of scope but urgent | Route to appropriate channel |

### Escalation Format
```
Je ne suis pas en mesure de traiter cette demande directement.

Raison : {explanation}

Options :
1. {Alternative within scope}
2. Contacter un opérateur humain
3. {Other relevant option}
```

---

## Multi-Step Workflows

For complex requests requiring multiple workers:

### Sequential Execution
```
Request → Worker A → Output A → Worker B → Output B → Final Response
```

### Parallel Execution (when independent)
```
Request → ┬→ Worker A → Output A ─┬→ Combine → Final Response
          └→ Worker B → Output B ─┘
```

### Workflow Rules
1. Break complex requests into atomic tasks
2. Determine dependencies between tasks
3. Execute independent tasks in parallel when possible
4. Pass outputs from one worker as inputs to the next
5. Aggregate results before responding to user

---

## Quality Assurance

### Pre-Routing Checks
- [ ] User intent is clearly understood
- [ ] Required information is available
- [ ] Selected worker can handle the request
- [ ] No conflicting workers selected

### Post-Routing Checks
- [ ] Worker acknowledged the task
- [ ] Worker has required inputs
- [ ] Expected output format is clear
- [ ] Error handling path is defined

---

## Metrics to Track

| Metric | Description | Target |
|--------|-------------|--------|
| Routing accuracy | % of requests routed to correct worker | >95% |
| Clarification rate | % of requests needing clarification | <20% |
| Fallback rate | % of requests hitting fallback | <5% |
| Escalation rate | % of requests escalated to human | <2% |
| First-route success | % of requests completed by first worker | >85% |
