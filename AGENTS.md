# AGENTS.md

Three-file repo in the planning/prompt-engineering phase for testing the buggy RESTful Booker API. No build tooling, no code, no tests yet.

## Key files

| File | Role |
|---|---|
| `PRD.txt` | Source-of-truth test plan doc (scope, strategy, environments, defect process, contacts) |
| `Prompt To Generate TestPlan.txt` | LLM prompt that references `@PRD.txt`. Feed this to a local LLM to produce `testplanopencode.docx` |

## Workflow

1. Write/edit LLM prompt in `Prompt To Generate TestPlan.txt`
2. Feed prompt to local LLM → generates Word doc (`testplanopencode.docx`)
3. Execute test cases manually in Postman
4. Automate with REST Assured (not yet written)
5. Report bugs in JIRA

## Toolchain

- **Postman** — manual execution
- **REST Assured** — future automation framework
- **JIRA** — defect tracking
- **Target API**: `https://restful-booker.herokuapp.com/apidoc/index.html`

## Defect contacts (from `PRD.txt`)

- Frontend: Devesh
- Backend: Sonal
- DevOps: Prajeeth

## Testing techniques used

Equivalence partitioning, BVA, decision tables, state transition, error guessing, exploratory testing. Smoke → regression cycles.

## Phase constraint

REST Assured automation code does not exist yet. This repo is **prompt-engineering only** until automation phase begins.

## Reusable skill

`.opencode/skills/test-plan-generator/SKILL.md` encodes the test-plan generation workflow. To use it:
1. Attach a PRD file (source of truth)
2. The skill guides the agent to produce `testplanopencode.docx`
