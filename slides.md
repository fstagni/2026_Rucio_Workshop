---
colorSchema: light
favicon: /public/images/diracx-logo-square.svg
color: diracx-light
layout: cover
routerMode: hash
title: DiracGrid software stacks
theme: neversink
neversink_string: "DiracGrid @ RCW26"
download: true
---

# DiracGrid software stacks
## Status, DiracX updates and plans

**Federico Stagni** <Email v="federico.stagni@cern.ch" />

DiracGrid Technical Coordinator

<br>

26–30 October 2026, IN2P3 Computing Centre, Lyon

<a href="https://indico.cern.ch/event/1628935/" class="ns-c-iconlink"><mdi-open-in-new />indico.cern.ch/event/1628935</a>

---
layout: top-title
color: diracx-light
align: cm
title: diracgrid
---

:: title ::

# What is DiracGrid, actually?

:: content ::

- An "**interware**" (a tool for doing distributed computing), started by LHCb
- Today used by a few dozens communities, for managing **jobs** (via pilots), **data**, **productions**, **dataset transfers**, ...

The DiracGrid project develops and maintains the whole software stack:
- [DIRAC](https://github.com/DIRACGrid/DIRAC) (the "legacy" workhorse)
- [DiracX](https://github.com/DIRACGrid/diracx) (the cloud-native rewrite)

<br>

In general, DIRAC has a very active community of users and developers:
- Apart from the regular zoom meetings, we meet at **3 hackathons per year**, plus one **workshop**
- The [12th Dirac(X) Users' Workshop](https://indico.cern.ch/event/1588323/) was just held, 13–16 October 2026 in Prague
  - most of what follows comes from there

---
layout: top-title
color: diracx-light
align: cm
title: since-last-year
---

:: title ::

# Since the last Rucio workshop

:: content ::

Since we met one year ago (8th Rucio Community Workshop):

- **CMS and FCC joined the effort** (summer 2026) – bringing new requirements, scale, and energy to the project
- **New development process** adopted since January 2026
  - SCRUM-based, with 2-week sprints and regular checkpoint meetings
- **ADRs for everything** – Architecture Design Records guide every major decision before code is written
  - Transparent, reviewable, community-driven design process

<br>

<div class="flex justify-center items-center gap-8 mt-4">
  <img src="/public/images/DIRAC-logo-extended.png" class="h-14">
  <span class="text-3xl">→</span>
  <img src="/public/images/diracx-logo-full.svg" class="h-14 diracx-logo">
</div>

---
layout: top-title-two-cols
color: diracx-light
align: cm-lm-lm
title: releases
columns: is-6
---

:: title ::

# Releases for the DiracGrid stacks

:: left ::

**DIRAC**
- v9.1, v9.0, v8.0 in maintenance
  - security fixes, and performance fixes when needed
- [github.com/DIRACGrid/DIRAC/releases](https://github.com/DIRACGrid/DIRAC/releases)

**DiracX**
- 23 releases since the first official one (Oct 2025)
- latest: **v0.6.1** (9 October 2026)
- [github.com/DIRACGrid/diracx/releases](https://github.com/DIRACGrid/diracx/releases)

:: right ::

<img src="/public/images/duw12/directions/architecture.png" class="w-full mb-4">

<AdmonitionType type='important' >
DIRAC and DiracX will live together for a while. One functionality at a time, we'll eventually migrate all from DIRAC to DiracX.
</AdmonitionType>

<AdmonitionType type='note' >
"Adopt what already exists in DiracX; DIRAC is only patched, so that DiracX can progress".
</AdmonitionType>

---
layout: top-title-two-cols
color: diracx-light
align: cm-lm-lm
title: dev-model
columns: is-4
---

:: title ::

# The development model

:: left ::

**SCRUM since 21 January 2026**
- 2-week sprints; planning and refinement in a weekly `DDev` meeting
- Monthly `DOps` meeting with the community representatives: where use cases are shared, and priorities agreed

:: right ::

<img src="/public/images/duw12/directions/process.png" class="w-4/5 mx-auto">

**Large changes** start with a **proof of concept**, then an **ADR** that the other developers approve (ADRs and roadmap are public)

*"Individuals and interactions over processes and tools": the process is a guide, not a rule, and it adapts as we learn.*

<span class="stamp">From "**DiracX developments: directions**" · A. Boyer · <a href="https://indico.cern.ch/event/1588323/contributions/7301774/">DUW12</a></span>

---
layout: top-title
color: diracx-light
align: cm
title: numbers
---

:: title ::

# The project in numbers

:: content ::

- **36 contributors** since the last workshop (10 to 18 in any given month, almost all part-time: about 5–6 FTEs in total, LHCb core developers included)
- **634 pull requests** merged across all DIRACGrid repositories since the last workshop (367 DIRAC, 261 DiracX), from **9 communities**; 17 new contributors
- The backlog is **shrinking**: 295 → 195 open issues since January 2026, with ~37 issues closed per month
- Known bottlenecks: **specification** and **review** (two people give three quarters of first reviews)
  - clear ADRs with scenario tests are what an implementer (human or AI agent) needs

<span class="stamp">From "**DiracX developments: directions**" · A. Boyer · <a href="https://indico.cern.ch/event/1588323/contributions/7301774/">DUW12</a></span>

---
layout: top-title
color: diracx-light
align: cm
title: ai-landscape
---

:: title ::

# AI is changing the landscape (also) for us

:: content ::

<AdmonitionType type='note' >
"AI's primary role in software development is that of an amplifier." -- DORA 2025, State of AI-assisted Software Development
</AdmonitionType>

- **Writing code got cheap**: spikes and proofs of concept are easier to try than ever
- But **deciding what to build, and checking it, did not get cheaper**
  - It does not change our process: it shows its weak points sooner
- Vague specification → verbose, AI-generated issues that go stale
  - a clear **ADR with a scenario test** is what an agent -- or a newcomer -- can implement
- The **review bottleneck** grows: more code means more to read, by the same two people
- **A new kind of user**: DiracX speaks HTTP and OAuth2, so an agent can use it through MCP
  - IHEP already operates DIRAC with an agent and MCP (DUW12)

<span class="stamp">From "**DiracX developments: directions**" · A. Boyer · <a href="https://indico.cern.ch/event/1588323/contributions/7301774/">DUW12</a></span>

---
layout: top-title-two-cols
color: diracx-light
align: cm-lm-lm
title: not-a-port
columns: is-8
---

:: title ::

# Not a port: a reimplementation

:: left ::

**Future clients**
- A DMS: a DIRAC client calls DiracX instead of DIRAC, over the same databases
- RSS: the read side is already in DiracX; DIRAC's adapter is in review

**A new data model**
- The spine: **workgraph**, **transformations**, **parcels**
- New requirements need new tables and new logic; DIRAC's WMS is used as it is, as a backend

**Standard protocols**
- Systems internal to DIRAC give way to standards: **OpenTelemetry** monitoring, **OIDC** identity, **S3** sandboxes

<span class="stamp">From "**DiracX developments: directions**" · A. Boyer · <a href="https://indico.cern.ch/event/1588323/contributions/7301774/">DUW12</a></span>

:: right ::

<img src="/public/images/duw12/directions/clients.png" class="h-32 mx-auto mb-2">
<img src="/public/images/duw12/directions/data_model.png" class="h-28 mx-auto mb-2">
<img src="/public/images/duw12/directions/protocols.png" class="h-16 mx-auto">

---
layout: section
color: diracx
title: ts
---

# The DiracX Transformation System

## Workgraphs, transformations and parcels

---
layout: top-title-two-cols
color: diracx-light
align: cm-lm-lm
title: ts-what
columns: is-6
---

:: title ::

# Transformation System: what it is (and what it is not)

:: left ::

<AdmonitionType type='important' >
Not the DIRAC Transformation System with a new coat of paint: same underpinnings and lessons learned, but a different shape.
</AdmonitionType>

- **One system where DIRAC had three**: Transformation, Production, and the "job" half of the WMS
- **Not** only for centrally-run activity: "user jobs" change too
- All in the ADRs: [DX-ADR-002 → 009](https://diracx.diracgrid.org/en/latest/adr/), with [explanations](https://diracx.diracgrid.org/en/latest/user/explanations/transformation-system/) and a [playground](https://diracx.diracgrid.org/en/latest/playground/)

<span class="stamp">From "The DiracX Transformation System" · C. Burr · <a href="https://indico.cern.ch/event/1588323/contributions/7264643/">DUW12</a></span>

:: right ::

DIRAC's WMS is two distinct abstractions, and DiracX pulls them apart:

<img src="/public/images/duw12/ts/wms.svg" class="h-52 mx-auto mt-2">

- **Pilots** (getting hold of resources) → Compute Backends
- **Jobs** (describing the work to run) → Transformation System

---
layout: top-title-two-cols
color: diracx-light
align: cm-lm-lm
title: ts-model
columns: is-3
---

:: title ::

# Transformation System: the model

:: left ::

> A **workgraph** is a directed acyclic graph of **transformations**. Each transformation maintains a pool of **inputs**: a **feeder** tops up the pool from the experiment's metadata catalogue, a **packer** groups pooled inputs into **parcels**, and a **dispatcher** hands each parcel to a compute or data **backend**, which executes it as a job or a request. -- DX-ADR-002

:: right ::

- **Workgraph**: the entire thing, what DIRAC called a *production*; its status is constrained by its members' (start, scout, drain, halt, cancel)
- **Transformation**: applies *one* operation to a pool of inputs (embarrassingly parallel); **compute** (runs jobs) or **data** (runs requests: copy or remove replicas)
- **Inputs**: processed *exactly once, or not at all* (`Unassigned` → `Assigned` → `Processed`/`NotProcessed`)
- **Feeder**: external ones bring work in from outside the workgraph (metadata queries, run ranges, seeds) – *this is where your catalogue plugs in*; internal ones follow the edges of the graph
- **Packer**: groups inputs into parcels (~3 GB, same storage, same run, ...); a parcel is **never retried**: a failure sends its *inputs* back to the pool
- **Dispatcher**: chooses the backend (native pilots, push to HPC, HTCondor, legacy DIRAC, ...); user jobs take exactly the same path

<span class="stamp">From "The DiracX Transformation System" · C. Burr · <a href="https://indico.cern.ch/event/1588323/contributions/7264643/">DUW12</a></span>

---
layout: top-title
color: diracx-light
align: cm
title: ts-pictures
---

:: title ::

# Transformation System: the model, in pictures

:: content ::

<div class="flex justify-center gap-8">
  <img src="/public/images/duw12/ts/generic-proc-wg.svg" class="h-44">
  <img src="/public/images/duw12/ts/generic-sim-wg.svg" class="h-44">
</div>

The two generic workgraphs (data processing: *process + merge*; simulation: *produce + process + merge*), and the workgraph state machine:

<img src="/public/images/duw12/ts/states.svg" class="w-4/5 mx-auto mt-2">

<span class="stamp">From "The DiracX Transformation System" · C. Burr · <a href="https://indico.cern.ch/event/1588323/contributions/7264643/">DUW12</a></span>

---
layout: top-title
color: diracx-light
align: cm
title: ts-usecases
---

:: title ::

## Transformation System: does it do everything we need?

:: content ::

Everything **composes**: any number of transformations, any shape of graph. Each use case changes only the shape of the graph, and which feeder, packer, hooks and actions are plugged in. Examples from DUW12:

- **Forking outputs**: one output, many consumers, each tracking its own progress
- **Removing replicas after N uses**: a data transformation whose packer delays each file until all consumers have processed it
- **Correlated processing**: e.g. a packer looks up each file's RAW ancestor and adds it to the parcel
- **Staging from tape**: a data transformation stages; the packer delays each file until on buffer
- **Scouting**: run on a small sample first, for resource estimation and reliability, with (possibly manual) approval actions
- **Retrying and splitting**: a hook decides each failed input's fate; partially-processed inputs are split

<AdmonitionType type='note' >
Have a use case that doesn't fit? The <a href="https://github.com/DIRACGrid/diracx/pull/1042">ADRs</a> are still open for input.
</AdmonitionType>

<span class="stamp">From "The DiracX Transformation System" · C. Burr · <a href="https://indico.cern.ch/event/1588323/contributions/7264643/">DUW12</a></span>

---
layout: section
color: diracx
title: dms
---

# Data Management for DiracX

---
layout: top-title-two-cols
color: diracx-light
align: cm-lm-lm
title: dms-elephant
columns: is-7
---

:: title ::

# The elephant in the room

:: left ::

<AdmonitionType type='important' >
diracx-Rucio integration is clearly a need for some communities.
</AdmonitionType>

<AdmonitionType type='important' >
DIRAC data management capabilities are NOT going away. Quite the opposite, actually!
</AdmonitionType>

**Where Rucio fits in DiracX:**
- As a **catalog**: it's just like another one
- As a **data movement orchestrator**: external to DiracX, triggered by the Transformation System

The DUW12 discussion focused on **use cases, not technicalities**: the input collected there will drive the future Data Management ADR!

<span class="stamp">From "Data Management for DiracX" · C. Haen · <a href="https://indico.cern.ch/event/1588323/contributions/7286647/">DUW12</a></span>

:: right ::

<img src="/public/images/duw12/dms/elephant.png" class="w-3/5 mx-auto">

---
layout: top-title-two-cols
color: diracx-light
align: cm-lt-lt
title: dms-fc
columns: is-6
---

:: title ::

# Data Management: the File Catalog

:: left ::

- The `FileCatalog` class **abstracts the actual catalog** behind, and defines the interface
  - used by everything: jobs, CLI, agents, etc.
  - **multiple file catalogs** can be used together (`FCConditionParser` – LHCb does)
- The **Dirac File Catalog (DFC)**: very *POSIX-like* (directories, files, replicas), with attributes, metadata, datasets, and a security manager for permissions
  - **Multi-VO**: GridPP has implemented Multi-VO metadata (and DiracX *must* be multi-VO)

<AdmonitionType type='tip' >
The DFC will be in DiracX, but <strong>the form is still to be decided</strong>: it needs input from every community.
</AdmonitionType>

:: right ::

<img src="/public/images/duw12/dms/file_catalog_multiple.png" class="w-11/12 mx-auto">

<span class="stamp">From "Data Management for DiracX" · C. Haen · <a href="https://indico.cern.ch/event/1588323/contributions/7286647/">DUW12</a></span>

---
layout: top-title-two-cols
color: diracx-light
align: cm-lt-lt
title: dms-se
columns: is-6
---

:: title ::

# Data Management: Storage Elements and transfers

:: left ::

- **Storage Elements**: the concepts stay (abstraction of storage endpoints, protocol resolution from LFN to URL)
- **Protocols & GFAL2**: the concepts stay; arguing for a *canonical* way to handle data access on the grid (used by DIRAC, Rucio, sites...)
- **FTS**: DIRAC is capable of third-party-copy natively (with caveats)
  - open question: delegate everything to FTS? And how do you use it (multiple instances, activities, shares)?

From these building blocks, the future plans: data popularity, storage usage reports, data placement, FC/SE consistency, analytics

:: right ::

Storage Elements, from a single endpoint to SE bases and groups:

<img src="/public/images/duw12/dms/se_base.png" class="h-36 mx-auto">

and the protocols, from LFN to URL:

<img src="/public/images/duw12/dms/protocols.png" class="h-20 mx-auto">

<span class="stamp">From "Data Management for DiracX" · C. Haen · <a href="https://indico.cern.ch/event/1588323/contributions/7286647/">DUW12</a></span>

---
layout: side-title
side: left
color: diracx-light
titlewidth: is-5
align: cm-lm
title: dirac-rucio
---

:: title ::

 <img id="DiracX" src="/public/images/diracx-logo-full.svg" class="mx-auto w-2/5"> </img> <img id="Rucio" src="/public/images/rucio_horizontaled_black.svg" class="mx-auto w-3/5"> </img>

# DIRAC(X) and Rucio

:: content ::

- Few communities (Belle2, CTAO, few institutes in GridPP, ...) have been using, or will soon use, DIRAC(X) and Rucio together, with (_en-gros_):
  - DIRAC(X) as **WMS** (so, not using DIRAC's DMS)
  - Rucio as **DMS**
- There are also exploratory works on using parts of DIRAC that are not the WMS

There is also a dedicated [mattermost channel](https://mattermost.web.cern.ch/diracx/channels/rucio---dirac)

---
layout: top-title
color: diracx-light
align: cm
title: how-together
---

:: title ::

# How DIRAC and Rucio work together

:: content ::

The entry point is DIRAC's `RucioFileCatalog`, an implementation of the `FileCatalog` "abstract" class (DIRAC has few different implementations of the same class, and you can `register_file()` to more than 1 catalog at the same time)
- in DIRAC since 2021
- by now it supports *Multi VO* and *Rucio metadata*
- The synchronization between DIRAC and Rucio is done via DIRAC agents

Once the data is in the Rucio catalog, all the replication policies, 3rd party copy are handled by Rucio subscriptions and rules.

This also means that:
- Admins still update the DIRAC configuration
- No change for the download/upload from jobs: still done via DIRAC's `DataManager`

---
layout: top-title
color: diracx-light
align: cm
title: duw12-rest
---

:: title ::

# DUW12: the rest of the workshop

:: content ::

- **Deployments**: K3S for Belle2, testbed infrastructure at IN2P3, non-Kubernetes deployments
- **AI-Assisted DIRAC Deployment and Operations at IHEP**: DiracX speaks HTTP and OAuth2, so an agent can use it (via MCP)
- **RSS in DIRAC and DiracX**: the Resource Status Service, shared between the stacks
- **No certificate authentication**: the path towards tokens (goodbye X509)
- Community status reports: GridPP, Belle2, CMS, LHCb, JINR, CTAO, iLCDirac + FCC, IHEP, EGI and GreenDIGIT
  - CMS: the use case for a non-DiracX WMS, and how this affects DiracX developments

<AdmonitionType type='note' >
All materials are (or will be) linked from the <a href="https://indico.cern.ch/event/1588323/timetable/">indico timetable</a>.
</AdmonitionType>

---
layout: top-title
color: diracx-light
align: cm
title: roadmap
---

:: title ::

# The roadmap

:: content ::

<img src="/public/images/duw12/directions/roadmap.png" class="w-4/5 mx-auto">

<AdmonitionType type='important' >
Priorities, not commitments. New requirements can reorder this page, and the team writes the detailed plan.
</AdmonitionType>

<span class="stamp">From "**DiracX developments: directions**" · A. Boyer · <a href="https://indico.cern.ch/event/1588323/contributions/7301774/">DUW12</a></span>

---
layout: top-title-two-cols
color: diracx-light
align: cm-lm-lm
title: installations
columns: is-6
---

:: title ::

# If you run an installation today

:: left ::

What you can count on:

- **DIRAC keeps running**, with security patches and performance fixes when needed
- You choose **when to switch each component**, usually at a shutdown; DIRAC and DiracX run in parallel meanwhile
- **No data migration** for anything but the transformation system, which has its own tables
- Your **extension keeps working** on DIRAC while you move
- **Increments to test**, shown at DOps whenever a sprint delivers one

<span class="stamp">From "**DiracX developments: directions**" · A. Boyer · <a href="https://indico.cern.ch/event/1588323/contributions/7301774/">DUW12</a></span>

:: right ::

<img src="/public/images/duw12/directions/increment_cycle.png" class="w-4/5 mx-auto">

---
layout: top-title-two-cols
align: cm-cm-lm
color: diracx-light
columns: is-4
title: summary
---
:: title ::

# Summary

:: left ::

<img id="DiracX" src="/public/images/diracx-logo-square.svg" class="mx-auto w-4/5"> </img>

:: right ::

<ul class="text-base">
  <li>DIRAC and Rucio have been used as complementary tools for exploiting distributed computing resources for a few years already.
    <ul class="text-sm">
      <li>The collaboration is meant to continue!</li>
      <li>DiracX will ease the interoperability with Rucio and/or any other tool out there</li>
      <li>Rucio as a catalog ("just like another one") or as a data movement orchestrator, triggered by the Transformation System</li>
    </ul>
  </li>
  <li>DiracX is "the neXt Dirac incarnation", ensuring the future of the widely used DIRAC.
    <ul class="text-sm">
      <li>LHCb runs it in production; CMS and FCC are joining</li>
      <li>Not a port: a reimplementation. You move one component at a time, and DIRAC is only patched meanwhile</li>
      <li>Transformation System first in line, Data Management next: your input will drive the future ADRs</li>
    </ul>
  </li>
</ul>

---
layout: section
color: diracx
title: Questions
---

# Questions?

---
layout: credits
color: diracx
loop: true
speed: 1.0
title: credits/people
---

<div class="grid text-size-4 grid-cols-3 w-3/4 gap-y-10 auto-rows-min ml-auto mr-auto">
    <div class="grid-item text-center mr-0- col-span-3">
        <strong>People</strong><br>
    </div>
    <div class="grid-item text-right mr-4 col-span-1">
        <strong>Current Developers, maintainers, supporters</strong>
    </div>
    <div class="grid-item col-span-2">
        Chris Burr <i>CERN, LHCb</i><br/>
        Christophe Haen <i>CERN, LHCb</i><br/>
        Alexandre Boyer <i>CERN, LHCb</i><br/>
        Natthan Piggoux <i>LUPM (FR), CTA</i><br/>
        Cedric Serfon <i>Brookhaven National Laboratory (US), Belle2</i><br/>
        Ryunosuke O'Neil <i>CERN, LHCb</i><br/>
        Daniela Bauer <i>Imperial college (UK), GridPP</i><br/>
        Simon Fayer <i>Imperial college (UK), GridPP</i><br/>
        Janusz Martyniak <i>Imperial college (UK), GridPP</i><br/>
        Xiaomei Zhang <i>Beijing, Inst. High Energy Phys. (CN), Juno</i><br/>
        Luisa Arrabito <i>LUPM (FR), CTA</i><br/>
        André Sailer <i>CERN</i><br/>
        Jorge Lisa Laborda <i>Univ. of Valencia and CSIC (ES), LHCb</i><br/>
        Bertrand Rigaud <i>IN2P3 (FR)</i>
    </div>
    <div class="grid-item text-right mr-4 col-span-1">
        <strong>Project lead</strong>
    </div>
    <div class="grid-item col-span-2">
        Federico Stagni <i>CERN, LHCb</i><br/>
        Andrei Tsaregorodtsev <i>CPPM (FR), EGI and LHCb</i>
    </div>
</div>

&nbsp;
&nbsp;
&nbsp;
&nbsp;
&nbsp;

<div class="grid-item col-span-3 text-center mt-180px mb-auto font-size-1.5rem">
    <strong>Thank you!</strong>
</div>
