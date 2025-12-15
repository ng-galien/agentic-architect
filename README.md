# Agentic Architect

```shell
# Core structure
mkdir -p \
  specs/agentic-architect \
  changes/archive \
  templates

# Root files
cat > project.md <<'EOF'
# project.md

(placeholder)
EOF

cat > AGENTS.md <<'EOF'
# AGENTS.md

(placeholder)
EOF

# First built-in agent spec (the meta-agent itself)
for f in spec.md design.md context.md playbook.md; do
  cat > "specs/agentic-architect/$f" <<EOF
# specs/agentic-architect/$f

(placeholder)
EOF
done

# Templates for future agents
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

# Optional: add a .gitignore
cat > .gitignore <<'EOF'
.DS_Store
.idea/
.vscode/
EOF

git add .
git commit -m "chore: bootstrap agentic architect repo structure"
echo "Agentic Architect repository structure has been created."
```