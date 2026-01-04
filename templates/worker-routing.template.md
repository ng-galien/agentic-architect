--- 
title: {{_("Worker Routing Logic")}}
domain: {{domain-summary}}
language: {{routing-language}}
version: 1.0
---

<!-- 
  LANGUAGE INSTRUCTIONS:
  All text in this template must be translated to {{routing-language}}.
  Only keep IDs, file paths, and code blocks in English.
  Translate: titles, descriptions, instructions, comments, table headers.
-->

# {{_("Worker Routing")}}

{{_("This document defines how to route user requests to the appropriate specialized workers.")}}

---

## {{_("Domain Overview")}}

{{domain-summary}}

---

## {{_("Routing Principles")}}

### 1. {{_("Intent-First Matching")}}
- {{_("Identify the user's primary intent before selecting a worker")}}
- {{_("Look for action verbs and target objects in the request")}}
- {{_("Map intent to worker capabilities")}}

### 2. {{_("Specificity Over Generality")}}
- {{_("Prefer workers with more specific matching criteria")}}
- {{_("If multiple workers match, choose the most specialized one")}}
- {{_("Avoid routing to a worker if only partially capable")}}

### 3. {{_("Clarify When Uncertain")}}
- {{_("If confidence is below 80%, ask a clarifying question")}}
- {{_("Maximum 3 clarification rounds")}}
- {{_("Provide 2-3 options for the user to choose from")}}

### 4. {{_("Single Responsibility")}}
- {{_("Route to ONE worker per atomic task")}}
- {{_("For complex requests, break down into sequential tasks")}}
- {{_("Each worker handles one well-defined responsibility")}}

---

## {{_("Available Workers")}}

{{specialized-workers}}

---

## {{_("Routing Decision Matrix")}}

| {{_("User Intent Pattern")}} | {{_("Matched Worker")}} | {{_("Confidence Threshold")}} |
|---------------------|----------------|---------------------|
| {intent-pattern-1} | {worker-id-1} | 80% |
| {intent-pattern-2} | {worker-id-2} | 80% |
| {intent-pattern-3} | {worker-id-3} | 80% |

---

## {{_("Routing Algorithm")}}

```
1. {{_("RECEIVE user request")}}
2. {{_("EXTRACT intent and entities")}}
3. {{_("FOR EACH worker in available_workers:")}}
     - {{_("CALCULATE match_score based on:")}}
       a. {{_("Intent alignment")}} (40%)
       b. {{_("Required capabilities present")}} (30%)
       c. {{_("Input requirements satisfiable")}} (20%)
       d. {{_("Context relevance")}} (10%)
4. {{_("SELECT worker with highest match_score")}}
5. {{_("IF match_score < 80%:")}}
     - {{_("ASK clarifying question")}}
     - {{_("GOTO step 1 with additional context")}}
6. {{_("IF match_score >= 80%:")}}
     - {{_("DELEGATE to selected worker")}}
7. {{_("IF no worker matches after 3 attempts:")}}
     - {{_("APPLY fallback behavior")}}
```

---

## {{_("Intent Keywords")}}

### {{_("Worker Selection Hints")}}

| {{_("Keywords / Phrases")}} | {{_("Likely Worker")}} | {{_("Notes")}} |
|-------------------|---------------|-------|
| {keywords-1} | {worker-id-1} | {context-notes} |
| {keywords-2} | {worker-id-2} | {context-notes} |
| {keywords-3} | {worker-id-3} | {context-notes} |

---

## {{_("Conflict Resolution")}}

{{_("When multiple workers could handle a request:")}}

### {{_("Priority Rules")}}
1. **{{_("Most specific match wins")}}** — {{_("Worker whose capabilities most closely match the request")}}
2. **{{_("Most constrained inputs wins")}}** — {{_("Worker with stricter input requirements (more specialized)")}}
3. **{{_("User preference")}}** — {{_("If still tied, ask user to choose")}}

