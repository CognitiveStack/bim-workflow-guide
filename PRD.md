# PRD: CogStack BIM Coordination Workflow

## 1. Executive Summary

The **CogStack BIM Coordination Workflow** repository is an educational source-of-truth that explains the modern Building Information Modeling (BIM) coordination workflow in plain, beginner-friendly language. It shows how separate discipline models move from design authoring tools (Revit, Civil 3D) into a Common Data Environment (CDE), become part of a federated model, pass through coordination and clash detection, and ultimately support construction and owner handover.

The core value proposition is correcting a common misconception: **clash detection is not the whole BIM workflow** — it is one activity inside a much wider coordination process. By laying out the full hierarchy clearly, the repo gives learners a mental model they can build on.

The MVP goal is a clean, reviewable first version of the repository: a beginner can open the README, understand the end-to-end workflow, see it as a 3D coordination diagram, and follow links into detailed topic docs. The repo also acts as the foundation for future CogStack BIM automation work (Revit MCP, Forma MCP, Revit template-as-code) and Triviron presentation material.

## 2. Mission

**Mission:** Make the modern BIM coordination workflow understandable to beginners, and provide a structured foundation for future CogStack BIM automation and teaching tools.

**Core principles:**

1. **Beginner-first** — explain plainly; define jargon before using it.
2. **Correct mental model** — show the full workflow hierarchy, not just clash detection.
3. **Original and unbranded** — all diagrams and content are original; no copying of branded material.
4. **Practical** — every concept anchored to a real AEC project example.
5. **Foundation for automation** — structured so it can later drive a Revit MCP 3D teaching model and become website/slide content.

## 3. Target Users

**Primary:**
- Charles, while learning Autodesk BIM workflows
- Triviron stakeholders
- Beginner BIM coordinators
- AEC professionals learning cloud-based model coordination
- Developers exploring BIM automation and "BIM as code"

**Secondary:**
- Future CogStack clients
- People interested in Autodesk Forma, Revit, Navisworks, and AI-assisted BIM workflows

**Technical comfort level:** Mixed. Content must work for non-technical AEC beginners while remaining useful to developers exploring automation.

**Key needs / pain points:**
- Confusion that "BIM coordination = clash detection."
- No clear picture of how models flow from authoring tools to handover.
- Difficulty distinguishing BIM coordination vs. MEP coordination vs. clash detection.
- Lack of a single, plain-language reference to build presentations and automation on.

## 4. MVP Scope

### In Scope

**Core content**
- ✅ Beginner-friendly README explaining the full workflow
- ✅ Workflow hierarchy: BIM Workflow → Coordination → Federated Models → MEP Coordination → Clash Detection → Issue Management → Model Updates → Construction Support → As-Built / Handover
- ✅ `docs/01-bim-workflow-overview.md` (full first version)
- ✅ `docs/glossary.md` (full first version)
- ✅ `links/related-repos.md` (full first version)
- ✅ `docs/08-revit-3d-workflow-diagram-plan.md` (full first version)

**Diagrams**
- ✅ `diagrams/revit/exports/ad-coordination-workflow-v05.png` (3D coordination diagram built in Revit via the pyRevit MCP; CDE-centric, contractor-neutral, with RFI + ISSUES loops) — the primary workflow illustration
- ✅ `docs/workflow-overview.md` + `docs/callouts/01–06` (embed the 3D diagram and explain the 6 callouts + both loops)

**Structure**
- ✅ Full repository directory and file structure scaffolded (stubs for remaining docs/diagrams/examples/links)

### Out of Scope (Future Phases)

- ❌ Fully written versions of all detailed topic docs (02–07) — stubs only in MVP
- ❌ Completed worked examples (Harrismith Fire Station, BIM Clash Visual Atlas) — placeholders only
- ✅ The Revit MCP-generated 3D teaching model — **Module 00 built** (`ad-coordination-workflow-v05`); further modules still out of scope
- ❌ Website or slide-deck rendering
- ❌ Live MCP automation (Revit MCP, Forma MCP) integration

