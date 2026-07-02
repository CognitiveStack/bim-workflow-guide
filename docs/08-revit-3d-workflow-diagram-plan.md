# 08 — Revit 3D Workflow Diagram: Build Runbook

> This repo holds the **instructions and documentation**. The Revit model itself is **not** stored here — it lives in the Autodesk project area (see below) and is built via the pyRevit MCP server.

## What this is

A step-by-step runbook for recreating the BIM coordination workflow as a **3D teaching diagram in Revit**, built programmatically through the **pyRevit MCP server** (`revit-triviron`). The 3D model is the first module (`Module_00`) in a BIM Coordination Workflow Atlas.

It is a **modernized** retelling of a well-known 2019 contractor coordination infographic (Turner / White Plains Hospital) — with that contractor/project branding removed — updated to current Autodesk Forma / Construction Cloud terminology and a cloud-first (CDE-centric) mental model. Autodesk product names are kept intentionally: the cloud drivers (Design Collaboration, Model Coordination) are Autodesk Forma products, while open standards such as IFC (e.g. Tekla) still interoperate.

A flowchart shows *order*; the 3D model shows *structure and relationships* — discipline streams flowing through a shared Common Data Environment into a central federated model, looping through issue resolution, and moving out to construction and handover.

## Where the files live

| Artifact | Location |
|---|---|
| **Build instructions & docs** (this file) | This repo |
| **Build prompt** (paste into Claude Desktop) | `docs/08-revit-build-prompt.md` |
| **Revit model (`.rvt`)** | `C:\Users\charles\Documents\Autodesk\projects\bim-coordination-workflow-atlas\rvt\current\BIM_Coordination_Workflow_Atlas_Module_00.rvt` |
| **Reference images** | `C:\Users\charles\Documents\Autodesk\projects\bim-clash-visual-atlas\images\revit-kid-bim-workflow-diag\` |
| **Exported view images** | Re-imported into this repo under `diagrams/` once captured |

## Modernized terminology (contractor-neutral)

This is the canonical term list. Keep it consistent across the model and the docs.

| Original (2019) | Modernized term used here |
|---|---|
| "Turner" ribbon ⑤ | **Common Data Environment** (the cloud backbone / spine) |
| GC / Construction Manager carrying models | A *legacy* role flow — explained in docs, not drawn as the spine |
| "Consolidated Model (Navisworks / IFC)" ⑧ | **Federated Model** (a.k.a. Consolidated Model) |
| "3D Design Model" ③ | **Coordinated Design Model** |
| "Source Models" ⑩ | **Discipline Models** |
| "Revit, Tekla, CAD, etc…" | **Authoring Tools (Revit, Civil 3D, …)** |
| coordination / clash step | **Model Coordination** (cloud) *or* **Navisworks Manage** (desktop) |
| design model exchange | **Design Collaboration** |
| "Design Changes" loop 8.2 | **Design Change Loop** |
| "Shop Drawing / Model Changes" loop 8.1 | **Issue & Update Loop** |
| project name / brand / date | removed |

### Disciplines (7 streams)

Architectural, Structural, Mechanical, Electrical, Plumbing, Fire Protection, Civil.
*(Landscape and Penthouse dropped.)*

### Discipline colors (keep consistent across all Atlas modules)

| Discipline | Color |
|---|---|
| Architectural | Tan / gold |
| Structural | Violet / light purple |
| Mechanical | Orange |
| Electrical | Yellow |
| Plumbing | Cyan / light blue |
| Fire Protection | Red |
| Civil | Green |
| **CDE backbone** | **Strong blue** |
| Federated Model stack | all seven discipline colors together |

> The CDE backbone takes the strong blue so no discipline uses blue (avoids confusion with the spine).

## The CDE backbone concept (callout ⑤)

In the 2019 original, a single contractor "carried" models from design into construction coordination. In a modern Forma workflow there is no single party carrying models — **everything publishes to and pulls from the cloud**. So callout ⑤ becomes the **Common Data Environment**: a strong-blue spine running through the middle of the diagram, with **Design Collaboration** and **Model Coordination** sitting *on* it. A small **BIM Coordinator** role-marker sits near the Federated Model (the human stays, the platform is the star).

The older **General Contractor / Construction Manager**-led flow is still common in practice; it is explained in the docs referenced at ⑤ rather than drawn as the backbone.

## Prerequisites

- Revit is open with the **pyRevit MCP server** connected.
- The MCP exposes (at minimum): `get_revit_status`, `get_revit_model_info`, `list_levels`, `list_views`, `place_family`, `execute_revit_code`, `get_revit_view` / `list_revit_views`, `color_splash` / `clear_colors`.
- Driven from either a Claude Desktop session (better for pasting reference images and iterating visually) or Claude Code — both can reach the same MCP.

## Build sequence

Run in order; save + screenshot after each milestone.

### 1. Verify connection and active document
- `get_revit_status` → confirm Revit is responding.
- `get_revit_model_info` → confirm the active document.
- If none suitable, create a new project from a generic metric template, then save to the canonical path before continuing.

### 2. Units and levels
- Set units to **millimetres**.
- Create a single level **"Workflow"** if needed.

### 3. Geometry layout (left → right along +X; streams along Y; stacking +Z)

**Zones** (with 3D model-text labels above each): **DESIGN** (X 0–8000), **CONSTRUCTION** (X 8000–20000), **OPERATION** (X 20000–28000).

**DESIGN zone:**
- 7 colored input streams entering from the left, stacked along Y, each ending in a +X arrowhead, labeled: Architectural, Structural, Mechanical, Electrical, Plumbing, Fire Protection, Civil.
- A **Coordinated Design Model** cluster (callouts ① ③) where streams converge (~X 6000).

**CDE backbone (callout ⑤):**
- A **strong-blue spine** running ~X 7000 → 20000 through the middle, labeled **"Common Data Environment"**.
- **Design Collaboration** marker on the design side of the spine; **Model Coordination** marker near the Federated Model. Note Navisworks Manage as an alternative on the Model Coordination marker.

**CONSTRUCTION zone:**
- Steel / penetrations branch (callouts 4.1 underground coordination, 4.2 penetrations & fabrication).
- Trade model inputs feeding up onto the spine (callouts 6, 7).
- Central **Federated Model** block (callout ⑧): a tall stack of all seven discipline colors at ~X 18000, labeled "Federated Model (Model Coordination / Navisworks)".
- Small **BIM Coordinator** role-marker beside it.

**OPERATION zone:**
- 3×3 grid of small **Discipline Models** cubes (callout ⑩).
- Assembled **Federated Model** block (callout ⑨, ~X 24000).

**Feedback loops (dashed):**
- Top: **Design Change Loop** (8.2) — federation back to DESIGN.
- Bottom: **Issue & Update Loop** (8.1) — operation back to the trade models.

### 4. Numbered callouts
Place markers for: 1, 2, 3, 4.1, 4.2, 5, 6, 7, 8, 8.1, 8.2, 9, 10 — positions matching the reference. Numbers must match the written workflow docs.

### 5. Views, sheet, labels
- A default 3D view + a key isometric framing the whole diagram.
- One presentation sheet with the views, a title block, a discipline color legend, and the callout key.

### 6. Save and export
- Save the `.rvt` to the canonical path.
- Capture views with `get_revit_view`, export images, re-import into this repo's `diagrams/`.

## How this connects back to the repo

- The **exported Revit images** are the primary workflow illustration, embedded in the README and in `docs/workflow-overview.md`.
- Keep block names, colors, and callout numbers aligned across: the README, `docs/workflow-overview.md` (and the six callout pages), and this Revit model.

## Build notes

- Generate everything via the MCP so the model is **reproducible**, not hand-placed.
- Wrap all model changes in transactions inside `execute_revit_code`.
- Start blocky (boxes + arrowheads + 3D model text); refine visually once the layout reads correctly.
- Commit only instructions/docs/exported images to this repo — never the `.rvt`.

---

*Status: runbook ready; terminology modernized and contractor branding removed (Autodesk product names kept intentionally). The model is built externally via the pyRevit MCP and stored in the Autodesk project area. Paste-ready prompt in [`08-revit-build-prompt.md`](08-revit-build-prompt.md).*
