# Archive

`journal-until-20261006/` is the whole `journal/` folder as it stood on
2026-10-06 (commit 738e950), the paper-trading record inherited from the
upstream bennyjo/phil fork. It was moved here so this fork's own experiment
starts from an empty ledger, which `core/ledger.py` reads as the full
`sim_bankroll_usd` ($1,000 in `config/protected.json`).

Nothing in `core/` or the cycle reads this folder. It is kept for reference.
