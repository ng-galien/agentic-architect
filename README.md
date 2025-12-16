# Agentic Architect

**Agentic Architect** is a meta-agent that produces **agents as deliverables**.

Instead of jumping straight to execution, it designs an agent as a *verifiable workflow*:

* **Routing**: choose (reuse / update / create) the right agent for the request
* **Planning**: turn the chosen process into an executable plan + explicit acceptance criteria
* **Execution**: produce the agent blueprint (not the final business output)
* **Validation**: ensure the produced agent is testable via scenarios and evidence

This repository is intentionally **OpenSpec-inspired**, but generalized beyond software.

---

## What you’ll find here

* `AGENTS.md` — operational rules for AI assistants (workflow, gatekeeping, strict formatting)
* `project.md` — project conventions (naming, where to put context, what is strict vs free-form)
* `specs/` — the current “truth”: agents that are considered in force
* `changes/` — proposed changes to agents (reviewable, versionable)
* `templates/` — copy/paste skeletons to create new agents quickly

---

## Repository layout

```
agentic-architect/
├── AGENTS.md
├── project.md
├── specs/
│   └── agentic-architect/
│       ├── spec.md
│       ├── design.md
│       ├── context.md
│       └── playbook.md
├── changes/
│   └── archive/
└── templates/
    ├── agent-spec.md
    ├── agent-design.md
    ├── agent-context.md
    └── agent-playbook.md
```

---

## Core idea

A **spec** is the description of one or more **processes** in a business domain.

An **agent** is a packaged, testable way to execute those processes:

* clear inputs and outputs
* a stable workflow (route → plan → execute → validate)
* explicit guardrails
* scenarios that make success/failure observable

The **Agentic Architect** produces such agents.

---

## Operating model

### Inputs (governance / references)

* Routing hints (signals → process)
* Domain knowledge (glossary, artifacts, rules)
* Planning methodology (how to build an executable plan)
* Validation policy (acceptance criteria + evidence)

### Agent flow (what the agent does)

1. Normalize the prompt (intake)
2. Route to the right process / agent archetype
3. Build a plan + definition of done
4. Produce the **agent blueprint**
5. Validate the blueprint via scenarios

### Outputs

* Agent spec (strict, testable)
* Supporting docs (context, playbook)
* Scenario-based validation suite

---

## Getting started

### Create the repository structure

Run the bootstrap script below to create the initial structure:

```bash
set -euo pipefail

REPO=agentic-architect

mkdir -p "$REPO" && cd "$REPO"

git init

mkdir -p \
  specs/agentic-architect \
  changes/archive \
  templates

cat > project.md <<'EOF'
# project.md

(placeholder)
EOF

cat > AGENTS.md <<'EOF'
# AGENTS.md

(placeholder)
EOF

for f in spec.md design.md context.md playbook.md; do
  cat > "specs/agentic-architect/$f" <<EOF
# specs/agentic-architect/$f

(placeholder)
EOF
done

cat > templates/agent-spec.md <<'EOF'
# templates/agent-spec.md

(placeholder)
EOF

cat > templates/agent-design.md <<'EOF'
# templates/agent-design.md

(placeholder)
EOF

cat > templates/agent-context.md <<'EOF'
# templates/agent-context.md

(placeholder)
EOF

cat > templates/agent-playbook.md <<'EOF'
# templates/agent-playbook.md

(placeholder)
EOF

cat > .gitignore <<'EOF'
.DS_Store
.idea/
.vscode/
EOF

git add .
git commit -m "chore: bootstrap agentic architect repo structure"

command -v tree >/dev/null 2>&1 && tree -a -I .git || true
```

---

## How to evolve an agent

1. Create a change proposal in `changes/<change-id>/`
2. Add spec deltas under `changes/<change-id>/specs/<agent-id>/spec.md`
3. Validate structure and scenarios (initially via checklist; later via automation)
4. After approval, update `specs/<agent-id>/` and archive the change

---

## Status

This is an early scaffold. The next steps are:

* write `AGENTS.md` (workflow + strict rules)
* define `project.md` conventions
* finalize the strict `spec.md` template and a lightweight validation checklist