### {{_("Disambiguation Questions")}}
{{_("Use this format when asking user to choose:")}}
```
{{_("I can help you in several ways:")}}
1. {Option A - worker-1 capability description}
2. {Option B - worker-2 capability description}

{{_("Which one best matches your need?")}}
```

---

## {{_("Fallback Behavior")}}

{{fallback-behavior}}

### {{_("Fallback Triggers")}}
- {{_("No worker matches with >50% confidence")}}
- {{_("User request is out of domain scope")}}
- {{_("Required inputs cannot be obtained")}}
- {{_("Maximum clarification rounds exceeded")}}

### {{_("Fallback Actions")}}
1. **{{_("Acknowledge limitation")}}** — {{_("Explain what you can and cannot do")}}
2. **{{_("Suggest alternatives")}}** — {{_("Offer related capabilities that might help")}}
3. **{{_("Escalate if critical")}}** — {{_("Route to human operator when necessary")}}

---

## {{_("Escalation Triggers")}}

{{escalation-triggers}}

### {{_("When to Escalate")}}
| {{_("Trigger")}} | {{_("Action")}} |
|---------|--------|
| {{_("Sensitive data involved")}} | {{_("Require human confirmation")}} |
| {{_("Irreversible action")}} | {{_("Require explicit user consent")}} |
| {{_("Repeated failures")}} | {{_("Escalate to human operator")}} |
| {{_("User frustration detected")}} | {{_("Offer human assistance")}} |
| {{_("Out of scope but urgent")}} | {{_("Route to appropriate channel")}} |

### {{_("Escalation Format")}}
```
{{_("I am not able to process this request directly.")}}

{{_("Reason:")}}: {explanation}

{{_("Options:")}}
1. {{{_("Alternative within scope")}}}
2. {{_("Contact a human operator")}}
3. {{{_("Other relevant option")}}}
```

---

## {{_("Multi-Step Workflows")}}

{{_("For complex requests requiring multiple workers:")}}

### {{_("Sequential Execution")}}
```
{{_("Request")}} → Worker A → Output A → Worker B → Output B → {{_("Final Response")}}
```

### {{_("Parallel Execution")}} ({{_("when independent")}})
```
{{_("Request")}} → ┬→ Worker A → Output A ─┬→ {{_("Combine")}} → {{_("Final Response")}}
          └→ Worker B → Output B ─┘
```

### {{_("Workflow Rules")}}
1. {{_("Break complex requests into atomic tasks")}}
2. {{_("Determine dependencies between tasks")}}
3. {{_("Execute independent tasks in parallel when possible")}}
4. {{_("Pass outputs from one worker as inputs to the next")}}
5. {{_("Aggregate results before responding to user")}}

---

## {{_("Quality Assurance")}}

### {{_("Pre-Routing Checks")}}
- [ ] {{_("User intent is clearly understood")}}
- [ ] {{_("Required information is available")}}
- [ ] {{_("Selected worker can handle the request")}}
- [ ] {{_("No conflicting workers selected")}}

### {{_("Post-Routing Checks")}}
- [ ] {{_("Worker acknowledged the task")}}
- [ ] {{_("Worker has required inputs")}}
- [ ] {{_("Expected output format is clear")}}
- [ ] {{_("Error handling path is defined")}}

---

## {{_("Metrics to Track")}}

| {{_("Metric")}} | {{_("Description")}} | {{_("Target")}} |
|--------|-------------|--------|
| {{_("Routing accuracy")}} | {{_("% of requests routed to correct worker")}} | >95% |
| {{_("Clarification rate")}} | {{_("% of requests needing clarification")}} | <20% |
| {{_("Fallback rate")}} | {{_("% of requests hitting fallback")}} | <5% |
| {{_("Escalation rate")}} | {{_("% of requests escalated to human")}} | <2% |
| {{_("First-route success")}} | {{_("% of requests completed by first worker")}} | >85% |
