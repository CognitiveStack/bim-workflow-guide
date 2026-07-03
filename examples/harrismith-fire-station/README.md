# Harrismith Fire Station — a worked example

*A real, still-in-progress project I'm using to walk the coordination workflow with actual tools rather than the abstract diagram. If the [BIM Workflow Guide](../../README.md) is the map, this is the territory.*

> **Status: in progress.** The project currently runs from civil survey coordinates through architecture, structure and MEP, and into cloud coordination in Forma — which is as far as I've taken it so far. It's a living example; the construction and operation stages aren't here yet.

> 🧩 **This page is a scaffold.** The stage-by-stage structure is set; the project-specific detail, screenshots and slides (from the Triviron walkthroughs) drop into the marked slots. Put images in an `images/` folder beside this file and replace each 📷 placeholder with the embed.

## The journey

The Harrismith model moves through one tool at a time, and each step lands somewhere on the guide's diagram.

### 1. Civil — establishing the coordinates

Everything downstream has to sit in the same place in space, so the project starts on the ground: the survey and civil setup (Civil 3D) that fixes the shared coordinate system — the base point every later model inherits. Get this wrong and every discipline is subtly misplaced. On the diagram it's the groundwork beneath [Consultant Models ①](../../README.md#1-coordinated-models).

> 📷 *Screenshot: the coordinate setup — base point, survey point, shared coordinates.*

### 2. Architecture — the Revit model

The architectural model is authored in Revit on those coordinates, and becomes the first shape of the building the other disciplines design against. On the diagram it's a [Consultant Model ①](../../README.md#1-coordinated-models), shared through [Design Collaboration ②](../../README.md#2-design-collaboration).

> 📷 *Screenshot: the architectural Revit model.*

### 3. Structure — Revit ↔ Robot Structural Analysis

The structural model round-trips between Revit and Autodesk Robot Structural Analysis: Revit for the physical model, Robot for the analysis and design, then back into a coordinated structural model. On the diagram, another [Consultant Model ①](../../README.md#1-coordinated-models).

> 📷 *Screenshot: the Revit structural model and/or a Robot analysis result.*

### 4. MEP — services in Revit

Mechanical, electrical, plumbing and fire services modelled in Revit and threaded through the architecture and structure — the systems most likely to fight each other for space. Still [Consultant Models ①](../../README.md#1-coordinated-models) here; the same trades become [Contractor / Trade Models ④](../../README.md#4-contractor-and-trade-models) downstream.

> 📷 *Screenshot: the MEP services model.*

### 5. Coordination — Navisworks

The discipline models are federated and clash-tested on the desktop — the first moment structure and MEP are actually forced to agree. This is [Model Coordination ⑤](../../README.md#5-model-coordination), desktop side.

> 📷 *Screenshot: the federated model and clash results. Note a real clash or two you found here.*

### 6. Cloud coordination — Forma — *current frontier*

The models are published into Autodesk Forma, where **Design Collaboration** handles sharing and **Model Coordination** handles cloud clash detection — the blue spine of the diagram. On the guide, this is the [Common Data Environment ③](../../README.md#3-common-data-environment) with [Design Collaboration ②](../../README.md#2-design-collaboration) and [Model Coordination ⑤](../../README.md#5-model-coordination). **This is as far as the project has gone so far.**

> 📷 *Screenshot: the Forma coordination space / issues.*

## Where it goes next

Not reached yet: contractor and trade models, shop drawings, installation and sequencing, as-built records, and eventual handover into operations — the right-hand side of the diagram. See [Construction vs Operations](../../README.md#construction-vs-operations).

## At a glance

| Harrismith stage | Tool | On the guide |
|---|---|---|
| Coordinates | Civil 3D / survey | groundwork under ① |
| Architecture | Revit | ① → ② |
| Structure | Revit ↔ Robot | ① |
| MEP | Revit | ① / ④ |
| Coordination | Navisworks | ⑤ (desktop) |
| Cloud coordination | Forma | ③ + ② + ⑤ ← *here now* |

---

*Companion to the [BIM Workflow Guide](../../README.md).*
