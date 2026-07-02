# Origin Story — How and Why I Built This

*This is the one page in this repo written in the first person. It's my personal account of where this project came from and how I modernized it.*

## Why I made this

I built the [Autodesk Coordination Workflow diagram](workflow-overview.md) to teach myself — and then others — how a modern BIM coordination workflow actually fits together. I kept hearing "BIM coordination" used as if it just meant clash detection, and I wanted a single picture that showed the whole thing: design, construction, operation, and the cloud that now runs through all of it.

## The image that inspired me

The spark was a diagram I saw in one of Jeffrey Pinheiro's videos — **The Revit Kid** — specifically ["3D Coordination Explained"](https://www.youtube.com/watch?v=2JOGvY9YplY&t=2991s) from his *BIM After Dark* series. The diagram itself was created by **Turner Construction** for their White Plains Hospital project:

![The original BIM coordination diagram that inspired this project](../diagrams/inspiration/turner-bim-coordination-white-plains-original.png)

*Original: "BIM Coordination at White Plains Hospital [MOD IV]", Turner Construction — as shown by The Revit Kid. (See [full credit](../diagrams/inspiration/README.md). This is a cleaned screenshot; the owner released it publicly and I've kept it clearly attributed.)*

I loved how it turned an abstract process into a 3D story you could actually follow. I wanted to build my own version — but modernized for how the work is done today.

## What the original showed

Look at the blue spine running across the middle of the original, labelled **"Turner"**. That spine is the **Construction Manager / General Contractor**. In that world, the CM/GC is the hub: they physically collect everyone's models, assemble them, run the coordination, and push information back out. Everything flows through *them*.

## How I modernized it

Here's the shift that made this interesting to me: **in a modern cloud workflow, that CM/GC spine is replaced by the cloud.**

In my version, the blue spine is the **Common Data Environment (CDE)**. Now, "CDE" is a general BIM term — it isn't Autodesk-specific. What makes my diagram *Autodesk-centric* is what sits **on** that spine: the two blue **Autodesk Forma** workflows — **[Design Collaboration](callouts/02-design-collaboration.md)** and **[Model Coordination](callouts/05-model-coordination.md)**. (Forma was formerly **ACC — Autodesk Construction Cloud**.)

So it's almost as if the CM/GC has become **redundant — or, more fairly, repurposed**. The coordinating *role* doesn't vanish, but the *spine* of the process is no longer a company standing in the middle passing files around. It's a shared cloud environment that stores, versions, routes, and records the information, with the Forma workflows doing the sharing and the clash-checking. (I dig into that reasoning more in the [workflow overview](workflow-overview.md).)

## The tension I keep coming back to

If you follow this workflow strictly, the **source of truth is the CDE** — the cloud, live and current. And that quietly contradicts a very old habit: handing out a **static set of Construction Documents** — Revit sheets frozen at a moment in time.

I don't think the answer is that Construction Documents are obsolete. They still do essential work: they're the **legal, payment, and scheduling** framework a project runs on. But the *process* around them is no longer siloed the way it used to be — it's far more collaborative and continuous than a set of printed sheets can represent. Holding both ideas at once — a live cloud source of truth **and** a frozen contractual document set — is, I think, one of the genuinely unresolved tensions in modern BIM. I'm keeping it here as an open question, not a verdict.

## How I actually built it (with limited Revit skills)

I'll be honest: my Revit skills aren't advanced enough to model this by hand. What made it possible was the **pyRevit MCP server** — [github.com/CognitiveStack/revit-mcp-server](https://github.com/CognitiveStack/revit-mcp-server) — which let me drive Revit programmatically and build the 3D diagram through an AI-assisted workflow instead of manual modelling.

If you want to see how that was done, the build is documented in the [Revit 3D diagram build runbook](08-revit-3d-workflow-diagram-plan.md) and the [Desktop build prompt](08-revit-build-prompt.md). The finished result — the modernized, de-branded, Autodesk-centric version — is explained in the [workflow overview](workflow-overview.md).

---

*See also: [workflow overview](workflow-overview.md) · [coordination feedback loop](coordination-feedback-loop.md) · [inspiration & credit](../diagrams/inspiration/README.md)*
