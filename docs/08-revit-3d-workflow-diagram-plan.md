# 08 — Revit 3D Workflow Diagram Plan (Phase 2)

## What this topic means

This is a **plan**, not a built feature. It describes a future goal: recreating the BIM coordination workflow as a **3D teaching diagram inside Revit**, so the workflow can be explored spatially rather than only read as text or a flat Mermaid chart.

The 3D model will be built later using the **Revit MCP server**.

## Why it matters

A flowchart shows *order*. A 3D model shows *structure and relationships* — discipline streams flowing into a central federated model, looping through issue resolution, and moving out to construction and handover. For workshops and Triviron presentations, a navigable 3D diagram is far more memorable than a flat image, and it doubles as a demonstration of Revit MCP automation.

## Where it fits in the workflow

This corresponds to **Phase 4** of the roadmap (see `PRD.md`). It depends on:
- the workflow narrative being settled (Phases 1–2 docs), and
- the Revit MCP server being available for automated placement.

## Planned model contents

The Revit model should include:

**Colored discipline streams** (each a distinct color):
- Architecture block
- Structure block
- Mechanical block
- Electrical block
- Plumbing block
- Fire protection block
- Civil / site block

**Central coordination structure:**
- Central **federated model** block (where streams converge)
- **Forma Model Coordination** zone
- **Navisworks** coordination zone
- **Issue resolution loop** (feedback from coordination back to disciplines)

**Downstream:**
- **Construction** zone
- **Owner handover** zone

**Annotation:**
- **Numbered callouts** matching the workflow steps in the README, so the 3D model and the written explanation stay in sync.

## Typical tools involved

- **Revit** — host for the 3D diagram.
- **Revit MCP server** (pyRevit-based) — programmatic placement of blocks, colors, zones, and callouts.
- This repo — the source narrative the model must match.

## Simple example

A presenter opens the Revit model in a workshop. Seven colored streams (one per discipline) flow toward a glowing **central federated block**. Numbered callout **8** sits on the **clash detection** zone; a looping arrow (callout **10**) returns from issue resolution back to the discipline streams. The presenter walks the room through the same numbers used in the README — first in text, then in 3D.

## Build notes (for later)

- Keep block naming and callout numbers identical to the README stages.
- Use one consistent color per discipline across all CogStack material.
- Generate via Revit MCP so the model is reproducible, not hand-placed.
- Treat the simplified Mermaid diagram as the canonical layout reference.

---

*Status: planned. Nothing in this document is built yet.*
