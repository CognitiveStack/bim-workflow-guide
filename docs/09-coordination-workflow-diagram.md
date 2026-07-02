# 09 — The Coordination Workflow Diagram Explained

This is the central teaching diagram for the repo: a modernized, de-branded view of how a BIM coordination workflow runs on a cloud Common Data Environment. It was built as 3D geometry in Revit (via the pyRevit MCP — see [08](08-revit-3d-workflow-diagram-plan.md)) and exported for the web.

![Autodesk Coordination Workflow](../diagrams/revit/exports/AD-Coordination-Workflow-v05.png)

## How to read it

The diagram flows **left → right** across the three phases of a project:

- **DESIGN** — consultants author their models.
- **CONSTRUCTION** — trade contractors add their models; everything is coordinated.
- **OPERATION** — the finished, coordinated model is handed to the owner.

Running through the middle is the blue **Common Data Environment (CDE)** — the cloud "single source of truth." Everything **publishes to** and **pulls from** it. Nothing moves from one party to another by email or USB stick; it moves through the CDE.

Two kinds of models feed the CDE:

- **Consultant models** (design side): Civil, Architectural, Structural, Mechanical, Electrical, Plumbing, Fire.
- **Contractor models** (construction side): the trades that build the MEP + fire systems — Mechanical, Plumbing, Electrical, Fire.

And two **feedback loops** keep it honest — the **RFI** loop and the **ISSUES** loop (explained below). These are what make coordination a *cycle*, not a one-way pipeline.

## The six callouts

### 1 — Coordinated Models
Each design consultant authors its own discipline model (in Revit, Civil 3D, etc.). On the design side these are first brought together into an initial **coordinated set** — a quick check that the design disciplines broadly fit — before being published.

### 2 — Design Collaboration
The cloud workflow (Autodesk Forma / Construction Cloud **Design Collaboration**) by which consultants **share and exchange** their models into the CDE. This is how design-side models get published and kept in sync with each other.

### 3 — Common Data Environment (CDE)
The cloud **single source of truth** (Autodesk Docs). It stores, shares, and manages every model and its data. In this diagram it's the blue spine that connects design, coordination, construction, and operation. **This is the heart of the modernization**: see the note below on how it replaces the old contractor-led file handling.

### 4 — Contractor Models
Trade contractors and fabricators (Mechanical, Plumbing, Electrical, Fire) create their detailed **construction / fabrication models** and publish them **up into the CDE**. These are more detailed than the design models — they represent what will actually be installed.

### 5 — Model Coordination
The cloud workflow (Autodesk Forma / Construction Cloud **Model Coordination**) that **federates** the published models and runs **automated clash detection**. Detected conflicts become tracked **issues**. *Autodesk Navisworks Manage* remains a valid desktop alternative for federation and clash detection.

> **What happened to the General Contractor / Construction Manager?**
> In the older (pre-cloud) workflow, a GC or CM physically collected everyone's files, assembled them, and ran coordination. In this modernized workflow that role is largely **absorbed by the CDE plus the two Forma workflows** — Design Collaboration (2) and Model Coordination (5). The GC/CM-led approach still happens in practice; it's just no longer the *spine* of the process.

### 6 — Federated Model
The **combined coordination model** — all consultant and contractor models referenced together into one view (without merging the originals). It's used for review and clash detection throughout construction, and the final version is **handed over for operation** — the deliverable in the OPERATION phase.

## The two feedback loops

Coordination is iterative. Two loops carry problems back to whoever can fix them; the fixed models are then **republished to the CDE**, and the cycle repeats.

- **RFI loop (design side).** When coordination raises a question that needs a design decision, a **Request For Information (RFI)** goes back to the consultants. They make the **design change** and republish via Design Collaboration.
- **ISSUES loop (construction side).** Clashes found by Model Coordination become **Issues** assigned to the responsible trade. The trade **updates its model** and republishes. This is the core day-to-day coordination cycle.

## Terminology (de-branded, modernized)

| Term in the diagram | What it means |
|---|---|
| Consultant Models | Design-side discipline models |
| Contractor Models | Construction-side trade/fabrication models |
| Coordinated Models | Design disciplines checked together before publishing |
| Common Data Environment (CDE) | The cloud single source of truth |
| Design Collaboration | Cloud workflow for sharing design models |
| Model Coordination | Cloud federation + clash detection |
| Federated Model | All models combined into one coordination view |
| RFI | A formal request for design information |
| Issue | A tracked coordination problem (often a clash) |

---

*See also: [01 — BIM Workflow Overview](01-bim-workflow-overview.md), the [Glossary](glossary.md), and the build runbook in [08](08-revit-3d-workflow-diagram-plan.md).*
