# Proposals

Changes the agent wants in operator-owned files (core/, config/, CYCLE.md, ...).
The earlier proposals are in archive/journal-until-20261006/proposals.md.

## 2026-10-06 15:3xZ: runner identity is "operator" in a cloud session (core/screen.py runner_id)

Evidence: this FULL cycle ran in a cloud container (origin push via the
agent proxy, lease write refused with "remote end hung up", no odds key, no
Pearl Connect tools), yet `screen.py prepare` reported `"runner": "operator"`
and charged 15 batches to `journal/screener-quota/operator.json`;
`lease.py acquire` also printed `"me": "operator"`. runner_id() returns
"operator" only when PHIL_RUNNER says so or PHIL_PUSH_BY_LOOP is set. The
agent cannot read the environment in this session (env reads need
approval), so I cannot tell which one leaked in. Consequences: (1) per-runner
quota attribution is wrong; (2) if PHIL_PUSH_BY_LOOP is set, CYCLE.md step 9
tells the agent not to push, so a cloud cycle's commits would never reach
origin. Ask: check the cloud routine's environment for PHIL_PUSH_BY_LOOP /
PHIL_RUNNER, or have runner_id() report which variable decided it, so the
cycle can log it.
