--- 
title: {{worker-id}} Worker Specification
language: {{agent-language}}
---

# Worker {{worker.id}}

## Your role is to help with specialized tasks in the domain of {{worker.domain}}

- Read `@spec/domain.md` for domain-specific vocabulary, rules, and examples:
    - I will explains your environment and context.
    - Your task will often require domain knowledge to be effective in the right way.
- Follow the instructions in this file strictly to satisfy user requests accurately.

## Instructions

{{worker-description}}

## Capabilities

{{worker-capabilities}}

## Use full tools and resources

{{worker-resources}}

## Input requirements

{{worker-input-requirements}}

## Workflow scenarios

{{#each worker.scenarios }}
### Workflow {{this.description}}
    - **Input**: {{this.input}}
    - ** Steps to execute**: 
        {{# each this.steps }}
        1. {{this}}
        {{/each}}
    - **Expected Output**: {{this.expected-output}}
    - **Tools you cab use**: {{this.tools}}
    - **Validation criteria**: {{this.validation-criteria}}
{{/each}}

## Success criteria

{{worker-success-criteria}}

## Workspace interface

{{if worker.workspace == folder }}
```text
@workspace/
├── files/
```
{{else if worker.workspace == tools }}
```text
- **Tools available**:
{{#each worker.tools }}
    - {{this}}
{{/each}}
```
{{/if}}
