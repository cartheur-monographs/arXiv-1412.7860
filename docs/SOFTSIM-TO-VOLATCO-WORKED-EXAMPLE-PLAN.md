# SOFTSIM To Volatco Worked Example Plan

Date: `July 26, 2026`

## Purpose

This note defines a practical implementation path for the paper's worked
computational example:

1. functional validation in `SOFTSIM`
2. later realization on a native GA144-based `Volatco` board

The goal is to give the paper a concrete computational witness without
pretending that the manuscript already includes full hardware proof.

## Why this example matters

The paper is stronger when it can show at least one compact mapping from:

- geometric partition
- local address
- state-bearing region
- adjacency relation
- supervisory or reactive update

to an executable computational pattern.

This worked example is intended to do exactly that.

## Example concept

The minimal example is a two-node distributed behavior:

- `node 000`: reactive local node
- `node 001`: supervisory token node

The intended semantics are:

- a bounded local partition corresponds to a small reactive state space
- a local address corresponds to a retraceable state slot or mode slot
- a neighboring relation corresponds to a permitted path for a supervisory
  update
- the supervisory node periodically emits a token
- the reactive node changes local mode or count behavior when that token
  arrives

This gives a simple but concrete bridge from the paper's geometric language to
distributed embedded execution.

## Paper-level mapping

The paper should describe the example in these terms:

- partition -> bounded local state region
- address -> known slot inside that region
- adjacency -> permitted control/update path
- token arrival -> local mode transition
- local iteration -> bounded execution inside one finite region

That is enough to illustrate the substrate claim without implying a full
runtime or general-purpose operating system.

## Stage 1: SOFTSIM functional validation

### Goal

Demonstrate the logic of the example in `SOFTSIM` as a functional witness.

### Why SOFTSIM first

`SOFTSIM` is the right first stage because it supports:

- logical validation of node-level behavior
- repeatable inspection of node memory and state
- confirmation that a supervisory token changes a reactive node's visible mode

It should not be treated as a timing-accurate proof of final hardware behavior.

### Expected result

The first result we want is:

- a simulated two-node program where `node 001` changes `node 000` mode
- visible local markers showing state change
- a traceable explanation of how that behavior corresponds to the paper's
  partition/address/control interpretation

### Existing local support material

Relevant local sources already exist in:

- `/home/cartheur/ame/aiventure/aiventure-github/monographs/behavior-hybrid-substrate/SOFTSIM/README.md`
- `/home/cartheur/ame/aiventure/aiventure-github/monographs/behavior-hybrid-substrate/SOFTSIM/behavior-softsim-ga144-summary.md`
- `/home/cartheur/ame/aiventure/aiventure-github/monographs/behavior-hybrid-substrate/SOFTSIM/softsim-programming-sequence.md`

### Practical outputs for Stage 1

1. a tiny node-level source example
2. a matching BDL or boot-frame loading sequence
3. a short execution log
4. screenshots or textual traces of state change
5. one small figure for the paper or a companion note

## Stage 2: Native GA144 / Volatco-board realization

### Goal

Move the same functional example onto a native hardware board so the logical
witness becomes a hardware witness.

### Why this matters

This stage is where the following questions can be tested more honestly:

- real asynchronous timing
- contention behavior
- node coordination on actual hardware
- power-use characteristics
- I/O realism and operational limits

### Role of Volatco

In this workflow, `Volatco` is not the paper's product story. It is the
candidate native GA144-based board context on which the substrate example can
be realized physically.

That distinction should remain explicit:

- paper claim -> conceptual and architectural
- SOFTSIM -> functional witness
- Volatco hardware -> physical realization path

### Practical outputs for Stage 2

1. a board-loading procedure
2. node placement and boot initialization notes
3. a minimal run log on real hardware
4. timing and power observations
5. a short hardware realization appendix or companion note

## Recommended manuscript use

The paper should not try to include the full implementation workflow in detail.
Instead, it should:

- include a short worked-example subsection
- state that the example can be validated first in `SOFTSIM`
- state that native hardware evaluation remains the second-stage realization
  path

That keeps the manuscript honest while still making it more concrete.

## Recommended next actions

1. Write the tiny two-node example in simulator-oriented form.
2. Record the exact `SOFTSIM` run sequence and outputs.
3. Add one paper-safe figure or table summarizing the example.
4. Port the same example to the native GA144 board path.
5. Decide whether the hardware result belongs in this paper or a companion
   implementation note.
