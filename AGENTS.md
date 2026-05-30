# AGENTS.md

Prompt-engineering repo for testing the buggy RESTful Booker API (`https://restful-booker.herokuapp.com/apidoc/index.html`). No build tooling, no code, no test runner — **planning phase only** until REST Assured automation begins.

## Key files

| File | Role |
|---|---|
| `PRD.txt` | Source-of-truth — scope, strategy, environments, defect process, POC contacts |
| `Prompt To Generate TestPlan.txt` | LLM prompt (references `@PRD.txt`). Feed to any LLM to produce `testplanopencode.docx` |
| `Test Case Generation Prompt.txt` | LLM prompt to produce `testcasesopencode.xlsx` in General CRUD template format |
| `Test cases - Ultimate _ TheTestingAcademy.xlsx` | Reference template defining the General CRUD column layout for test case output |

## Skills (installed globally — usable from any directory)

| Trigger | Loads | Produces |
|---|---|---|
| `setup/test plan generator` or `/test-plan-gen` | `.opencode/skills/test-plan-generator/SKILL.md` | `testplanopencode.docx` |
| `setup/test case generator` or `/test-case-gen` | `.opencode/skills/test-case-generator/SKILL.md` | `testcasesopencode.xlsx` |

Both skills are also mirrored at `~/.config/opencode/skills/` and registered as TUI commands in `~/.config/opencode/opencode.jsonc`.

## Workflow (primary — skill path)

1. Say `setup/test plan generator @PRD.txt` (or `/test-plan-gen`)
2. Agent loads the skill and generates `testplanopencode.docx`
3. Say `setup/test case generator @testplanopencode.docx` (or `/test-case-gen`)
4. Agent loads the skill and generates `testcasesopencode.xlsx` (General CRUD format)
5. Execute test cases manually in Postman
6. Automate with REST Assured *(future phase)*
7. Report bugs in JIRA

## Generated output format

`testcasesopencode.xlsx` uses the **General CRUD** template (14 columns):
`Scenario TID | TestCase Description | PreCondition | TestSteps | Expected Result | Actual Result | Steps to Execute | Expected Result | Actual Result | Status | Executed QA Name | Misc (Comments) | Priority | Is Automated`

Row 2 defaults `Is Automated = No`. Columns 6–12 left blank for execution-time filling.

## Defect POCs (from `PRD.txt`)

- **Frontend**: Devesh
- **Backend**: Sonal
- **DevOps**: Prajeeth

## Testing techniques

Equivalence partitioning, BVA, decision tables, state transition, error guessing, exploratory testing. Smoke → regression cycles.

## Toolchain

- **Postman** — manual API test execution
- **REST Assured** — future automation (not yet written)
- **JIRA** — defect tracking
