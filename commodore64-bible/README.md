# READY.

# Commodore 64 Bible

## The Complete Reverse Engineering Project

**Learn how it worked.
Understand why it worked.
Build what comes next.**

---

## What is the Commodore 64 Bible?

The **Commodore 64 Bible** is an open, research-driven project dedicated to understanding, documenting, preserving and teaching the architecture, programming techniques and engineering practices of the Commodore 64.

This is not simply another programming tutorial, code archive or emulator guide.

It is an attempt to build a complete technical reference that explains **how the Commodore 64 really worked**, from the 6510 CPU to the VIC-II, SID, CIA chips, memory banking, raster interrupts, sprite multiplexing, loaders, compression techniques and the advanced programming methods used in commercial games and demos of the 1980s and 1990s.

Beyond documenting existing knowledge, this project also aims to rediscover, analyze and explain undocumented techniques, forgotten programming tricks, unconventional design solutions and hardware behaviors that allowed programmers to push the Commodore 64 far beyond its original limits.

But this project goes one step further.

It seeks to reconstruct the knowledge that was never formally documented:

forgotten programming techniques;
reverse engineered algorithms;
undocumented hardware behaviors;
optimization tricks;
design patterns hidden inside commercial software;
and the engineering ideas that allowed programmers to achieve results once considered impossible on an 8-bit computer.

Our goal is to preserve not only the code, but the **thinking process of the programmers who created it**.

---

## Why this project exists

The Commodore 64 remains the best-selling personal computer in history and one of the most influential machines ever created.

It introduced millions of people to programming, electronics, music synthesis and game development.

Over the decades, an enormous amount of knowledge has been scattered across:

* books;
* magazines;
* technical articles;
* demo scene productions;
* commercial games;
* source code releases;
* personal notes of programmers;
* hardware documentation;
* community forums and archives.

The Commodore 64 Bible exists to gather, verify and organize this knowledge into a coherent, structured and continuously evolving reference for future generations.

---

## Our Philosophy

The Commodore 64 Bible is a **living project**.

It does not seek to preserve nostalgia.

It seeks to preserve knowledge.

We believe that:

* understanding is more valuable than memorization;
* experiments are more valuable than assumptions;
* documentation is as important as code;
* history deserves technical accuracy;
* knowledge grows when it is shared.

Read the full philosophy here:

? **docs/en/ProjectPhilosophy.md**

---

## Repository Structure

```
commodore64-bible/

    bible/          Official verified documentation

    docs/           Project documentation and standards

    journal/        Research notes and development diary

    lab/            Experiments and hardware investigations

    src/            Assembly source code and libraries

    reverse/        Reverse engineering projects

    examples/       Minimal working examples

    games/          Educational game projects

    references/     Books, magazines and historical sources

    assets/         Logos, diagrams and images

    tools/          Build and utility scripts
```

---

## Two Worlds: Laboratory and Bible

### Laboratory

The place where ideas are explored.

* experiments;
* prototypes;
* measurements;
* failed attempts;
* discoveries;
* ongoing investigations.

Nothing here is considered final.

### Bible

The official knowledge base.

Only information that has been verified, documented and reviewed enters the Bible.

This separation allows the project to remain both **scientifically rigorous** and **creatively experimental**.

---

## Research Notes (Pillole del Giorno)

The project advances through small, self-contained research units called **Research Notes (RN)**, affectionately known as **Pillole del Giorno**.

Each Research Note focuses on **one concept only** and follows a consistent structure:

1. Theory
2. Historical Context
3. Hardware Analysis
4. Assembly Implementation
5. Practical Experiment
6. Reverse Engineering Notes
7. References

The objective is to make every topic understandable in a single focused study session.

---

## Historical Accuracy

Whenever possible we ask:

**"How did Commodore 64 programmers actually solve this problem in 1987?"**

For each technique we distinguish between:

* **Historical Implementation**;
* **Modern Interpretation**;
* **Why that original solution was chosen**.

The goal is not merely to reproduce old code, but to understand the engineering constraints and design decisions of the time.

---

## Assembly Standards

The historical reference environment is:

**Turbo Macro Pro compatible syntax (TMPx)**

Modern compatibility targets include:

* Kick Assembler;
* 64tass;
* other modern 6502/6510 assemblers.

Source code remains in English and is written with meaningful labels and extensive documentation.

---

## International Project

English is the canonical language of the project.

Translations are organized by language directories:

```
docs/

    en/

    it/

    ...
```

Technical terminology and source code remain consistent across all translations.

See:

? **docs/en/TranslationPolicy.md**

---

## Scientific Method

The Commodore 64 Bible follows a research-oriented methodology:

**Observe -> Experiment -> Measure -> Verify -> Document -> Repeat**

Whenever uncertainty exists, it is explicitly stated.

Whenever possible, claims are supported by original documentation, experiments or historical sources.

---

## Current Milestone

### M0 -- Project Foundation ?

* repository structure;
* multilingual architecture;
* project philosophy;
* translation policy;
* documentation templates;
* editorial standards.

### M1 -- Project Identity (in progress)

* official README;
* project roadmap;
* contribution guide;
* first Research Note.

---

## How to Contribute

Contributions are welcome in many forms:

* technical documentation;
* assembly code;
* reverse engineering analysis;
* historical research;
* magazine indexing;
* hardware experiments;
* translations;
* proofreading and review.

Please read the contribution guidelines before submitting changes.

---

## Project Motto

Every session begins with one word:

```
READY.
```

For us, READY no longer means that BASIC is waiting.

It means that curiosity is ready.

Research is ready.

Learning is ready.

The laboratory is open.

---

## Final Statement

The Commodore 64 Bible is not a monument to the past.

It is a bridge between generations.

It preserves the knowledge of yesterday,
explains it today,
and inspires the programmers of tomorrow.

**READY.**
