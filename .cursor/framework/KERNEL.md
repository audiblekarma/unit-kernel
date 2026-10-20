# Unit Kernel v1.0

A portable operating kernel. Hierarchical text: `HIERARCHY.txt`. Growth map: `GROWTH.txt`. Another system gets the same kernel, a new Purpose Pack, and the portable rows of the Field Ledger and Growth Map.

It is specialized to one person's purpose, and usable in any situation that person meets. Specialization lives in Purpose Pack and in ledger rows. The kernel does not change per project.

```
Unit Kernel
├── Dispatch     Feature Registry, Unit Map
├── Kernel       Unit Kernel (this document)
├── Record       Field Ledger, Growth Map
├── Purpose      Purpose Pack
├── Protocol     situation units (this template: Settle Prompt)
└── Mark         Voice Mark, Read Ease
```

## Research used

- Architecture Decision Records: keep **fact**, **interpretation**, and **decision** apart. Append-only. Do not rewrite an accepted row. Supersede it. One event per row. Short and dated ([ADR](https://www.martinfowler.com/bliki/ArchitectureDecisionRecord.html), [Azure WAF](https://learn.microsoft.com/en-us/azure/well-architected/architect-role/architecture-decision-record)).
- Progressive disclosure: keep a short index in context; open the body only on a match. Eager-loading every spec raises cost as the library grows; disclosure has been measured up to **81.7%** fewer tokens versus eager load. **One** routing level is enough; a deeper tree can hurt accuracy ([arXiv:2609.35692](https://arxiv.org/html/2609.35692), [arXiv:2607.17598](https://arxiv.org/html/2607.17598)).
- Portable personal context: files outlive tools. General kernel, cascading purpose, ledger of evidence ([PCP](https://github.com/milesgoscha/personalcontextprotocol), [KCP](https://cantara.github.io/knowledge-context-protocol/), [Human Kernel](https://humankernel.org/)).

This kernel already had Map → Draw. Ledger, Growth Map, and Purpose Pack complete the portable shape.

## Files that move

| File | Stays on port | Role |
| --- | --- | --- |
| `map.json` | schema and kernel units | cheap index |
| `ledger/index.json` + `ledger/log.jsonl` | rows with `portable: true` | evidence |
| `growth/index.json` + `growth/log.jsonl` | rows with `portable: true` | lineage |
| `purpose.json` | **replaced** | this system's aim |

Copy steps: `PORT.md`.

## Unit

The minimal requirement (locked line, do not rewrite when listing):

`「{Name vX.Y}」は、{when}のときだけ引き出します（{note}）。`

Open `spec` only after `when` matches. That is the cost cut.

## Layer

One level under the framework. Match **layer `when` first**, then units. Do not add a fourth nesting.

## Field Ledger

Every discussion that produces a fact, an experiment, a success, a failure, or an insight appends **one** row. Do not dump the log in chat. Do not rewrite a row. If the decision changes, append a new row that supersedes the old id.

| `kind` | Meaning |
| --- | --- |
| `fact` | Observed. Not interpreted. |
| `experiment` | Tried X, saw Y. |
| `success` | A form or act the user accepted. |
| `failure` | A form or act the user rejected, or a break. |
| `insight` | Interpretation. Never stored as if it were a fact. |

Each row: `id`, `at`, `kind`, `when`, `fact`, optional `insight`, optional `decision`, `unit`, `portable`, `source`.

Dispatch reads `ledger/index.json` (id, kind, when, portable). Opens the matching line in `log.jsonl` only when `when` matches the current situation.

## Growth Map

A unit grows in small steps. Map: `GROWTH.txt`. Index: `growth/index.json`. Process: `growth/log.jsonl`. Kinds: seed, born, lock, bump, reject, split, settle, store. Do not mix with Field Ledger. Do not invent a step. Do not rewrite a row.

## Purpose Pack

`purpose.json` states **this** system's aim. The kernel stays general. Swap the pack to transplant. Protocol units that name a previous system stay with that pack, not with the kernel.

## Related and contradiction

`related` is the compose graph (drawn together when their `when` matches).
`contradictions` is the exclude graph: two units, a `when`, a `prefer`. After the match, keep `prefer`, drop the other, do not open its spec.
`forbids` is one unit against a rejected act of its own.

A known conflict that is not in `map.json` is an unmapped failure. Map it.

Contradiction line (do not rewrite when listing):

`「{A}」と「{B}」は、{when}ときは両立しません（{note}）。`

## Draw

1. Read `map.json`.
2. Match layer, then unit.
3. Apply contradictions and forbids.
4. Scan `ledger/index.json`; open matching log lines only.
5. Scan `growth/index.json`; open matching growth lines only.
6. Open remaining `spec` files. Copy unit `line` when listing.
7. If this turn produced a ledger kind, append one accurate row. If a unit grew, append one growth row.
8. Close the rest.
