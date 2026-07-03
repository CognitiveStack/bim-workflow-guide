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

The six numbered stations on the diagram, taken one at a time.

<a id="1-coordinated-models"></a>

### <img src="diagrams/callouts/1.png" alt="1" height="28"> Coordinated Models

Every discipline authors its own model — civil, architecture, structure, and the MEP trades — usually in Revit, with site work often coming from Civil 3D. Before any of it moves downstream, the design team pulls those models together and checks they roughly line up. Catching a conflict here, while it still costs nothing more than rerouting a duct, beats discovering it after a contractor has priced or fabricated around it. This is the first, lightest pass at *does this all actually fit?*

<a id="2-design-collaboration"></a>

### <img src="diagrams/callouts/2.png" alt="2" height="28"> Design Collaboration

This is how the consultant teams share work without the project dissolving into a pile of emailed file copies. Rather than swapping random exports, each team publishes model packages the others can review and pull in — the architect publishes, structure consumes the update, MEP then coordinates against the latest design intent. In Autodesk's world it's the Forma / ACC Design Collaboration workflow, shown on the diagram as the blue arrow feeding down into the CDE from the design side.

<a id="3-common-data-environment"></a>

### <img src="diagrams/callouts/3.png" alt="3" height="28"> Common Data Environment

The CDE is the shared, controlled home for everything on the project — models, drawings, packages, reviews, issues, RFIs, coordination records, published exports — and it's the blue spine running the length of the diagram. Its whole reason to exist is to replace the usual scatter of emails, local folders, USB sticks and spreadsheets with one place the team can trust. But it pays to be precise about what it does: the CDE stores, versions, routes and records information; it doesn't fix anything. People fix the models. In Autodesk terms, Forma Data Management is the CDE layer that Design Collaboration, Model Coordination, reviews and issues all plug into.

<a id="4-contractor-and-trade-models"></a>

### <img src="diagrams/callouts/4.png" alt="4" height="28"> Contractor and Trade Models

Design intent is one thing; building it is another. The trade contractors — mechanical, plumbing, electrical, fire — build their own models for fabrication, installation and sequencing, and these run far more detailed than the design versions: real duct sections, fittings, hangers, access panels, fabrication splits. On the diagram they feed up into the CDE from below. Authored in Revit or specialist fabrication tools, they're where construction-stage coordination really bites.

<a id="5-model-coordination"></a>

### <img src="diagrams/callouts/5.png" alt="5" height="28"> Model Coordination

Here the shared models get checked against each other — clashes, clearances, access, the lot. The value isn't the clash list itself; it's that each problem becomes a tracked issue or RFI with someone's name on it, instead of a manual exercise nobody owns. And it's worth repeating the thing people most often get wrong: clash detection is *one* quality-control step inside coordination, not the whole of it. Autodesk's Forma Model Coordination runs the detection in the cloud and ties clashes to issues; Navisworks still earns its keep for deeper desktop analysis, viewpoints and reports.

<a id="6-federated-model"></a>

### <img src="diagrams/callouts/6.png" alt="6" height="28"> Federated Model

The federated model is all those separate discipline and trade models referenced together into one coordinated view — not a single authored file, but an assembly. (Federated, not *confederated* — a small slip that trips people up.) It's what lets the team see the whole building at once, and it carries through from construction review into handover and operations. In Navisworks you build it by appending NWCs into an NWF; in Forma / ACC the same idea appears as cloud model aggregation and shared coordination spaces.

---

## The coordination feedback loop

The mistake is to read the diagram as a conveyor belt — models in, coordinated model out. It's really a loop, and the loop is the whole point. Model Coordination doesn't resolve anything on its own; it surfaces problems. Each real one becomes either an *issue* or an *RFI*, gets handed to whoever owns the model, is fixed at the source, and is republished for the next pass — and that repeats until the problem is genuinely gone.

There are two of these loops, running in opposite directions. The RFI loop heads back to the *design* side: when coordination throws up a question only the design team can settle — say a duct that seems to need a new penetration through a structural beam — nobody on site just decides that. It goes back as an RFI, the consultants rule on it and revise the design if they must, and the answer flows back in through Design Collaboration. The Issues loop heads back to the *construction* side: a duct fouling a cable tray isn't a design question, it's a trade clash, so it's assigned to the trade that owns it, they adjust their model, and it re-coordinates.

The one thing worth being pedantic about is that these loops return to *people*, not to the cloud. It's tempting to draw the return arrow landing on the CDE, but the CDE doesn't fix anything — it stores, versions and routes. The fix happens in someone's model, and only then does the corrected version flow forward into the CDE again. Find, raise, fix, republish, re-coordinate, verify.

---

## Forma Model Coordination

It's easy to file Forma Model Coordination under "Navisworks, but in the cloud," and that undersells it. Navisworks is a desktop workbench — where you go to analyse clashes deeply, build viewpoints, and produce reports. Forma is a shared environment — where the whole team sees the same coordination problems, owns them, and tracks them to resolution. They answer different questions: Navisworks asks *where exactly are the clashes and how do I dig into them*, while Forma asks *how do we make sure everyone sees, owns, and closes them out*.

The clash detection itself is automatic — upload the models into a configured coordination space and Forma flags the conflicts. But finding a clash and resolving one aren't the same thing, and the software only does the first. A person still decides whether the clash is even real, who owns it, whether it warrants an issue or a full RFI, whether the proposed fix actually holds, and whether the models need another pass. The tool surfaces; the coordinator judges.

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
