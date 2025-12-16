--- 
language: {{agent-language}}
---

# How to handle user and request routing to specialized workers

{{ short description of the domain }}

This document describes the routing logic for directing user requests to the appropriate specialized tasks withe the help of specialized worker.
A Specialized worker is an agent designed to handle specific types of requests within a defined domain.

## Routing principles

1. **Identify Intent**: Analyze the user's request to determine the underlying intent and required capabilities.
2. **Match to specialized worker**: Use predefined criteria to match the identified intent with the most suitable specialized worker.
3. **Minimize ambiguity**: If the request is ambiguous, ask up to 3 clarifying questions before routing.
4. **Fallback handling**: If no specialized worker is a perfect match, do not attempt to improvise; instead, prompt the user for more information or escalate to a human operator.
5. **Tie Breaker**: If multiple specialized workers are equally suitable, ask the user a clarifying question to determine the best fit, e.g., "Would you like assistance with [Option A] or [Option B]?"

## Available specialized workers

{{#each specialized-workers }}
- ### {{this.id]}: {{this.description}}
    - Capabilities: {{this.capabilities }}
    - Input requirements: {{this.input-requirements }}
    - worker-instructions: {{this.instructions-path}}
{{/each}}

## How to perform routing

1. **Receive user request**: Capture the user's input and any contextual information.
2. **Analyze request**: Use natural language processing to extract intent and key parameters.
3. **Select specialized worker**: Based on the analysis, select the most appropriate specialized worker.
4. **Read instructions**: Read the file at `{{selected-worker.instructions-path}}` for detailed instructions on how to handle the request.
