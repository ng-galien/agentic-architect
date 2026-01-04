# Agentic Architect

Design and compile autonomous agent specifications with a clear, validated workflow.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Overview

Agentic Architect is a framework for designing **supervisor-worker agent systems**. It guides you through a structured process to:

1. **Specify** your business domain and workflows
2. **Define** specialized workers with clear responsibilities
3. **Compile** production-ready agent specifications

```
┌─────────────────────────────────────────────────────────┐
│                     SUPERVISOR                          │
│  • Receives and analyzes user requests                  │
│  • Determines intent and routes to workers              │
│  • Orchestrates multi-worker workflows                  │
└───────────────────────┬─────────────────────────────────┘
                        │ routing
        ┌───────────────┼───────────────┐
        ▼               ▼               ▼
   ┌─────────┐    ┌─────────┐    ┌─────────┐
   │ Worker  │    │ Worker  │    │ Worker  │
   │   A     │    │   B     │    │   C     │
   └─────────┘    └─────────┘    └─────────┘
```

## Features

- 📋 **Structured specification process** — Domain documentation, workflow planning, and progress tracking
- 🔄 **Iterative refinement** — Dialogue-driven clarification with checklists
- 🌍 **Multi-language support** — Generates agents in the user's language
- 📦 **Template-based compilation** — Consistent, production-ready output
- ✅ **Validation gates** — Prevents compilation until specifications are complete

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/ng-galien/agentic-architect.git
   cd agentic-architect
   ```

2. Add `AGENTS.md` as custom instructions in your AI assistant (GitHub Copilot, Claude, etc.)

3. Start designing agents!

## Usage

### Creating a New Agent

Start a conversation with the architect:

```
Create a supervisor for [your domain].

## Business Context
[Describe what the agent should do]

## Workers needed
- [worker-1]: [responsibility]
- [worker-2]: [responsibility]

## Business Rules
[Constraints and policies]
```

### Workflow

| Stage | Description | Output |
|-------|-------------|--------|
| **1. Specification** | Define domain, workflows, workers | `specs/{id}/domain.md`, `specs/{id}/plans.md` |
| **2. Compilation** | Generate agent files from templates | `agents/{id}/` |

### Project Structure

```
agentic-architect/
├── AGENTS.md                    # Architect instructions
├── templates/                   # Compilation templates
│   ├── supervisor-template.md
│   ├── worker-spec.template.md
│   └── worker-routing.template.md
├── specs/                       # Specifications (Stage 1)
│   └── {supervisor-id}/
│       ├── domain.md
│       └── plans.md
└── agents/                      # Compiled agents (Stage 2)
    └── {supervisor-id}/
        ├── domain.md
        ├── supervisor.md
        ├── worker-routing.md
        └── workers/
            └── {worker-id}.md
```

## Example

Here's a simple example — a note-taking assistant:

```
Create a supervisor for smart note management.

## Workers needed
- format-note: Restructure raw notes into clean Markdown
- tag-note: Categorize notes with relevant tags
- summarize-note: Extract key points from long notes

## Business Rules
- Never delete information, only restructure
- Output format: Markdown
- Preserve the user's original intent
```

## Templates

The framework includes 3 templates:

| Template | Purpose |
|----------|---------|
| `supervisor-template.md` | Generates the supervisor agent with routing logic |
| `worker-spec.template.md` | Generates specialized worker specifications |
| `worker-routing.template.md` | Generates intent-to-worker routing rules |

All templates support **automatic translation** to the user's language via `{{_("...")}}` markers.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
