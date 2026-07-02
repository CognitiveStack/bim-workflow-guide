# 08 — Revit Build Prompt (paste into Claude Desktop)

> Paste the block below into a **new Claude Desktop session** that has the pyRevit MCP server connected. Paste the reference image (`revit-kid-bim-workflow-diag\image.png`) **first**, then the prompt. See [`08-revit-3d-workflow-diagram-plan.md`](08-revit-3d-workflow-diagram-plan.md) for the full runbook and terminology rationale.

```text
You are helping me build a 3D "teaching diagram" in Autodesk Revit using the
pyRevit MCP server. I have just pasted a reference image — a 2019 isometric BIM
coordination workflow infographic. I want a MODERNIZED, CONTRACTOR-NEUTRAL,
simplified "kid-friendly" version of this layout as real 3D geometry. This is
Module_00 of my "BIM Coordination Workflow Atlas".

== SAVE LOCATION ==
Save the Revit model to:
C:\Users\charles\Documents\Autodesk\projects\bim-coordination-workflow-atlas\rvt\current\BIM_Coordination_Workflow_Atlas_Module_00.rvt
(create folders if needed). Do NOT save anywhere else.

== MODERNIZE / CONTRACTOR-NEUTRAL (important) ==
- Remove CONTRACTOR branding: no "Turner", no project name, no logo, no draft
  date. KEEP Autodesk product names (Design Collaboration, Model Coordination) —
  the diagram may be titled "Autodesk Coordination Workflow".
- The big blue ribbon in the image becomes the COMMON DATA ENVIRONMENT — a
  strong-blue spine running through the middle. Label it in full:
  "Common Data Environment".
- "Consolidated Model (Navisworks/IFC)" becomes "Federated Model". It is
  produced via Model Coordination (cloud) OR Navisworks Manage (desktop) —
  label it "Federated Model (Model Coordination / Navisworks)".
- "3D Design Model" -> "Coordinated Design Model".
- "Source Models" -> "Discipline Models".
- Tool note "Revit, Tekla, CAD" -> "Authoring Tools (Revit, Civil 3D, ...)".
- Put "Design Collaboration" on the design side of the spine and
  "Model Coordination" near the Federated Model.
- Add a small "BIM Coordinator" role-marker beside the Federated Model.
- Feedback loops: top = "Design Change Loop", bottom = "Issue & Update Loop".

== HOW TO WORK ==
- Use the pyRevit MCP for everything. Wrap all changes in transactions.
- Work INCREMENTALLY. After each milestone: save, capture the 3D view as an
  image, and show me so I can correct before you continue.
- METRIC (millimetres). One level called "Workflow".
- Keep block names, colors, and callout numbers consistent across modules.

== STEP 0: CONNECT ==
1. Check Revit status and the active document. If nothing suitable is open,
   start a new project from a generic metric template.
2. Set units to mm. Create level "Workflow" if missing.
3. Report what you found before building.

== LAYOUT (left -> right along +X; streams along Y; stacking up +Z) ==
Three zones along X, each with a flat 3D model-text label:
- DESIGN:       X 0     to 8000
- CONSTRUCTION: X 8000  to 20000
- OPERATION:    X 20000 to 28000

DESIGN zone:
- 7 colored input streams from the left at X~0, stacked along Y
  (Y = -9000, -6000, -3000, 0, +3000, +6000, +9000), each ending in a +X
  arrowhead, labeled: Architectural, Structural, Mechanical, Electrical,
  Plumbing, Fire Protection, Civil.
- A "Coordinated Design Model" cluster (callouts 1, 3) where streams converge
  at ~X 6000, Y 0.

CDE BACKBONE (callout 5):
- Strong-blue spine from ~X 7000 to 20000 through the middle, Y 0, raised in Z.
  Label "Common Data Environment".
- "Design Collaboration" marker on the design side; "Model Coordination"
  marker near the Federated Model (note Navisworks as the alternative).

CONSTRUCTION zone:
- Steel / penetrations branch (callouts 4.1 underground coordination,
  4.2 penetrations & fabrication) below the design model.
- Trade model inputs feeding onto the spine (callouts 6, 7).
- Central "Federated Model" block (callout 8): a tall stack of all seven
  discipline colors at ~X 18000, Y 0.
- Small "BIM Coordinator" role-marker beside it.

OPERATION zone:
- 3x3 grid of small "Discipline Models" cubes (callout 10), top-right.
- Assembled "Federated Model" block (callout 9) at ~X 24000.

FEEDBACK LOOPS (dashed; approximate with short segments / small boxes):
- Top: "Design Change Loop" (8.2) from federation back to DESIGN.
- Bottom: "Issue & Update Loop" (8.1) from operation back to trade models.

== DISCIPLINE COLORS (keep consistent) ==
Architectural = tan/gold,  Structural = violet/light purple,
Mechanical = orange,  Electrical = yellow,  Plumbing = cyan/light blue,
Fire Protection = red,  Civil = green.
CDE backbone = strong blue. The Federated Model stack uses all seven colors.
(Do NOT use blue for any discipline — blue is reserved for the CDE spine.)

== CALLOUTS ==
Numbered markers (small disks/spheres or 3D text) for:
1, 2, 3, 4.1, 4.2, 5, 6, 7, 8, 8.1, 8.2, 9, 10 — positioned as in the
reference image. These numbers must match my written workflow docs.

== BUILD ORDER (save + screenshot after each) ==
A. Zones + zone labels + level/units.
B. DESIGN streams + arrows + labels.
C. Coordinated Design Model cluster.
D. CDE backbone + Design Collaboration / Model Coordination markers.
E. Steel branch + trade streams + Federated Model + BIM Coordinator marker.
F. OPERATION discipline-models grid + assembled federated block.
G. Feedback loops.
H. All numbered callouts.
I. Set a nice default 3D isometric view, save, export final image.

Start with STEP 0 and report back before building.
```
