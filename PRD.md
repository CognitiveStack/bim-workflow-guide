# PRD: BIM Workflow Guide

## 1. Executive Summary

The **BIM Workflow Guide** repository is an educational source-of-truth that explains the modern Building Information Modeling (BIM) coordination workflow in plain, beginner-friendly language. It shows how separate discipline models move from design authoring tools (Revit, Civil 3D) into a Common Data Environment (CDE), become part of a federated model, pass through coordination and clash detection, and ultimately support construction and owner handover.

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
- ✅ `README.md` (the single-page guide: origin story, diagram walkthrough, six callouts, feedback loop, Forma, Navisworks, Construction vs Operations, coordination risks)
- ✅ `docs/glossary.md` (full first version)
- ✅ `links/related-repos.md` (full first version)
- ✅ `docs/08-revit-3d-workflow-diagram-plan.md` (full first version)

**Diagrams**
- ✅ `diagrams/revit/exports/ad-coordination-workflow-v06.png` (3D coordination diagram built in Revit via the pyRevit MCP; CDE-centric, contractor-neutral, with RFI + ISSUES loops) — the primary workflow illustration
- ✅ `README.md` embeds the 3D diagram and explains the 6 callouts + both loops (single page with in-page TOC anchors)

**Structure**
- ✅ Full repository directory and file structure scaffolded (stubs for remaining docs/diagrams/examples/links)

### Out of Scope (Future Phases)

- ❌ Fully written versions of all detailed topic docs (02–07) — stubs only in MVP
- ❌ Completed worked examples (Harrismith Fire Station, BIM Clash Visual Atlas) — placeholders only
- ✅ The Revit MCP-generated 3D teaching model — **Module 00 built** (`ad-coordination-workflow-v06`); further modules still out of scope
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
bim-workflow-guide/
├── README.md                       # THE single-page guide (all core content + TOC anchors)
├── PRD.md
├── .gitignore                      # excludes Autodesk binaries (.rvt/.nwc/.nwf/.nwd)
├── docs/
│   ├── glossary.md                 # reference
│   ├── versioning-and-exports.md   # reference
│   ├── 08-revit-3d-workflow-diagram-plan.md   # build runbook
│   └── 08-revit-build-prompt.md
├── diagrams/
│   └── revit/
│       ├── README.md              # exports table + versioning
│       └── exports/ad-coordination-workflow-v06.png
├── examples/
│   ├── harrismith-fire-station/README.md
│   └── bim-clash-visual-atlas/README.md
└── links/
    ├── related-repos.md
    └── learning-resources.md
```

**Design patterns:**
- **Single-page README** — all core learning content lives in `README.md` with a table of contents that jumps in-page (GitHub heading anchors); external links reserved for reference/appendix pages.
- **Diagram + explanation split** — the Revit-built 3D diagram is the visual; Markdown is the source of truth.
- **Original diagrams** — the coordination diagram is built as 3D geometry in Revit (via pyRevit MCP) and exported as PNG for the web.
- **Separation of concerns** — narrative in `README.md`, reference in `docs/` (glossary, versioning, build), visuals in `diagrams/`, applied cases in `examples/`, external pointers in `links/`.

## 7. Tools / Features (Content Modules)

| Module | Purpose |
|---|---|
| `README.md` | **The single-page guide**: origin story · diagram · how to read it · the six callouts · feedback loop · Forma Model Coordination · Revit→Navisworks · Construction vs Operations · non-obvious risks — with an in-page TOC |
| `docs/glossary.md` | Reference: plain definitions of key BIM terms |
| `docs/versioning-and-exports.md` | Reference: why PNG/Markdown are versioned and the .rvt is not |
| `docs/08-revit-3d-workflow-diagram-plan.md` / `-build-prompt` | Revit build runbook + Desktop prompt |
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
- ✅ Write README, PRD, glossary, `links/related-repos`, `08-revit-3d-workflow-diagram-plan` (early topic docs later consolidated into the single-page `README.md`)
- ✅ Publish the coordination workflow diagram in the README
- **Validation:** README displays the diagram; structure complete; first-version docs readable end to end.

### Phase 2 — Autodesk Coordination Workflow Documentation
**Goal:** The primary educational artifact is now a Revit-generated PNG diagram explaining the Autodesk BIM coordination workflow, and the repo explains that diagram in Markdown.

The repo must distinguish: BIM workflow · BIM coordination · MEP coordination · clash detection · model coordination · issue/RFI workflow · federated model handover.

- ✅ README displays the current Revit PNG export
- ✅ Diagram walkthrough, the six callouts, RFI + Issues feedback loops, Revit→Navisworks, Forma Model Coordination, Construction vs Operations, and non-obvious risks written up (originally separate pages; consolidated into the single-page `README.md` in Phase 5)
- ✅ `docs/versioning-and-exports.md` + `diagrams/revit/README.md` (exports table)
- ✅ `.gitignore` excludes Autodesk binaries (`.rvt/.nwc/.nwf/.nwd`)

**Phase 2 acceptance criteria:**
- ✅ README displays the current Revit PNG export
- ✅ The exported PNG is stored under `diagrams/revit/exports/`
- ✅ The source Revit model is not committed to Git
- ✅ Each of the six callouts is explained (now as sections of `README.md`)
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
- ✅ **Module 00 built** (`ad-coordination-workflow-v06.png`): 7 consultant + 4 contractor streams, CDE spine, Design Collaboration + Model Coordination, Federated Model, RFI + ISSUES loops, 6 numbered callouts.
- ✅ Explained in the single-page `README.md`.
- ⏳ Future modules (e.g. Module 01 — Construction: shop drawings, fabrication) remain out of scope.
- **Validation:** Model matches the documented plan and the README / guide narrative.

**Callout scheme (Module 00):** 1 Coordinated Models · 2 Design Collaboration · 3 Common Data Environment · 4 Contractor Models · 5 Model Coordination · 6 Federated Model · (loops) RFI, ISSUES.

### Phase 5 — Single-page README + repo rename
**Goal:** Make the front page *be* the guide, under a shorter repo name.
- ✅ All core narrative consolidated into one long-form page with an in-page table of contents (GitHub heading anchors).
- ✅ The single page **is the `README.md`** — a browser landing on the repo sees the whole guide immediately (no hop).
- ✅ Reference/appendix kept as separate pages: glossary, build runbook + prompt, versioning & exports, diagram/inspiration READMEs, PRD.
- ✅ Repo renamed `cogstack-bim-coordination-workflow` → **`bim-workflow-guide`** (org already namespaces it as `CognitiveStack/…`).
- **Validation:** All internal links and in-page anchors resolve; no orphaned pages.

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
