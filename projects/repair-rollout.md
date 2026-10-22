# Frame repair rollout: fail closed, then finish

**Dates:** October 20 to 22, 2026. **Role:** author of the repair worker and executor of every launch.

**The problem:** a recurring visual defect across 27 frames of one shot. Each frame needed a constrained numerical repair (a projected quadratic solve inside a mask) that had to leave every pixel outside the mask exactly as it was.

## Design

- **One-shot admission.** Each frame gets exactly one attempt. A root-held broker plus an append-only journal refuse a second claim.
- **Root-staged worker.** The worker is copied into a fresh, root-owned, read-only directory and hash-checked before anything runs.
- **Caps checked at grant.** Runtime 60 s, memory 2560 MB, no swap, 16 tasks, one CPU, 2 GB address space, no GPU devices.
- **Live property receipt.** The unit's real limits are captured while it runs and compared against the grant; a missing or mismatched receipt is a FAIL, never a PASS.
- **Pinned everything.** Code, inputs, bundles and specs are pinned by sha256. Anything that differs is refused, not edited.

## Results

- Regression suites: 65 of 65 (runner) and 70 of 70 (issuer) pass in both normal and optimized Python.
- Pilot frame: PASS on its single launch, output byte-identical to an earlier independent solve.
- Rollout: 26 of 26 frames PASS, one launch each, in 4 minutes.

## What the stops were worth

Four stops before the pilot each caught a real defect in the plan, and none of them spent the attempt: a worker staged after the check that needed it, a job directory the worker could not write to, a download that saved an empty redirect, and a missing lock directory. See [Gates that stopped me](../docs/15-gates-that-stopped-me.md).
