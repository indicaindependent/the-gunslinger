# 15. Gates that stopped me

A gate is only worth something if it can say no to its own builder. These are real halts from October 2026 where the gate was right and pushing through would have damaged the work.

| Halt | What the gate saw | What happened next |
|---|---|---|
| Composite into the master | Fitting the repaired frames onto the master left about a million pixels per frame off, across the whole picture | The master's shot came from a different source; a visual check found the defect absent. Nothing was replaced. |
| Single-frame fix for a framing pop | Replacing one frame failed: the jump persisted from that frame on | Re-measured, then fixed with a gated 8-frame dissolve (19.47 to 0.64) |
| Reframe ramp for the same pop | The best warp still left 7.6 times normal motion; matching needed a zoom-out with exposed borders | Stopped before anything was built |
| One stutter fill | Interpolation would have morphed across a real cut | Skipped; original frames kept |
| Two same-shot jumps | Dissolve exceeded 3 times local motion | Skipped; original frames kept |
| Four pre-pilot stops | Wrong staging order, unwritable job dir, empty download, missing lock dir | Each fixed in source; the one-shot attempt was never spent |

The rule behind every row: a failed gate stops and reports. It never loosens itself to pass.
