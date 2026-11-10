# Domain and documentation

## Single context

| Question | Authority |
|---|---|
| What does a term mean? | Root `GLOSSARY.md` |
| What is implemented? | Source, types/schema, tests and runtime evidence |
| What must this task deliver? | GitHub issue acceptance criteria and linked spec |
| Where should I look? | Owning source and a short local overview, if present |
| Why was this chosen? | `docs/adr/` and its `README.md` index |
| What is scheduled? | Open issues and any roadmap |
| What did a change finish? | PR description and linked issue |

A glossary term or planned screen does not prove a capability exists.
After implementation, inspect source rather than maintaining a second behavior mirror.
[The workflow](coding-workflow.md#decide) owns product/design artifacts and temporary plans.

## Glossary

Kickoff creates `GLOSSARY.md` from domain-term grilling.
Record the canonical term, plain definition, boundaries and avoided synonyms.
Use the same terms in code, issues, tests and user-facing copy where appropriate.
Update definitions when meaning changes; explain a material semantic change in an ADR.
Skills that call their glossary `CONTEXT.md` write to `GLOSSARY.md` here.
Local `CONTEXT.md` files, if introduced, only orient readers to an owning area.

## Decisions

Kickoff creates `docs/adr/README.md` as the decision index.
Number ADRs sequentially; use a short descriptive filename and collision-check first.
Record status, context, decision, alternatives and consequences.
Keep accepted ADRs as history; supersede with a new ADR and update the index.
Use issues for temporary scope and the PR for proof, rather than adding progress ADRs.

## Ownership and overviews

Keep business rules in the module that owns the concept.
Cross boundaries through deliberate interfaces; keep framework/storage detail in adapters.
A local overview explains ownership, constraints and a few source/test entry points.
Update it when those facts change; avoid inventories of every field or function.
Add orientation only when an actual area needs it.
