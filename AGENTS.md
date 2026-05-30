# AGENTS.md

Prompt-engineering repo for testing the buggy RESTful Booker API (`https://restful-booker.herokuapp.com/apidoc/index.html`). **No build tooling, no code, no test runner** — planning phase only until REST Assured automation begins.

## Key files

| File | Role |
|---|---|
| `PRD.txt` | Source-of-truth — scope, strategy, environments, defect POCs |
| `Prompt To Generate TestPlan.txt` | LLM prompt for generating `testplanopencode.docx` |
| `Test Case Generation Prompt.txt` | LLM prompt for generating `testcasesopencode.xlsx` |
| `MASTER PROMPT – ENTERPRISE API AUTOMATION FRAMEWORK GENERATION.txt` | Architect-level prompt for generating a Salesforce automation framework (separate use case) |
| `Test cases - Ultimate _ TheTestingAcademy.xlsx` | Reference template defining the General CRUD column layout |

## Skill triggers & TUI commands

| Trigger / TUI | Loads | Produces |
|---|---|---|
| `setup/test plan generator` or `/test-plan-gen` | `.opencode/skills/test-plan-generator/` | `testplanopencode.docx` |
| `setup/test case generator` or `/test-case-gen` | `.opencode/skills/test-case-generator/` | `testcasesopencode.xlsx` |
| `setup/restassured-api-framework` or `/restassured` | `.opencode/skills/restassured-api-framework/` | Java REST Assured framework code |
| `setup/gen-api-framework` or `/gen-api-framework` | `.opencode/skills/gen-api-framework/` | Enterprise API automation framework (Java + Maven + REST Assured + Playwright + CI/CD) |
| `setup/playwright-api` | `.opencode/skills/playwright-api/` | Playwright API testing skill |

## Workflow

1. `setup/test plan generator @PRD.txt` (or `/test-plan-gen`) → `testplanopencode.docx`
2. `setup/test case generator @testplanopencode.docx` (or `/test-case-gen`) → `testcasesopencode.xlsx`
3. Execute test cases manually in Postman
4. Automate with REST Assured *(future phase)*
5. Report bugs in JIRA

## Generated output format

`testcasesopencode.xlsx` uses the **General CRUD** template (14 columns):
`Scenario TID | TestCase Description | PreCondition | TestSteps | Expected Result | Actual Result | Steps to Execute | Expected Result | Actual Result | Status | Executed QA Name | Misc (Comments) | Priority | Is Automated`

Row 2 defaults `Is Automated = No`. Columns 6–12 left blank for execution-time filling.

## Defect POCs (from `PRD.txt`)

- **Frontend**: Devesh
- **Backend**: Sonal
- **DevOps**: Prajeeth

## Toolchain

- **Postman** — manual API test execution
- **REST Assured** — future automation (not yet written)
- **JIRA** — defect tracking