## 5. User Stories

1. **As a BIM beginner**, I want to read a plain-language overview, so that I understand the whole coordination workflow, not just clash detection.
   - *Example:* A new coordinator opens the README and follows the workflow from "Discipline Models" to "Owner Handover."

2. **As an AEC professional**, I want to see how a federated model fits into coordination, so that I understand where my discipline model goes after I publish it.
   - *Example:* An MEP engineer sees their model published, federated, reviewed, and clashed against structure.

3. **As a learner**, I want clear definitions of BIM terms, so that I can follow industry conversations.
   - *Example:* A reader looks up "hard clash" vs. "clearance clash" in the glossary.

4. **As a Triviron stakeholder**, I want structured, presentation-ready content, so that I can turn it into a deck or website page.
   - *Example:* The docs become slides for a client workshop.

5. **As a developer**, I want a documented plan for the Revit 3D workflow model, so that I can later build it with the Revit MCP server.
   - *Example:* A developer reads `08-revit-3d-workflow-diagram-plan.md` and scopes the build.

6. **As a reader**, I want the workflow shown as a diagram, so that I can grasp it visually.
   - *Example:* The 3D coordination diagram displays directly on the GitHub README.

7. **As a CogStack contributor**, I want links to related repos, so that I can navigate the wider BIM automation ecosystem.
   - *Example:* A contributor jumps from this repo to the Revit MCP server repo.

## 6. Core Architecture & Patterns

This is a **documentation repository**, not an application. The "architecture" is its information structure: a beginner entry point (README) that links to progressively detailed topic docs, a glossary, original diagrams, worked examples, and a forward-looking automation plan.

**Directory structure:**

```
cogstack-bim-coordination-workflow/
├── README.md
├── PRD.md
├── .gitignore                     # excludes Autodesk binaries (.rvt/.nwc/.nwf/.nwd)
├── docs/
│   ├── index.md
│   ├── workflow-overview.md            # BIM-001 diagram explained
│   ├── coordination-feedback-loop.md   # RFI + Issues loops
│   ├── revit-to-navisworks-workflow.md
│   ├── forma-model-coordination.md
│   ├── construction-vs-operations.md
│   ├── versioning-and-exports.md
│   ├── 01-bim-workflow-overview.md     # background
│   ├── 08-revit-3d-workflow-diagram-plan.md   # build runbook
│   ├── 08-revit-build-prompt.md
│   ├── glossary.md
│   ├── callouts/
│   │   ├── 01-coordinated-models.md
│   │   ├── 02-design-collaboration.md
│   │   ├── 03-common-data-environment.md
│   │   ├── 04-contractor-trade-models.md
│   │   ├── 05-model-coordination.md
│   │   └── 06-federated-model.md
│   └── coordination-risks/
│       └── non-obvious-clashes.md
├── diagrams/
│   └── revit/
│       ├── README.md              # exports table + versioning
│       └── exports/ad-coordination-workflow-v05.png
├── examples/
│   ├── harrismith-fire-station/README.md
│   └── bim-clash-visual-atlas/README.md
└── links/
    ├── related-repos.md
    └── learning-resources.md
```

**Design patterns:**
- **Callout-per-page** — each of the six diagram callouts has its own Markdown page (Meaning / Why it matters / Autodesk workflow connection / Simple example).
- **Diagram + explanation split** — the Revit-built 3D diagram is the visual; Markdown is the source of truth.
- **Original diagrams** — the coordination diagram is built as 3D geometry in Revit (via pyRevit MCP) and exported as PNG for the web.
- **Separation of concerns** — concepts in `docs/`, visuals in `diagrams/`, applied cases in `examples/`, external pointers in `links/`.

## 7. Tools / Features (Content Modules)

