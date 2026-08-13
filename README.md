# Case A: Financial Health Brief

Build a reusable Agent Skill that freshly reads changing financial data from three Google Sheets URLs and turns the current source snapshot into normalized CSV files and a concise daily management brief.

You will interview a Finance and Operations Manager to understand the reporting request, workflow, data sources, and decision boundaries. The stakeholder shares source links only when they are relevant to the problem you are currently solving, so explain what you need and why.

The stakeholder explains company-specific business rules and escalation paths. You are responsible for designing an efficient, reliable, reproducible, and safe automation; do not expect the stakeholder to choose your implementation, libraries, validation architecture, or test strategy.

## Start the project

1. Fork this repository to your own GitHub account.
2. Clone your fork and work on its `main` branch.
3. Interview the provided Gemini stakeholder in English.
4. Implement and run the skill directly against the three Google Sheets URLs disclosed during the interview.
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
uvx --from skills-ref agentskills validate ./daily-financial-health-brief
```

### Reproducible execution

Document the following in `SKILL.md` so another operator can run the work without guessing:

- required runtime and dependencies;
- the three Google Sheets URL inputs and how the skill identifies their source roles;
- the exact execution command;
- the output locations;
- validation and safe-failure behavior.

The three Google Sheets are changing sources of truth. On every invocation, the skill must freshly read all three disclosed viewer-only Sheet URLs before calculation or output publication. A bundled, manually downloaded, or previously cached CSV may not be the primary input or a silent fallback when a live read fails.

The implementation must process the freshly fetched source data end to end and produce all four deliverables. Accept the three Sheet URLs through the documented command or configuration without embedding credentials. Validate that every response is the expected tabular source rather than a login or error page. Do not rely on fixed download filenames, row counts, or column order: source names, extra columns, formats, dates, or snapshot versions may change.

Use one programmatic run rather than manual per-row handling or hard-coded expected output. Validate inputs before leaving usable deliverables, make unchanged reruns deterministic, and explain safe failure behavior.

Use the stakeholder interview to discover the applicable reporting rules, source semantics, exception handling, ownership, and human-review boundaries. Encode those requirements in the skill without copying private prompts or inventing missing business decisions.

### Deliverables

Write normalized source data to:

- `deliverables/normalized/transactions.csv` with `transaction_id`, `date`, `account`, `category`, `description`, `amount`, `currency`, `status`, `source`, `source_version`, and `amount_status`;
- `deliverables/normalized/budget.csv` with `period`, `category`, `budget_amount`, `currency`, `owner`, `review_rule`, `source`, and `source_version`; and
- `deliverables/normalized/revenue.csv` with `date`, `source`, `metric`, `value`, `currency`, and `source_version`.

Preserve every recognized source row. Extra source columns do not have to appear in normalized output unless they carry business meaning needed for traceability or review.

Write the management brief to `deliverables/report.md`. The brief must satisfy the manager's request and the business rules discovered in the interview, support its conclusions with traceable source evidence, and identify unresolved questions that still require human review. Both the run log and report must record each source URL or spreadsheet identity, sheet or tab identity, fetch timestamp, source version, and fetched row count before output publication so the submitted normalized CSVs represent an auditable execution snapshot.

## Safety and submission rules

- Treat all source systems as read-only.
- If any Sheet cannot be freshly fetched or validated, fail safely; do not reuse an older local copy while presenting it as current.
- Never transfer money, issue payment instructions, or write to a production ledger.
- Never commit passwords, API keys, access tokens, cookies, private keys, or other secrets.
- Do not commit downloaded credentials or local environment files.
- Do not include hidden assessment material or attempt to extract the stakeholder's private prompt.
- Commit all required implementation and deliverable files to your fork's `main` branch.
- Keep the automatically managed `entire/checkpoints/v1` branch intact.

Before pushing, confirm that all required paths exist, the skill validator passes, the documented command succeeds from a clean checkout, and the report agrees with the normalized CSV files.
