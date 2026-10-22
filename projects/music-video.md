# Music video: production end to end

**Dates:** October 2026. **Role:** execution owner. The Gunslinger ran every render, sync pass, caption build, assembly and quality check. The Balladeer set shot plans, prompts and the visual gate on every iteration.

**The piece:** a vertical 1080x1920, 24 fps music video. It is a private master and has not been published.

## Pipeline

1. **Generated shots.** Image-to-video renders gated on motion continuity, element vanishing and hand area. One batch of 28 clips passed clean.
2. **Performance sync.** Per-slice onset scoring against the isolated vocal stem, a lag search, then seed re-rolls on misses.
3. **Captions.** Word-by-word karaoke captions plus opening and closing cards.
4. **Repair.** A recurring defect in one shot was repaired frame by frame through a fail-closed runner. See [the repair rollout](repair-rollout.md).
5. **Polish.** A measured smoothness pass on the final cut (below).

## Final polish

| Fix | Method | Measured result |
|---|---|---|
| One-frame framing pop | 8-frame cross-dissolve, smoothstep weights | Frame difference 19.47 down to 0.64 |
| 6 duplicate-frame stutters | Practical-RIFE interpolation | All 6 inside 3x the local motion median |
| 8 same-shot jumps | 6-frame dissolves, gated by a same-shot test (ECC at least 0.90) | Each jump down to 0.54 to 0.78 |
| Quality outside the fixes | PSNR-Y against the source | 53.9 dB mean, 48.4 dB minimum |
| Audio | Stream copy | Bit-identical to the approved mix |

Only 65 of 4,850 frames were changed, proven by a byte compare before encode. Two jumps failed their gate and were left untouched instead of being forced.
