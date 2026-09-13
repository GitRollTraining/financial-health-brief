# Daily Financial Health and Budget Brief

You have joined Quillhaven Academy as an automation specialist. Interview the Finance and Operations Manager to understand how the Daily Financial Health Brief is produced and to obtain only the data needed for the work at hand.

## Get a working copy

Public starter: [GitRollTraining/financial-health-brief](https://github.com/GitRollTraining/financial-health-brief). Use a Git-enabled terminal in the supplied Agent Skills-capable coding environment:

```bash
git clone https://github.com/GitRollTraining/financial-health-brief.git
cd financial-health-brief
```

Read this README from that working-copy root. The starter supplies instructions and inputs; you create the Skill and its outputs. Keep credentials out of the repository. The facilitator supplies the supported runtime, read-only source access and assessed submission/capture route; report missing setup to that owner. The public starter is not an assigned submission destination. For a pre-S3 authoring trial, the designer selects the authorized Agent test identity, isolated workspace and test submission/capture route; no human learner or Classroom assignment is needed for that test.

**Interview rule.** You conduct the stakeholder interview yourself, and the questions are yours. Do not connect a coding agent or any other AI to the interview to run, script, or automate it. The facilitator must provide a verified interview recording/export route and associate it with you and this project before interview evidence is assessed. A missing platform record is not your performance failure. A human-assessed interview must be conducted by you; an internal authoring Agent trial is a separate test.

Build an Agent Skills-compliant skill named `daily-financial-health-brief`. Another operator must be able to use it to fetch the current data directly from the three disclosed Google Sheets URLs on every invocation, inspect the source schemas, normalize the three financial datasets, validate the inputs, and produce a traceable management brief without editing a source system or performing a financial action.

Your automation—not the stakeholder—must supply the implementation knowledge needed to make this efficient, reliable, reproducible, and safe. Design one programmatic end-to-end run, validate before producing usable outputs, preserve signed credits and unknown states, support deterministic reruns, and avoid manual per-row processing or hard-coded expected answers.

Your repository must contain:

- `daily-financial-health-brief/SKILL.md` with valid `name` and `description` frontmatter;
- an executable implementation under `daily-financial-health-brief/scripts/`;
- focused operating knowledge under `daily-financial-health-brief/references/`;
- `deliverables/normalized/transactions.csv`;
- `deliverables/normalized/budget.csv`;
- `deliverables/normalized/revenue.csv`; and
- `deliverables/report.md`.

The normalized CSV contracts are:

- `transactions.csv`: `transaction_id`, `date`, `account`, `category`, `description`, `amount`, `currency`, `status`, `source`, `source_version`, `amount_status`;
- `budget.csv`: `period`, `category`, `budget_amount`, `currency`, `owner`, `review_rule`, `source`, `source_version`; and
- `revenue.csv`: `date`, `source`, `metric`, `value`, `currency`, `source_version`.

Preserve every recognized source row. Use exactly the disclosed normalized columns. Unrelated extra source columns need not appear there; preserve additional meaningful source information in source-linked report notes rather than silently dropping it or changing the public CSV shape. A source change that alters required business meaning needs clarification and a refreshed assessment basis.

Use relative paths from the skill root, keep secrets out of the repository, and preserve the Entire branch created during your work. Treat the disclosed Google Sheets URLs as runtime inputs: each run must perform a fresh read of all three viewer-only Sheets rather than use a bundled, manually downloaded, or previously cached CSV as its primary input. Before outputs are published, print each source URL or spreadsheet identity, sheet/tab identity, fetch timestamp, source version, and fetched row count so the existing Entire transcript captures the evidence; record the same metadata in `report.md`. If a Sheet cannot be fetched or validated, fail safely instead of silently reusing an older local copy. Challenge A assessment uses the current fixed source versions, but the implementation must still identify source roles from field meaning rather than hard-code filenames, column positions, or expected answer values. If a required source is invalid or unavailable, fail safely and identify the needed clarification. A valid source that lacks a required comparison-date record may support other conclusions: explicitly withhold the missing comparison and identify its owner. Valid explicit unknown pending/disputed amounts are supported business states: retain them as unresolved, omit only their numeric contribution, and continue conclusions supported by the remaining valid evidence.

Preserve explicit unknown amounts as unknown with a blank numeric value; never convert them to zero or include them in totals. Preserve confirmed negative posted credits or corrections with their sign. Reconcile posted transaction categories to the current budget, distinguish a category with no observed activity from missing source evidence, and retain current-month unresolved items even when they predate the report day.

Interview entry: [Finance and Operations Manager](https://work-sim-alpha.catalyte.ai/s/interview-r62mbg). The facilitator must confirm the current scenario version and the recording/submission route before the assessed interview.

## Reporting commission and completion states

The current business request is for the Aug 12, 2026 operations meeting: reporting date Aug 11, comparison Aug 10 and August budget. Confirm it through the stakeholder. All three Sheets remain runtime inputs; wall-clock retrieval time is recorded separately. A reusable implementation accepts reporting context explicitly rather than embedding expected answers.

A complete submission hands over a supported draft, not a financial decision. Report current/prior daily posted totals and signed change; keep current daily pending/disputed confirmed amounts separate; reconcile each budget category's MTD spend, budget, signed variance and materiality; compare collected revenue and outstanding balances; retain the complete current-month unresolved queue. Show context, source versions and limitations with sufficient evidence for the manager to review. Required business meanings and thresholds are available through the stakeholder, without a secret question.

- Supported: all required sources are valid; all four named files exist and agree. Draft status and human decision ownership remain visible.
- Supported with unresolved business items: valid explicit unknowns, disputed/pending items an identified unmapped category or an unavailable comparator in an otherwise valid source are shown with affected scope and owner. Do not invent missing values or complete unsupported comparisons. All four artifacts still expose the available evidence and limits.
- Failed input or output validation: return a nonzero status and a diagnostic naming affected source/field/identity and necessary repair. Do not claim current success or leave earlier deliverables masquerading as current. Remove, invalidate or visibly mark the prior bundle stale; preserve authentic run evidence. The diagnostic/session record is the valid failure evidence; normal result files must not be claimed current.
- Retry or changed input: fetch all three sources again. Confirm every required artifact actually exists, matches this run and is consistent before reporting success, even if inputs are unchanged. Rebuild missing/corrupted derived outputs or fail explicitly; do not fabricate lost past observations.

Validate duplicate semantic identities, coherent versions (ledger, budget period, revenue date), dates, monetary types/currency, state vocabulary and conditional blank amounts before using them. Signed decimals and reordered rows/columns must retain business meaning. Never include pending/disputed or unknown values in confirmed posted totals.

## Given, authored and submitted

The starter provides this README with the commission and interview entry. Use the facilitator-provided workspace/runtime and capture instructions; obtain the view-only business sources and their meanings through the interview. The starter does not provide a solved Skill, teacher fixtures, reference answer or private prompt.

Implement and document one end-to-end command of your choice; state runtime/dependencies, URL roles, reporting context, outputs and declared failure status. The empty starter is not a working financial pipeline. The facilitator must verify advertised environment, source access, interview identity/export and Entire capture before an assessed run. Do not install unrequested infrastructure or share credentials to compensate for missing setup.

Submit the Skill and four required artifact paths in your repository at one identified revision, plus the facilitator-bound interview record and genuine coding-session evidence where available. Preserve the Entire branch created during work. Record source/tool actions truthfully; a written claim or snapshot cannot replace an actual execution record. If interview/capture support is unavailable, report that setup issue rather than inventing a transcript. A manager review correction returns to the relevant input/calculation; financial approvals and external actions stay outside the task.
