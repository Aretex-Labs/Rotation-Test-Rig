# Rotation-Test-Rig

An open source, buildable rig for testing the rotational accuracy of orientation sensors (IMUs, inclinometers, etc.) against known, commanded rotation.

**Status: early / not yet buildable.** Nothing really yet. See [Roadmap](#roadmap) below for what's done and what's planned.

## Why this exists

Characterizing an orientation sensor's real-world accuracy means comparing its output against a known ground-truth rotation. That instrument exists commercially (rate tables, positioning tables) but usually costs low five figures and up, and there's no single open source project that assembles the pieces into something buildable at hobbyist scale. This project is that assembly.

## How it works

- **v1.0 (current target):** one precision motorized axis plus a manually-indexed fixture for the other two: you drive one axis under closed-loop control and re-clock the fixture by hand to test the other two axes at fixed, known angles. Simpler and more accurate than a coupled multi-axis gimbal, and the standard approach used in real IMU calibration labs.
- **v2.0 (later):** a full three-axis gimbal with all three axes driven simultaneously, for dynamic multi-axis motion.
- **Actuation:** serial-bus smart servos with a built-in magnetic encoder (e.g., FEETECH STS3215), daisy-chained over a single USB-to-TTL adapter. Control runs via CLI.
- **(future) Ground truth:** never trust the servo's own encoder alone. A second, independently-wired encoder plus an optical cross-check (camera + ArUco/ChArUco target + OpenCV pose estimation) verify the commanded angle was actually reached.

## Roadmap

| Phase | Scope | Status |
|---|---|---|
| 0 — Scaffold | Repo structure, README, licenses, roadmap | In progress |
| 1 — Single axis | Motorized axis built and moving under closed-loop control | Not started |
| 2 — Manual-index fixture | Two-axis pinned index bracket; all three axes individually testable | Not started |
| 3 — v1.0 | BOM, assembly guide, calibration procedure, worked test example; measured accuracy documented | Not started |
| 4 — v1.x Verification layer | Independent encoder + optical cross-check live; backlash/repeatability characterized | Not started |
| 5+ — v2.0 | Full simultaneous 3-DOF gimbal | Not started |

## Repo layout

```
/hardware   CAD, STL, BOM
/software   host-side CLI control + logging scripts
/docs       assembly guide, calibration procedure, test protocols
/results    example runs, measured accuracy data
```

## License

- Everything under `/hardware`: [CERN-OHL-W](https://ohwr.org/cern_ohl_w_v2.txt)
- Everything under `/firmware` and `/software`: MIT

See `LICENSE` (software) and `LICENSE-HARDWARE` (hardware) for full text.

## Contributing

Not much to contribute to yet — check the roadmap above for what's actually in progress. Issues and discussion are welcome.
