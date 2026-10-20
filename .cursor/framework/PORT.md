# Port

Copy Unit Kernel to another system this person uses. The settled tree is `HIERARCHY.txt`. Do not rewrite ledger rows. Do not take purpose-only units unless that system needs them.

1. Copy `.cursor/framework/KERNEL.md`, `PORT.md`, `map.json` schema, `ledger/` schema, `growth/` schema, `GROWTH.txt`, and the specs for Feature Registry, Unit Map, Unit Kernel, Field Ledger, Growth Map, Purpose Pack, Settle Prompt, Voice Mark, Read Ease.
2. Replace `purpose.json` with that system's aim.
3. Copy ledger rows and growth rows where `portable` is true. Leave `portable: false` rows behind.
4. Drop or replace Protocol units that name the old system.
5. Point `map.json` `framework.name` at the new instance. Keep kernel unit versions unless you bump them.
6. Announce `Unit Kernel v1.0`.
