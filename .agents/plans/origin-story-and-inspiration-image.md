# Feature: First-Person Origin Story + Cleaned Inspiration Image

The following plan should be complete, but it's important that you validate the image crop **visually** and confirm the attribution wording with the user before finalizing. This is a documentation + image-asset task in a Markdown docs repo — there is no application code, so "tests" here mean link checks, image checks, and visual review.

## Feature Description

Add a **first-person, personal account** of how the author (Charles) created the Autodesk Coordination Workflow diagram. The page:

1. Shows the **original Revit-built diagram that inspired the project** (a screenshot from The Revit Kid's "BIM After Dark" YouTube series, of Turner Construction's "BIM Coordination at White Plains Hospital [MOD IV]" diagram), **cleaned up / cropped** to remove YouTube chrome.
2. **Credits** the original creator(s): The Revit Kid (Jeffrey Pinheiro) / "BIM After Dark", and the diagram's origin (Turner Construction).
3. Tells the **modernization story** in the author's voice: the blue "Turner" spine represented the Construction Manager / General Contractor; in a modern cloud workflow that role is replaced by the cloud — here the **Common Data Environment** — and made *Autodesk-centric* by the two Forma products **Design Collaboration** and **Model Coordination** (Forma was formerly ACC / Autodesk Construction Cloud). The CM/GC becomes, in theory, redundant or repurposed.
4. Explains the **single-source-of-truth tension**: if the workflow is strictly followed, the CDE (cloud) is the source of truth, which sits awkwardly against the traditional practice of issuing static **Construction Documents** (Revit sheets) — even though CDs still serve a vital legal, payment, and scheduling purpose.
5. Notes that the author built the 3D diagram despite limited Revit skills by using the **pyRevit MCP server** (https://github.com/CognitiveStack/revit-mcp-server).

## User Story

As a **reader of this educational repo**
I want to **read a personal, honest account of how and why this BIM workflow diagram was created and modernized**
So that **I understand the reasoning behind the Autodesk-centric, cloud-first design, its inspiration, and its real-world tensions — and I can trace the credit to the original creators.**

## Problem Statement

The repo currently explains *what* the diagram shows (Phase 2 docs) but not *why it exists* or *where it came from*. There is no attribution to the original inspiration, and no narrative of the modernization reasoning — which is itself one of the most interesting teaching points (the CM/GC → CDE shift). The only copy of the inspiration image is a raw YouTube screenshot with player chrome, living outside the repo.

## Solution Statement

Create a first-person `docs/origin-story.md` page, add a **cleaned/cropped** inspiration image under `diagrams/inspiration/` with an attribution README, and link the story from the README and `docs/index.md`. Clean the screenshot with ImageMagick (crop out the top black bar, bottom caption band, right-edge presenter picture-in-picture, and the like/comment icons); if the result is unsatisfactory, flag that a higher-resolution official copy may be obtainable.

## Feature Metadata

**Feature Type**: Enhancement (documentation + image asset)
**Estimated Complexity**: Low–Medium (image crop is the only fiddly part)
**Primary Systems Affected**: `docs/`, `diagrams/inspiration/` (new), `README.md`, `docs/index.md`
**Dependencies**: ImageMagick (`/usr/bin/convert`, `/usr/bin/identify` — confirmed present). No Pillow.

---

## CONTEXT REFERENCES

### Relevant Codebase Files — READ THESE BEFORE IMPLEMENTING

- `docs/workflow-overview.md` — Why: the finished diagram + the "Why Autodesk" and GC/CM notes already exist here; the origin story must be consistent with (and link to) it, not contradict it.
- `docs/index.md` — Why: the docs landing page; must add the origin story under "Start here".
- `README.md` (Documentation section, ~lines 60–95) — Why: add a link to the origin story; match existing link-list style.
- `diagrams/revit/README.md` — Why: pattern for a diagram-folder README with an attribution/exports table and an embedded image + caption. Mirror this for `diagrams/inspiration/README.md`.
- `docs/versioning-and-exports.md` — Why: the repo's asset philosophy ("PNG exports are the version-controlled visual artifacts"); the inspiration image follows the same lowercase-naming, committed-PNG convention.
- `docs/glossary.md` — Why: reuse exact term definitions (CDE, Federated Model, Design Collaboration, Model Coordination) so wording is consistent.
- `.gitignore` — Why: confirm PNGs are NOT ignored (only `.rvt/.nwc/...` are). The new PNG will commit fine.

### Source assets (outside the repo — on the Windows mount)

- `/mnt/c/Users/charles/Documents/Autodesk/projects/BIM/images/revit-kid-bim-workflow-diag/image.png` — the main 3D diagram screenshot, **1438x910**. This is the one to clean and embed.
- `.../image 2.png` (1185x874) and `.../image 3.png` (1213x841) — the two explanation slides (10-step process + coordination timeline). OPTIONAL to include; default is to leave them out of the origin story to keep it focused.

### New Files to Create

- `docs/origin-story.md` — the first-person account.
- `diagrams/inspiration/README.md` — attribution + source note for the inspiration image.
- `diagrams/inspiration/turner-bim-coordination-white-plains-original.png` — the cleaned/cropped inspiration image (copied into the repo from the crop output).

### Relevant Documentation — READ BEFORE IMPLEMENTING

- ImageMagick crop usage: `convert input.png -crop WxH+X+Y +repage output.png`
  - Why: `+repage` is required after `-crop` or the output keeps the original canvas offset (a common gotcha that leaves the "crop" looking uncropped).
- The Revit Kid / BIM After Dark: https://www.therevitkid.com and the "BIM After Dark" YouTube series (creator: Jeffrey Pinheiro).
  - Why: attribution target. **Confirm the exact video URL and preferred credit wording with the user before publishing** — do not invent a specific video title/URL.

### Patterns to Follow

**Diagram-folder README pattern** (from `diagrams/revit/README.md`): a short intro, a table (Diagram ID / File / Version / Purpose / Notes), then the embedded image with an italic caption, then a link to the explaining doc. Mirror this shape for `diagrams/inspiration/README.md` (swap the "Version" columns for "Source / Credit / Licence-note").

**Doc footer nav pattern** (used across `docs/*.md` and `docs/callouts/*`): end each page with an italic `*See also: [x](...) · [y](...)*` line. Apply to `origin-story.md`.

**Image caption pattern** (from `docs/workflow-overview.md` line under the image): image on its own line, then an italic caption line directly below.

**Lowercase, hyphenated asset filenames** (established convention: `ad-coordination-workflow-v05.png`). The new image filename must be lowercase-hyphenated.

**First-person voice**: this page is the ONLY one written in first person ("I"). All other docs are third-person/instructional. Keep the persona contained to this page and clearly framed as a personal account.

---

## IMPLEMENTATION PLAN

### Phase 1: Foundation — Clean the inspiration image

Produce a clean, chrome-free crop of the screenshot and place it in the repo.

**Tasks:**
- Inspect the screenshot to confirm crop boundaries (top black bar; bottom "Draft / BIM Coordination at White Pains Hospital" caption band; right-edge presenter picture-in-picture; bottom-right like/dislike/comment icons + Turner logo).
- Run an ImageMagick crop; **view the result and iterate** until only the 3D diagram (DESIGN → CONSTRUCTION → OPERATION, all arrows and callouts) remains.
- Copy the accepted crop into `diagrams/inspiration/` with a lowercase-hyphenated name.

### Phase 2: Core Implementation — Write the origin story + attribution

**Tasks:**
- Create `diagrams/inspiration/README.md` (attribution + source).
- Create `docs/origin-story.md` (first-person narrative embedding the cleaned image).

### Phase 3: Integration — Link it in

**Tasks:**
- Add the origin story to `docs/index.md` ("Start here").
- Add a link in `README.md` Documentation section.

### Phase 4: Validation

**Tasks:**
- Verify image dimensions/that the crop removed chrome (visual).
- Run the internal-link checker (all relative `.md`/`.png` links resolve).
- Confirm the embedded image renders and the caption/credit are present.
- Confirm attribution wording with the user.

---

## STEP-BY-STEP TASKS

Execute in order.

### CREATE `diagrams/inspiration/` (cleaned image)

- **IMPLEMENT**: First-pass crop of the source screenshot removing YouTube chrome. Starting estimate for the 1438x910 image (iterate from here):
  - `convert "/mnt/c/Users/charles/Documents/Autodesk/projects/BIM/images/revit-kid-bim-workflow-diag/image.png" -crop 1360x775+0+38 +repage /tmp/insp-crop.png`
  - Then **Read /tmp/insp-crop.png visually** and adjust `WxH+X+Y`: trim more from the right (`W`) if the presenter thumbnail remains; increase `Y` / reduce `H` if the bottom caption band or icons remain; reduce `Y` if the top of the "DESIGN/CONSTRUCTION/OPERATION" labels is clipped.
  - When satisfied, copy to the repo: `cp /tmp/insp-crop.png diagrams/inspiration/turner-bim-coordination-white-plains-original.png`
- **PATTERN**: Asset naming mirrors `diagrams/revit/exports/ad-coordination-workflow-v05.png` (lowercase, hyphenated).
- **IMPORTS**: ImageMagick `convert` (present at `/usr/bin/convert`).
- **GOTCHA**: `+repage` is mandatory after `-crop`, or the PNG keeps a virtual canvas and appears uncropped when embedded. The source has spaces in sibling filenames ("image 2.png") — always quote paths. Do NOT modify the originals on `/mnt/c/...`; only read them.
- **GOTCHA (copyright)**: This is a third-party (Turner) diagram surfaced by The Revit Kid. Keep it clearly attributed and framed as educational reference. Do not remove/obscure authorship to pass it off as original.
- **VALIDATE**: `identify diagrams/inspiration/turner-bim-coordination-white-plains-original.png` (confirm it exists and dimensions match the accepted crop, not 1438x910).

### CREATE `diagrams/inspiration/README.md`

- **IMPLEMENT**: Short attribution page. Table with columns: File / Source / Credit / Note. Embed the cleaned image with an italic caption. State: original diagram is Turner Construction's "BIM Coordination at White Plains Hospital [MOD IV]" (Draft 03.07.2019); brought to the author's attention via **The Revit Kid (Jeffrey Pinheiro), "BIM After Dark" YouTube series**; screenshot cleaned for educational use; a higher-resolution official copy may be substituted if found. Link to `../../docs/origin-story.md`.
- **PATTERN**: Mirror `diagrams/revit/README.md` structure.
- **GOTCHA**: Leave the exact YouTube video URL as a clearly-marked placeholder (`<!-- confirm exact video URL -->`) until the user confirms it — do not fabricate a specific link.
- **VALIDATE**: link checker (below) reports no broken links from this file.

### CREATE `docs/origin-story.md`

- **IMPLEMENT**: First-person narrative with roughly these sections:
  1. **Intro** — "I built this diagram to teach myself the modern Autodesk BIM coordination workflow…" (why it exists).
  2. **The image that inspired me** — embed `../diagrams/inspiration/turner-bim-coordination-white-plains-original.png` with caption + credit line to The Revit Kid / BIM After Dark and Turner. Link to `../diagrams/inspiration/README.md`.
  3. **What the original showed** — the blue "Turner" spine = the Construction Manager / General Contractor coordinating everyone's models.
  4. **How I modernized it** — in a cloud workflow, that CM/GC spine is replaced by the **cloud**; in my Autodesk-centric version it's the **Common Data Environment** (note: "CDE" is a general BIM term). What makes it *Autodesk-centric* is the two **Forma** products shown in blue — **Design Collaboration** and **Model Coordination** (Forma was formerly **ACC / Autodesk Construction Cloud**). In theory the CM/GC becomes redundant — or repurposed.
  5. **The single-source-of-truth tension** — if the workflow is strictly followed, the **CDE (cloud) is the source of truth**. That sits awkwardly against issuing static **Construction Documents** (Revit sheets): the process is no longer siloed, it's collaborative. Yet CDs still serve a vital **legal, payment, and scheduling** framework. (Present as an honest, unresolved tension, not a verdict.)
  6. **How I built it (with limited Revit skills)** — I used the **pyRevit MCP server** (https://github.com/CognitiveStack/revit-mcp-server) to author the 3D diagram programmatically; link to `08-revit-3d-workflow-diagram-plan.md` and `08-revit-build-prompt.md`.
  7. **Footer nav** — `*See also: [workflow overview](workflow-overview.md) · [feedback loop](coordination-feedback-loop.md) · [inspiration & credit](../diagrams/inspiration/README.md)*`
- **PATTERN**: Reuse glossary-consistent terms (CDE, Federated Model, Design Collaboration, Model Coordination). Match the caption/footer patterns noted above. Keep first person contained to this page.
- **GOTCHA**: Do not contradict `workflow-overview.md`'s existing "Why Autodesk" and GC/CM notes — this page is the *personal* version of that reasoning; cross-link rather than duplicate verbatim.
- **VALIDATE**: link checker passes; `grep -n "revit-mcp-server" docs/origin-story.md` shows the MCP credit; image path resolves.

### UPDATE `docs/index.md`

- **IMPLEMENT**: Under "Start here", add `- [Origin Story — how and why I built this](origin-story.md)`.
- **VALIDATE**: link checker passes.

### UPDATE `README.md`

- **IMPLEMENT**: In the Documentation "Start here" (or "Background & build") list, add `- [Origin Story — how I built and modernized this](docs/origin-story.md)`.
- **PATTERN**: Match the existing bullet-link style in the Documentation section.
- **VALIDATE**: link checker passes.

---

## TESTING STRATEGY

This is a docs repo; "tests" are structural/visual checks, not unit tests.

### Structural checks
- Internal markdown link resolution across all `.md` files (reuse the Phase 2 link-checker shell loop that scans `](...md|png)` relative links).
- Image existence + non-original dimensions (`identify`).

### Visual checks
- Read the cropped PNG in-tool and confirm: no top black bar, no bottom caption band, no right-edge presenter thumbnail, no like/comment/Turner icons, and the full diagram (all callouts 1–10, DESIGN/CONSTRUCTION/OPERATION labels) is intact.
- Confirm the embedded image and caption render on the origin-story page.

### Edge cases
- Crop too aggressive (clips DESIGN label or callout 10 / consolidated model on the right) → widen/raise the crop.
- Crop leaves a sliver of the presenter PiP on the right → reduce width.
- Spaces in source sibling filenames → ensure all paths are quoted.
- If the screenshot is simply too low-quality when cropped → STOP and surface to the user the option to source a higher-res official copy (documented as acceptable in the inspiration README).

---

## VALIDATION COMMANDS

### Level 1: Asset check
```
identify diagrams/inspiration/turner-bim-coordination-white-plains-original.png
```

### Level 2: Link check (all internal md/png links resolve)
```
cd /home/charles/projects/cogstack-bim-coordination-workflow
while IFS= read -r f; do d=$(dirname "$f"); \
  grep -oE '\]\(([^)]+\.(md|png))\)' "$f" | sed -E 's/^\]\(//; s/\)$//' | \
  while IFS= read -r l; do t="${l%%#*}"; [ -z "$t" ] && continue; \
  [ -e "$d/$t" ] || echo "BROKEN: $f -> $l"; done; \
done < <(find . -name '*.md' -not -path './.git/*' -not -path './.claude/*' -not -path './.agents/*'); echo "done"
```

### Level 3: Content presence
```
grep -n "revit-mcp-server" docs/origin-story.md
grep -ni "revit kid\|bim after dark" docs/origin-story.md diagrams/inspiration/README.md
grep -n "origin-story" README.md docs/index.md
```

### Level 4: Manual / visual
- Read `diagrams/inspiration/turner-bim-coordination-white-plains-original.png` in-tool and confirm chrome is gone and the diagram is intact.
- Confirm on GitHub (after push) that the origin-story image renders.

---

## ACCEPTANCE CRITERIA

- [ ] A cleaned, chrome-free inspiration image exists at `diagrams/inspiration/turner-bim-coordination-white-plains-original.png`.
- [ ] `docs/origin-story.md` is written in first person and tells the inspiration + modernization story, including: Turner spine = CM/GC; cloud/CDE replaces it; Autodesk-centric via Design Collaboration + Model Coordination (Forma, formerly ACC); CM/GC redundant/repurposed; CDE-as-source-of-truth vs static Construction Documents (legal/payment/scheduling) tension; pyRevit MCP server credit + link.
- [ ] Clear attribution to The Revit Kid / "BIM After Dark" (Jeffrey Pinheiro) and to Turner Construction as the diagram's origin.
- [ ] `diagrams/inspiration/README.md` records source + credit + educational-use note.
- [ ] Origin story linked from `README.md` and `docs/index.md`.
- [ ] All internal links resolve; image renders.
- [ ] Attribution wording (and exact video URL) confirmed with the user before final publish.
- [ ] Existing docs unchanged in meaning; no contradiction with `workflow-overview.md`.

---

## COMPLETION CHECKLIST

- [ ] Image cropped and visually verified clean
- [ ] Image copied into `diagrams/inspiration/`
- [ ] `diagrams/inspiration/README.md` created
- [ ] `docs/origin-story.md` created (first person)
- [ ] `README.md` + `docs/index.md` updated
- [ ] Link checker passes with zero broken links
- [ ] Content-presence greps pass
- [ ] Visual review of rendered image done
- [ ] Attribution confirmed with user
- [ ] Committed (as Charles, no Claude co-author) and pushed on request

---

## NOTES

**Design decisions / assumptions:**
- Inspiration image goes in a new `diagrams/inspiration/` folder (kept separate from `diagrams/revit/exports/`, which is for the author's *own* Revit output). This keeps third-party reference assets clearly distinct from original work.
- Filename `turner-bim-coordination-white-plains-original.png` names the *diagram's true origin* (Turner) rather than "revit-kid", since The Revit Kid surfaced it but Turner authored it. Open to `revit-kid-bim-workflow-original.png` if the user prefers to foreground where they found it.
- The two explanation slides (`image 2/3.png`) are **left out** by default to keep the story focused; they can be added later (e.g. as an appendix) if wanted.
- First person is deliberately quarantined to this single page.

**Key risks / things to confirm with the user (surface before publishing):**
1. **Exact credit + video URL** for The Revit Kid / BIM After Dark — I will not invent a specific video link; needs the user's confirmation. Creator name assumed to be Jeffrey Pinheiro — confirm.
2. **Copyright/permission** — the diagram is Turner's, surfaced by The Revit Kid. The user states it was publicly released; educational use with attribution is the approach. Confirm the user is comfortable committing the (cleaned) third-party image, or prefers to link out to an official copy instead of hosting it.
3. **Image quality** — the source is a video screenshot; the crop may still look soft. Option to substitute a higher-res official copy later is baked into the inspiration README.
4. **Filename/foregrounding** — Turner-first vs Revit-Kid-first naming (see above).

**Confidence score for one-pass success: 8/10.** The Markdown is fully specified; the only real variable is the visual crop, which needs one or two iterate-and-view cycles, and the attribution wording, which needs a one-line confirmation from the user.
