# Glossary

Plain-language definitions of the key terms used across this repo. Where a term has a longer form, both are listed together.

---

**BIM** — Building Information Modeling. A way of designing and managing buildings using rich 3D models that carry data, not just geometry.

**CDE / Common Data Environment** — The single, shared cloud location where project information is stored, shared, and managed. The "one source of truth" for the team.

**Federated model** — Several discipline models brought together into one combined view for coordination. The originals stay separate; they are referenced together, not merged into one file.

**Native model** — A model in its original authoring format (for example, a Revit `.rvt` file), owned and edited by the team that created it.

**Linked model** — A model referenced into another model or coordination space so it can be seen alongside others, without being edited there.

**Coordination model** — A model (often a federated set) used specifically for reviewing how disciplines fit together and finding conflicts.

**Clash detection** — Automatically checking models to find where elements physically conflict or break clearance rules.

**Hard clash** — Two elements occupy the same physical space (e.g., a pipe passes through a beam).

**Clearance clash** — Elements don't physically touch, but are too close — violating a required gap for access, insulation, or maintenance.

**Workflow clash** — A scheduling/sequence conflict rather than a physical one (e.g., two trades need the same space at the same time during construction).

**MEP** — Mechanical, Electrical, and Plumbing. The building systems that are especially prone to conflicts and need careful coordination.

**Mechanical** — Heating, ventilation, and air conditioning (HVAC) systems — ducts, equipment, etc.

**Electrical** — Power, lighting, cable trays, conduits, and electrical equipment.

**Plumbing** — Water supply, drainage, and piping systems.

**Fire protection** — Fire safety systems such as sprinklers and fire piping. Often coordinated alongside MEP.

**Design Collaboration** — An Autodesk Forma capability for sharing and exchanging discipline models between teams during design.

**Model Coordination** — An Autodesk Forma capability for combining models and running automated clash detection in the cloud.

**Navisworks** — Autodesk Navisworks Manage. A desktop tool for federating models and running detailed clash detection and reviews.

**Revit** — Autodesk's main BIM authoring tool for architecture, structure, and MEP.

**Civil 3D** — Autodesk's authoring tool for civil and site engineering (terrain, roads, drainage).

**Issue** — A tracked problem (often a clash) assigned to a responsible team to resolve, with status and history.

**Viewpoint** — A saved camera position/view used to point reviewers to a specific spot in the model (for example, where a clash is).

**Shop drawing** — A detailed drawing used to fabricate and install elements on site, derived from coordinated models.

**As-built model** — A model updated to reflect what was actually built, including changes made during construction.

**Asset data** — Non-geometric information about building components (manufacturer, model, maintenance details) used after construction.

**Handover model** — The final model and data package delivered to the owner at project completion.

**Digital twin** — A live, data-connected model of a building used to operate and maintain it after handover.
