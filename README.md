# brianpw / claude-skills

Claude Code skills for structured document review and related product-engineering workflows.

## Contents

- **[iterative-document-review](iterative-document-review/SKILL.md)** — Multi-pass, converge-to-clean review of specs, PRDs, RFCs, architecture docs, and similar structured documents. Runs review passes as isolated subagents, auto-fixes what it can, batches questions for the user, and re-reviews until no Critical/High/Medium findings remain.

## Install

### As a Claude Code plugin (recommended)

Add this repo as a marketplace, then install the plugin:

```
/plugin marketplace add brianpw/claude-skills
/plugin install iterative-document-review@brianpw-claude-skills
```

### Manual install (no marketplace)

Clone and drop the skill directory into your Claude Code skills folder:

```powershell
git clone https://github.com/brianpw/claude-skills.git
Copy-Item -Recurse claude-skills/iterative-document-review $env:USERPROFILE/.claude/skills/
```

The skill will be discovered on Claude Code's next start. Verify with `/skill` or by asking Claude to list available skills.

## Using iterative-document-review

Once installed, trigger it by asking Claude to review a document:

```
Review docs/payment-service-prd.md — find gaps, risks, and unclear requirements. Max 3 passes.
```

Claude will dispatch review passes as subagents, auto-fix issues it has context for, ask you via `AskUserQuestion` for items requiring stakeholder input, and deliver a final report when the document converges (no Critical/High/Medium findings remain) or the pass limit is hit.

See [`iterative-document-review/SKILL.md`](iterative-document-review/SKILL.md) for the full process, severity definitions, and worked classification examples.

## License

[MIT](LICENSE)
