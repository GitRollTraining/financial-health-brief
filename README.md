# Project 1: Financial Health Brief

Build a reusable Agent Skill that turns the provided financial source data into normalized CSV files and a concise daily management brief.

You will interview a Finance and Operations Manager to understand the reporting request, workflow, data sources, and decision boundaries. The stakeholder shares source links only when they are relevant to the problem you are currently solving, so explain what you need and why.

## Start the project

1. Fork this repository to your own GitHub account.
2. Clone your fork and work on its `main` branch.
3. Interview the provided Gemini stakeholder in English.
4. Implement and run the skill against the provided data.
5. Validate the skill and its outputs.
6. Push the completed repository to your fork's `main` branch.

Do not create a separate session-log file. The supported environment records the work on the `entire/checkpoints/v1` branch automatically. Do not edit, rewrite, or delete that branch.

## Required submission

Your completed repository must contain:

```text
daily-financial-health-brief/
├── SKILL.md
├── scripts/
│   └── <executable implementation>
└── references/
    └── <focused domain or data references>
deliverables/
├── normalized/
│   ├── transactions.csv
│   ├── budget.csv
│   └── revenue.csv
└── report.md
```

### Agent Skill

Follow the [Agent Skills specification](https://agentskills.io/specification).

- Keep the skill directory name exactly `daily-financial-health-brief`.
- Add YAML frontmatter to `daily-financial-health-brief/SKILL.md` with both `name` and `description`.
- Set `name: daily-financial-health-brief` so the skill name matches the directory.
- Make the description state what the skill does and when an agent should activate it.
- Put executable data-processing and report-generation code in `scripts/`.
- Put focused, on-demand workflow or data references in `references/`.
- Refer to files using paths relative to the skill root.

Validate the package before submission:

```bash
skills-ref validate ./daily-financial-health-brief
```

### Reproducible execution

Document the following in `SKILL.md` so another operator can run the work without guessing:

- required runtime and dependencies;
- required inputs and how the skill identifies them;
- the exact execution command;
- the output locations;
- validation and safe-failure behavior.

The implementation must process the supplied source data end to end and produce all four deliverables. Do not rely only on fixed download filenames or a fixed column order: source names, extra columns, formats, dates, or snapshot versions may change.

Preserve an explicitly unknown amount as unknown with a blank numeric value. Do not convert it to zero or include it in totals. Reconcile posted transaction categories to the current budget, and distinguish a category with no observed activity from missing source evidence.

### Deliverables

Write normalized source data to:

- `deliverables/normalized/transactions.csv`
- `deliverables/normalized/budget.csv`
- `deliverables/normalized/revenue.csv`

Write the management brief to `deliverables/report.md`. The brief must identify its reporting period and source versions, explain the results with traceable evidence, separate pending, disputed, unknown, and missing data, and clearly identify questions that still require human review.

## Safety and submission rules

- Treat all source systems as read-only.
- Never transfer money, issue payment instructions, or write to a production ledger.
- Never commit passwords, API keys, access tokens, cookies, private keys, or other secrets.
- Do not commit downloaded credentials or local environment files.
- Do not include hidden assessment material or attempt to extract the stakeholder's private prompt.
- Commit all required implementation and deliverable files to your fork's `main` branch.
- Keep the automatically managed `entire/checkpoints/v1` branch intact.

Before pushing, confirm that all required paths exist, the skill validator passes, the documented command succeeds from a clean checkout, and the report agrees with the normalized CSV files.