| Module | Purpose |
|---|---|
| README | Landing page; main diagram, core concepts, doc links, versioning strategy |
| `docs/index.md` | Documentation index |
| `workflow-overview` | The BIM-001 Autodesk Coordination Workflow diagram explained |
| `coordination-feedback-loop` | RFI + Issues loops; coordination as an iterative cycle |
| `callouts/01–06` | One page per numbered callout (Coordinated Models → Federated Model) |
| `revit-to-navisworks-workflow` | RVT authoring → NWC/NWF/NWD review workflow |
| `forma-model-coordination` | Forma Model Coordination as collaboration-first |
| `construction-vs-operations` | Lifecycle roles of the model across phases |
| `versioning-and-exports` | Why PNG/Markdown are versioned and the .rvt is not |
| `coordination-risks/non-obvious-clashes` | Access/maintenance/sequence risks beyond geometry |
| `01-bim-workflow-overview` | Background: clash detection is not the whole workflow |
| `08-revit-3d-workflow-diagram-plan` / `-build-prompt` | Revit build runbook + Desktop prompt |
| `glossary` | Plain definitions of key BIM terms |
| `diagrams/revit/` | Exported 3D coordination diagram + exports table |
| `examples/` / `links/` | Worked AEC examples; related repos and learning resources |

**Main tools covered in content:** Revit, Civil 3D, Navisworks Manage, Autodesk Forma (Data Management, Design Collaboration, Model Coordination), Autodesk Construction Cloud concepts, pyRevit MCP / Revit MCP, GitHub as documentation + workflow source control.

## 8. Technology Stack

- **Format:** Markdown (`.md`) for all documentation
- **Diagrams:** 3D model built in Revit (via pyRevit MCP), exported as PNG
- **Source control:** Git / GitHub
- **No build system, runtime, or dependencies** for the MVP
- **Future (out of MVP):** Revit MCP server, Forma MCP server, pyRevit — for the Phase 2 3D teaching model

## 9. Security & Configuration

- **Authentication/authorization:** None required — public educational content.
- **Configuration:** None — static Markdown files and exported images.
- **Security scope:**
  - In scope: ✅ Ensure no proprietary/branded diagrams or copyrighted material are copied; all content original.
  - Out of scope: ❌ Application security, secrets, access control (no software in MVP).
- **Deployment:** Hosted as a GitHub repository; renders directly on GitHub. Future option to publish as a website/slide deck.

## 10. API Specification

Not applicable for the MVP — this is a documentation repository with no API surface.

## 11. Success Criteria

The repo is successful when:

- ✅ A beginner can open the README and understand the BIM coordination workflow.
- ✅ The 3D coordination diagram displays correctly on GitHub.
- ✅ The repo clearly explains how a federated model fits into coordination.
- ✅ The repo distinguishes BIM coordination vs. MEP coordination vs. clash detection.
- ✅ The docs are structured enough to become a future website page or slide deck.
- ✅ The repo can later support a Revit MCP-generated 3D workflow model.

**Quality indicators:** clear, practical, beginner-friendly, professional tone suitable for Triviron presentation material; jargon explained; no branded/copied diagrams; clash detection never presented as the whole workflow.

## 12. Implementation Phases

### Phase 1 — Foundation (MVP)
**Goal:** Clean, reviewable first version of the repo.
- ✅ Create full directory/file structure
- ✅ Write README, PRD, `01-bim-workflow-overview`, `glossary`, `links/related-repos`, `08-revit-3d-workflow-diagram-plan`
- ✅ Publish the coordination workflow diagram in the README
- **Validation:** README displays the diagram; structure complete; first-version docs readable end to end.

### Phase 2 — Autodesk Coordination Workflow Documentation
**Goal:** The primary educational artifact is now a Revit-generated PNG diagram explaining the Autodesk BIM coordination workflow, and the repo explains that diagram in Markdown.

The repo must distinguish: BIM workflow · BIM coordination · MEP coordination · clash detection · model coordination · issue/RFI workflow · federated model handover.

