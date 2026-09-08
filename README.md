# RORTEX — Clustered Multi-Motor Actuator Research

> **Status: Design and validation · Hardware performance not yet established**

RORTEX explores a clustered multi-motor actuator, combining quasi-direct-drive thinking with harmonic/cycloidal transmission research. Its current electronics baseline uses **three FOC motor-control channels and four SPI encoder interfaces**.

The owner reports that the PCB passes EasyEDA design-rule checking. Electrical, thermal, fabrication, and actuator-output validation remain open. **50 N·m peak torque is a design target, not a measured rating.**

## Contents

- [The engineering problem](#the-engineering-problem)
- [The RORTEX idea](#the-rortex-idea)
- [Current design baseline](#current-design-baseline)
- [Architecture and interfaces](#architecture-and-interfaces)
- [Engineering questions](#engineering-questions)
- [Current development status](#current-development-status)
- [Validation priorities](#validation-priorities)
- [Development roadmap](#development-roadmap)
- [Repository purpose](#repository-purpose)

## The engineering problem

A robotic actuator must balance torque, size, mass, controllability, transmission behavior, and heat. A clustered motor arrangement adds coordination and packaging questions: multiple power stages, several position signals, and a mechanical output must work together reliably.

RORTEX investigates that combined system. The project needs evidence at both the electronics level and the assembled-actuator level before its targets can become specifications.

## The RORTEX idea

Explore how a cluster of three motors, appropriate feedback, and a suitable transmission could support a compact robotic actuator. Quasi-direct-drive, harmonic, and cycloidal ideas are being investigated; they should not be read as a finalized, simultaneously implemented transmission design.

The next useful result is a clearly documented and validated baseline, followed by measured actuator behavior.

## Current design baseline

| Area | Current direction | Evidence or limitation |
|---|---|---|
| Motor control | Three FOC channels | Current architecture in the project record |
| Feedback | Four SPI encoder interfaces | Interface baseline; assignment and timing need verification |
| Controller | STM32G491RE planning | Firmware and timing validation pending |
| Low-voltage power | Shared buck converter direction | Power, noise, thermal, and layout review pending |
| PCB | EasyEDA design work | DRC pass reported by the owner |
| Mechanical system | Clustered motors and transmission research | Final mechanism and measured behavior not supplied |
| Peak output | 50 N·m target | No measured torque result supplied |

Future revisions should start from the three-FOC/four-encoder baseline. A single-channel circuit can be a test fixture, but it would not represent the complete current architecture.

## Architecture and interfaces

### Motor-control channels

Three FOC channels form the current motor-control direction. Their power stages, current sensing, timing, and protection behavior need to be reviewed together with the controller and power distribution.

### Feedback and coordination

Four SPI encoder interfaces support the feedback direction. The design needs explicit signal assignments, electrical compatibility, acquisition timing, and behavior when a measurement is invalid or unavailable. A connector count alone does not prove usable closed-loop feedback.

### Shared power

A shared buck converter is the selected low-voltage supply direction. Its load budget, startup sequence, noise coupling, grounding, and thermal behavior must be checked against the complete electronics design.

### Mechanical output

The mechanical research includes motor clustering and transmission approaches. Gear ratio, backlash, compliance, bearing loads, lubrication, efficiency, and heat affect the eventual output. None is assigned a verified performance value in this README.

## Engineering questions

1. Can the planned controller satisfy the timing and feedback requirements of all three channels?
2. Are sensing, protection, and power distribution appropriate for the complete actuator?
3. How do the shared supply and PCB layout behave under simultaneous operation?
4. Which transmission arrangement best matches the intended output requirements?
5. How much torque can the assembled actuator sustain, and for how long, within measured thermal limits?
6. What are the measured efficiency, backlash, compliance, and repeatability?

## Current development status

- [x] Clustered actuator concept and electronics direction documented.
- [x] Three FOC channels and four SPI encoder interfaces identified as the current baseline.
- [x] EasyEDA DRC pass reported.
- [x] Shared buck converter direction recorded.
- [ ] Original schematic and PCB design files uploaded here.
- [ ] Electrical, power-path, sensing, and protection review completed.
- [ ] Manufacturing checks and fabricated-board inspection recorded.
- [ ] Firmware and synchronized feedback demonstrated.
- [ ] Thermal and actuator-output tests recorded.
- [ ] 50 N·m target demonstrated under defined conditions.

A DRC pass checks configured layout rules. It does not establish electrical correctness, manufacturability, thermal adequacy, or output performance.

## Validation priorities

Begin with the source design package and a revision-specific review. Record assumptions and unresolved decisions in the same revision as the schematic and PCB. Then establish controlled board-level validation and measured feedback behavior before progressing to a combined actuator test.

For output characterization, record test conditions, instrumentation, duration, temperatures, electrical input, and uncertainty. Distinguish short-duration peak output from continuous operation. Publish measured values only when a traceable test supports them.

## Development roadmap

| Phase | Focus | Completion evidence |
|---|---|---|
| 1 — Design record | Capture the current electronic and mechanical baseline | Native files and revision notes |
| 2 — Review | Electrical, thermal, layout, and mechanical checks | Findings and resolved decisions |
| 3 — Electronics validation | Power, sensing, feedback, and channel behavior | Recorded measurements |
| 4 — Integrated control | Coordinate the three channels | Reproducible firmware and test logs |
| 5 — Actuator characterization | Torque, temperature, efficiency, and repeatability | Defined test method and measured curves |
| 6 — Revision | Improve the design using evidence | Comparison against the previous baseline |

## Repository purpose

This repository currently contains the project brief and editable `project.json`. Native EasyEDA files, Gerbers, CAD, firmware, and measured test data have not been supplied here. Proposed future folders should be added when they contain actual project materials.

## Author

**Rohan Sashank Reddy**  
[GitHub](https://github.com/Rohansashankreddy07) · [LinkedIn](https://www.linkedin.com/in/rohan-sashank-reddy-chilukuri-aa169336a/) · [Instagram](https://www.instagram.com/rohansashankreddy/)

## Maintaining this repository

Keep this README and `project.json` aligned as the project develops. Record evidence when a planned feature becomes implemented or a target becomes a measured result. Preserve the project ID so future portfolio updates can link to the same project.
