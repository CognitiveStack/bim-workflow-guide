# BIM Workflow Guide

A single-page guide to the modern, **Autodesk-centric BIM coordination workflow** — built around a Revit-generated teaching diagram. It covers Revit, Forma / ACC, Design Collaboration, Model Coordination, Navisworks, the Common Data Environment, Issues, RFIs, and federated-model handover.

## Contents

1. [Origin story](#origin-story) — how and why I built this
2. [The diagram](#the-diagram)
3. [How to read it](#how-to-read-it)
4. [The six callouts](#the-six-callouts)
   - [1. Coordinated Models](#1-coordinated-models)
   - [2. Design Collaboration](#2-design-collaboration)
   - [3. Common Data Environment](#3-common-data-environment)
   - [4. Contractor and Trade Models](#4-contractor-and-trade-models)
   - [5. Model Coordination](#5-model-coordination)
   - [6. Federated Model](#6-federated-model)
5. [The coordination feedback loop](#the-coordination-feedback-loop)
6. [Forma Model Coordination](#forma-model-coordination)
7. [Revit to Navisworks workflow](#revit-to-navisworks-workflow)
8. [Construction vs Operations](#construction-vs-operations)
9. [Non-obvious coordination risks](#non-obvious-coordination-risks)
10. [Reference pages](#reference-pages)

---

## Origin story

### Why I made this

I built the Autodesk Coordination Workflow diagram to teach myself how a modern BIM coordination workflow actually fits together. I kept hearing "BIM coordination" used as if it just meant clash detection, and I wanted a single picture that showed the whole thing: design, construction, operation, and the cloud that now runs through all of it.

### The image that inspired me

The spark was a diagram created by **Jeffrey Pinheiro — The Revit Kid** — in his video ["3D Coordination Explained"](https://www.youtube.com/watch?v=2JOGvY9YplY&t=2991s), part of his *BIM After Dark* series. His diagram illustrates the coordination workflow using Turner's White Plains Hospital project as the worked example:

![The original BIM coordination diagram that inspired this project](diagrams/inspiration/revit-kid-bim-coordination-workflow-original.png)

### What the original showed

Look at the blue spine running across the middle of the original, labelled **"Turner"**. That spine is the **Construction Manager / General Contractor**. In that world, the CM/GC is the hub: they physically collect everyone's models, assemble them, run the coordination, and push information back out. Everything flows through *them*.

### How I modernized it

Here's the shift that made this interesting to me: **in a modern cloud workflow, that CM/GC spine is replaced by the cloud.**

In my version, the blue spine is the **Common Data Environment (CDE)**. Now, "CDE" is a general BIM term — it isn't Autodesk-specific. What makes my diagram *Autodesk-centric* is what sits **on** that spine: the two blue **Autodesk Forma** workflows — [Design Collaboration](#2-design-collaboration) and [Model Coordination](#5-model-coordination). (Forma was formerly **ACC — Autodesk Construction Cloud**.)

So it's almost as if the CM/GC has become **redundant — or, more fairly, repurposed**. The coordinating *role* doesn't vanish, but the *spine* of the process is no longer a company standing in the middle passing files around. It's a shared cloud environment that stores, versions, routes, and records the information, with the Forma workflows doing the sharing and the clash-checking.

### The tension I keep coming back to

If you follow this workflow strictly, the **source of truth is the CDE** — the cloud, live and current. And that quietly contradicts a very old habit: handing out a **static set of Construction Documents** — Revit sheets frozen at a moment in time.

I don't think the answer is that Construction Documents are obsolete. They still do essential work: they're the **legal, payment, and scheduling** framework a project runs on. But the *process* around them is no longer siloed the way it used to be — it's far more collaborative and continuous than a set of printed sheets can represent. Holding both ideas at once — a live cloud source of truth **and** a frozen contractual document set — is, I think, one of the genuinely unresolved tensions in modern BIM. I'm keeping it here as an open question, not a verdict.

### How I actually built it (with limited Revit skills)

I'll be honest: my Revit skills aren't advanced enough to model this by hand. What made it possible was the **pyRevit MCP server** — [github.com/CognitiveStack/revit-mcp-server](https://github.com/CognitiveStack/revit-mcp-server) — which let me drive Revit programmatically and build the 3D diagram through an AI-assisted workflow instead of manual modelling. The build is documented in the [Revit 3D diagram build runbook](docs/08-revit-3d-workflow-diagram-plan.md) and the [Desktop build prompt](docs/08-revit-build-prompt.md).

---

## The diagram

![Autodesk Coordination Workflow](diagrams/revit/exports/ad-coordination-workflow-v06.png)

*Autodesk Coordination Workflow — a Revit-generated 3D teaching diagram showing consultant models, contractor models, Design Collaboration, the Common Data Environment, Model Coordination, RFIs, Issues, and the Federated Model. It was created in Revit as a conceptual teaching diagram — **not a real building model** — then exported as PNG.*

The overview shows how project information flows through a modern Autodesk coordination workflow. Consultant models are created during design, shared through **Design Collaboration**, managed in the **Common Data Environment**, checked through **Model Coordination**, and eventually contribute to a **Federated Model** that supports construction review, handover, and operations.

The **CDE is the backbone** of the workflow. It is not just a storage folder. It is the controlled environment where project information is shared, versioned, reviewed, routed, and acted on.

The diagram is intentionally simplified. It does not show every possible Autodesk tool or every possible project exchange. Its purpose is to explain the major coordination stations and the lifecycle movement from **design → construction → operation**.

---

## How to read it

Read it left to right, across the three lifecycle zones. Design asks what we should build, construction asks how we actually build it, and operation asks how we run and maintain it once it's handed over. Two streams of models feed the blue Common Data Environment running down the middle — the consultants' design models flowing in from the left, and the contractors' more detailed trade models joining further along.

The one thing worth slowing down for is that this is a loop, not a pipeline. The obvious reading — models flow in, get checked, flow out — misses the point. Model Coordination doesn't fix anything; it *finds* things. The real work happens when a clash becomes an issue or an RFI, goes back to whoever owns that model, gets fixed at the source, and is republished for another pass. Clash detection is one moment in that cycle, not the whole of coordination.

As for the name: I kept "Autodesk" on purpose. A Common Data Environment is a generic BIM idea, but the two blue workflows sitting on the spine — Design Collaboration and Model Coordination — are Autodesk Forma products. Open formats like IFC still flow in from tools such as Tekla; it's the cloud coordination itself that's Autodesk-driven.

---

## The six callouts

The numbered blue callouts on the diagram are explained below. Each follows the same shape: what it means, why it matters, its Autodesk connection, and a simple example.

### 1. Coordinated Models

**Meaning.** Coordinated models are design discipline models that have been brought together and checked for basic alignment before moving deeper into the shared project workflow. In the diagram, these sit between the **Consultant Models** and the **CDE**. Consultant models usually include Civil, Architecture, Structural, Mechanical, Electrical, Plumbing, and Fire.

**Why this matters.** Coordination at this stage helps the team identify design conflicts early — before construction teams price, fabricate, or install work based on incomplete or conflicting information.

**Autodesk workflow connection.** In Revit, each discipline may author its own model. Civil and site information may come from Civil 3D or related site workflows. These models can then be shared through Forma Data Management / ACC and [Design Collaboration](#2-design-collaboration), and later reviewed together in [Model Coordination](#5-model-coordination) or Navisworks.

**Simple example.** The architectural model shows ceiling heights, the structural model shows beams, and the mechanical model shows duct routes. Coordinating them early helps reveal whether the duct routes fit within the ceiling zones.

### 2. Design Collaboration

**Meaning.** Design Collaboration is the controlled sharing process between consultant teams. Instead of exchanging random files, teams publish and share model packages so other disciplines can review, compare, and consume updates in a structured way. In the diagram, it is shown above the CDE with a downward arrow into the main information backbone.

**Why this matters.** This prevents the project from becoming a collection of uncontrolled file copies. It gives the design team a clearer process for sharing work-in-progress information, reviewing changes, and coordinating design intent.

**Autodesk workflow connection.** In Autodesk Forma / ACC, Design Collaboration supports package-based sharing between teams. It helps consultants share model updates before they flow into broader coordination and construction workflows.

**Simple example.** The architecture team shares a package. The structural team reviews and consumes the update. The MEP team can then coordinate its services against the latest shared design intent.

### 3. Common Data Environment

**Meaning.** The Common Data Environment, or CDE, is the central information environment for the project — the large blue horizontal backbone in the diagram. It stores and manages models, drawings, documents, packages, reviews, Issues, RFIs, coordination records, and published exports.

**Why this matters.** The CDE becomes the shared project information backbone. Instead of project information being scattered across emails, local folders, USB drives, informal file transfers, and spreadsheets, the CDE gives the team a controlled place to share, version, review, and act on information.

> **The CDE stores, versions, routes, and records information — but it does not fix coordination problems by itself. People and model authors fix the source models.**

**Autodesk workflow connection.** In Autodesk Forma / ACC, Forma Data Management acts as the CDE layer. It connects with Design Collaboration, Model Coordination, Reviews, Issues, and other project workflows.

**Simple example.** A Revit model, a PDF drawing, an Issue, an RFI response, and a coordination review record can all be connected through the CDE instead of being scattered across separate systems.

### 4. Contractor and Trade Models

**Meaning.** Contractor models, also called **trade models**, are developed by contractors and subcontractors for construction, fabrication, installation, and sequencing. In the diagram, they are shown below the CDE, feeding upward into the coordination workflow. They often include Mechanical, Plumbing, Electrical, and Fire.

**Why this matters.** A design model may show design intent, but a contractor/trade model shows how the work will actually be fabricated and installed. This is especially important for MEP services, steelwork, fire protection, and other coordinated systems.

**Autodesk workflow connection.** Trade models may be authored in Revit or specialist fabrication tools, then shared into the CDE and reviewed in [Model Coordination](#5-model-coordination) or Navisworks. They form a major part of construction-stage coordination.

**Simple example.** A mechanical design model may show the intended duct route. The mechanical contractor's trade model may show actual duct sections, fittings, hangers, access panels, fabrication splits, and installation detail.

### 5. Model Coordination

**Meaning.** Model Coordination is the process of checking shared models for clashes, access problems, clearance issues, and coordination risks. In the diagram, it is shown above the CDE near the transition from construction coordination toward the federated model.

**Why this matters.** Model Coordination helps replace unmanaged manual coordination with a trackable workflow. Problems can become **Issues**, **RFIs**, and assigned actions.

> **Clash detection is not the whole workflow. Clash detection is one quality-control activity inside the wider BIM coordination workflow.**

**Autodesk workflow connection.** Autodesk Forma Model Coordination can detect clashes from shared models, group coordination problems, and connect them to Issues. Navisworks can still be used for deeper desktop-based analysis, viewpoints, reports, and advanced clash review — but Forma improves team visibility and cloud collaboration. See [Forma Model Coordination](#forma-model-coordination).

**Simple example.** A duct clashes with a beam. The clash is detected in Model Coordination. A coordination Issue is created and assigned. The mechanical contractor updates the duct route and republishes the model.

### 6. Federated Model

**Meaning.** A federated model is a combined model set made from multiple discipline and trade models. In the diagram, it is shown at the right side, after the CDE and Model Coordination workflow. It is not usually one single authored model — it is a coordinated assembly of separate models brought together for review, handover, and operations.

> **The federated model is the central object of coordination.** (Use "Federated Model" — not "Confederated Model.")

**Why this matters.** The federated model gives the project team a single coordinated view of the building information. It supports construction review, handover, facilities management, asset data, and future operational use.

**Autodesk workflow connection.** In Navisworks, a federated model is commonly created by appending multiple NWC or model files into an NWF. In Forma / ACC, the same concept appears through cloud-based model aggregation, coordination spaces, and shared model review. See [Revit to Navisworks workflow](#revit-to-navisworks-workflow).

**Simple example.** Architecture, structure, mechanical, electrical, plumbing, fire, civil, and contractor trade models are combined into one review environment so the project team can inspect the whole building system together.

---

## The coordination feedback loop

### The BIM coordination workflow is not linear

Coordination is **iterative**. Model Coordination finds clashes and coordination risks. Important problems become **Issues** or **RFIs**. The responsible team updates the source model. The model is republished into the CDE. The model is re-coordinated. The loop repeats until the issue is resolved.

> **Find → Raise → Fix → Republish → Re-coordinate**

The diagram shows two feedback loops: the **RFI loop** and the **Issues loop**.

### RFI loop

A coordination review identifies a question that needs design input. The **RFI** goes back to the consultants / design model authors. The consultants respond, revise the design if needed, and republish through [Design Collaboration](#2-design-collaboration) into the CDE.

**Example:** A duct route appears to require a beam penetration. The contractor cannot approve this alone. The question becomes an RFI to the structural / design team.

### Issues loop

Model Coordination identifies a construction or trade coordination problem. The **Issue** goes back to the contractor / trade model authors. The trade team updates the model and republishes it into the CDE.

**Example:** A mechanical duct clashes with a cable tray. The issue is assigned to the relevant trade team. The trade model is updated and re-coordinated.

### The loops return to the model authors, not just the CDE

The return arrows should **not** be explained as returning to the CDE only. The CDE stores and manages information, but **people fix models**. The loops return to the model authors. Their updated models then flow forward again into the CDE.

| Thing | What it does |
|---|---|
| **CDE** | Stores, versions, routes, and records information |
| **Model authors** | Fix the source models |
| **Model Coordination** | Tests the shared / federated model environment |
| **Issues and RFIs** | Create accountable feedback loops |

> **Find → Raise → Fix → Republish → Re-coordinate → Verify**

---

## Forma Model Coordination

### Collaboration-first, not just "Navisworks in the cloud"

Forma Model Coordination is cloud-based model review and clash coordination. It is **not just a replacement for Navisworks** — it is **collaboration-first**.

- **Navisworks** is stronger as a **desktop clash-analysis workbench**.
- **Forma Model Coordination** is stronger as a **shared cloud coordination environment**.

### Automatic clash detection, human judgement

Forma Model Coordination can **automatically detect clashes** once models are uploaded into a configured coordination space. However, **human judgement is still required**. The software can identify possible conflicts, but the coordinator must decide:

- whether the clash is real
- who owns it
- whether it should become an Issue
- whether an RFI is needed
- whether the fix is acceptable
- whether the model should be re-coordinated

### Key distinction

| Tool | The question it asks |
|---|---|
| **Navisworks** | Where exactly are the clashes and how do I analyse them deeply? |
| **Forma Model Coordination** | How do we make sure the whole team sees, owns, tracks, and resolves coordination problems? |

---

## Revit to Navisworks workflow

### Key idea

**Revit is where the model is authored and changed. Navisworks is where the federated model is reviewed and clashes are detected.**

- **NWC** files are exported snapshots / caches from Revit.
- **NWF** is the Navisworks working file that references the NWC files.
- **NWD** is a published, frozen model.

### Workflow

1. Open the correct Revit discipline model.
2. Make the design or coordination change.
3. Export a fresh NWC.
4. Overwrite the old NWC in the Navisworks cache folder.
5. Open or refresh the Navisworks NWF.
6. Rerun the clash test.
7. Confirm whether the clash is resolved.

### Folder logic

| Folder | Holds |
|---|---|
| `/revit/current/` | the live working Revit models |
| `/navisworks/02_NWC_Cache/` | exported NWC snapshots |
| `/navisworks/03_NWF_Working/` | Navisworks working files |

### Do not treat the NWC as the source model

The **RVT is the authoring source.** The NWC is an **exported coordination snapshot**. If a clash is found, you fix it in Revit and re-export the NWC — you never "fix" the NWC directly. Navisworks is a desktop workbench; Forma Model Coordination is collaboration-first — they complement each other (see [Forma Model Coordination](#forma-model-coordination)).

---

## Construction vs Operations

**Construction is about delivering and building the project. Operations is about running and maintaining the building after handover.**

**Construction involves:** contractors, subcontractors, trade models, shop drawings, RFIs, Issues, sequencing, fabrication, inspections, commissioning, as-built updates.

**Operations involves:** facilities management, asset registers, maintenance schedules, equipment data, warranties, manuals, commissioning records, asset tags, lifecycle cost, digital twins, building performance.

### The model's role changes across the lifecycle

Operations can have a model, but it is not usually another design discipline model. It is better understood as an **asset / facilities layer** of the BIM lifecycle.

| Phase | What the model says |
|---|---|
| **Design** | This is what we intend to build. |
| **Construction** | This is what we are coordinating and installing. |
| **Operation** | This is the asset we now need to manage. |

**MEP+O** means mechanical / electrical / plumbing **plus operations**. It extends MEP thinking beyond design and installation into maintainability, commissioning, asset data, and lifecycle management.

---

## Non-obvious coordination risks

### Beginner vs professional coordination

Beginner clash detection asks: *Do the objects touch?*

Professional coordination asks: *Can this be built, accessed, maintained, replaced, certified, and operated?*

The clashes below are **not just geometry clashes**. They are access, maintenance, replacement, performance, documentation, and sequence clashes.

- **Duct fits geometrically but has no maintenance access.** The duct may not clash with structure, but dampers, access doors, actuators, sensors, and inspection panels may be unreachable.
- **Pipe passes through wall but no sleeve/opening was coordinated.** The route may be intended, but the wall needs a coordinated opening, sleeve, fire stopping, acoustic treatment, and responsibility assignment.
- **Cable tray fits but blocks access panel.** The tray may not physically clash, but it may prevent access to a duct panel, valve, ceiling hatch, or equipment access zone.
- **Valve is above a fixed ceiling with no access hatch.** Correctly placed, but unusable after construction because maintenance staff cannot reach it.
- **Fire damper is installed where it cannot be maintained.** Near the fire wall but inaccessible for inspection, reset, or maintenance.
- **Ceiling void is too shallow for all services.** Each system may fit individually, but ducts, pipes, trays, sprinklers, lights, hangers, insulation, and ceiling framing may not fit together.
- **Structural opening is missing.** An MEP service may pass through a beam, wall, or slab in the model, but the structural opening may not be approved or documented.
- **Drainage pipe does not have enough fall.** It may look correct in plan, but gravity drainage needs slope — the route may fail in section because beams or ceiling zones prevent the required fall.
- **Equipment cannot be replaced later because access space is blocked.** Installable during construction but impossible to remove or replace after walls, doors, pipework, or ceilings are complete.
- **Installation sequence is impossible.** The final model may appear clash-free, but the actual installation order may not be feasible.

### Catch it digitally, before site

"Catch it in the software, not on site" does **not** mean builders are careless. Experienced builders usually will not knowingly build a duct through a beam. The point is that **late discovery is expensive**.

| In software, a clash may require | On site, the same clash may cause |
|---|---|
| discussion | stopped work |
| model edit | RFI |
| revised drawing | redesign |
| issue update | wasted prefabricated material |
| re-coordination | rework, delay, cost claim, trade resequencing, contractual tension |

> **Catch coordination problems digitally before they become physical site problems.**

---

## Reference pages

Separate reference and appendix material:

- [Glossary](docs/glossary.md) — plain definitions of key BIM terms
- [Revit 3D diagram build runbook](docs/08-revit-3d-workflow-diagram-plan.md) · [Build prompt](docs/08-revit-build-prompt.md) — how the diagram was built (pyRevit MCP)
- [Versioning & exports](docs/versioning-and-exports.md) — how diagrams and docs are version-controlled
- [Diagram exports & credit](diagrams/revit/README.md) · [Inspiration & credit](diagrams/inspiration/README.md)
- [PRD](PRD.md) — product requirements
- [Related CogStack repos](links/related-repos.md) · [Learning resources](links/learning-resources.md) *(coming soon)*
- Examples: [Harrismith Fire Station](examples/harrismith-fire-station/README.md) *(coming soon)* · [BIM Clash Visual Atlas](examples/bim-clash-visual-atlas/README.md) *(coming soon)*

### Versioning strategy

- **Revit `.rvt`** = diagram authoring file (not committed to Git — binary, no useful diffs; excluded via `.gitignore`).
- **PNG / PDF exports** = version-controlled visual artifacts under `diagrams/revit/exports/`.
- **Markdown docs** = explanation / source of truth.
- **GitHub** = versioned educational repo / website source.

---

*New to a term? See the [Glossary](docs/glossary.md). Want to build the diagram yourself? See the [build runbook](docs/08-revit-3d-workflow-diagram-plan.md).*