- ✅ README displays the current Revit PNG export
- ✅ `docs/workflow-overview.md` explains the BIM-001 diagram
- ✅ `docs/coordination-feedback-loop.md` explains RFI + Issues loops returning to model authors
- ✅ Six callout pages under `docs/callouts/`
- ✅ `docs/revit-to-navisworks-workflow.md`, `docs/forma-model-coordination.md`, `docs/construction-vs-operations.md`
- ✅ `docs/coordination-risks/non-obvious-clashes.md`
- ✅ `docs/versioning-and-exports.md` + `diagrams/revit/README.md` (exports table)
- ✅ `.gitignore` excludes Autodesk binaries (`.rvt/.nwc/.nwf/.nwd`)

**Phase 2 acceptance criteria:**
- ✅ README displays the current Revit PNG export
- ✅ The exported PNG is stored under `diagrams/revit/exports/`
- ✅ The source Revit model is not committed to Git
- ✅ The six callouts each have their own Markdown page
- ✅ The CDE is explained as the backbone of the workflow
- ✅ RFIs and Issues are explained as feedback loops to model authors
- ✅ Forma Model Coordination is explained as collaboration-first
- ✅ Navisworks is explained as a desktop coordination workbench
- ✅ Construction vs Operations is explained
- ✅ Non-obvious coordination risks are documented
- ✅ Existing useful repo content is preserved

### Phase 3 — Worked Examples
**Goal:** Real AEC examples that apply the workflow.
- ✅ Harrismith Fire Station example
- ✅ BIM Clash Visual Atlas example
- **Validation:** Examples map cleanly to workflow stages.

### Phase 4 — Revit 3D Teaching Model
**Goal:** Build the 3D workflow diagram in Revit via Revit MCP.
- ✅ **Module 00 built** (`ad-coordination-workflow-v05.png`): 7 consultant + 4 contractor streams, CDE spine, Design Collaboration + Model Coordination, Federated Model, RFI + ISSUES loops, 6 numbered callouts.
- ✅ Explained in `docs/workflow-overview.md` (+ the six callout pages) and embedded in the README.
- ⏳ Future modules (e.g. Module 01 — Construction: shop drawings, fabrication) remain out of scope.
- **Validation:** Model matches the documented plan and the README/doc-09 narrative.

**Callout scheme (Module 00):** 1 Coordinated Models · 2 Design Collaboration · 3 Common Data Environment · 4 Contractor Models · 5 Model Coordination · 6 Federated Model · (loops) RFI, ISSUES.

## 13. Future Considerations

- Publish docs as a website or Triviron slide deck.
- Build the Phase 2 Revit 3D teaching model with the Revit MCP server.
- Integrate live Forma MCP / Revit MCP automation demonstrations.
- Expand the example library with more discipline-specific cases.
- Add a digital-twin / owner-handover deep dive.

## 14. Risks & Mitigations

| Risk | Mitigation |
|---|---|
| Copying branded/copyrighted diagrams | Author all diagrams originally (3D model built in Revit, then exported); review for originality before publishing. |
| Over-simplifying or, conversely, overbuilding | Keep MVP to clean first versions; defer deep content to Phase 2; follow "do not overbuild." |
| Reinforcing the "clash detection = BIM" misconception | Lead every relevant doc with the full hierarchy; state explicitly that clash detection is one step. |
| Jargon alienating beginners | Define terms in the glossary; explain on first use in each doc. |
| Content not reusable for slides/site | Keep docs short, structured, and consistently templated. |

## 15. Appendix

**Related CogStack repos** (see `links/related-repos.md`): Revit MCP server, Forma MCP server, Revit template-as-code, Modern BIM workflow decks, Harrismith BIM Learning Project, BIM Clash Visual Atlas.

**Core concept — workflow hierarchy:**

```
BIM Workflow
└─ BIM Coordination
   └─ Federated Models
      └─ MEP Coordination
         └─ Clash Detection
            └─ Issue Management
               └─ Model Updates
                  └─ Construction Support
                     └─ As-Built / Owner Handover
```
