# READY.

# Trail 001 — The Commodore 64 Machine

## Stage 002 — Inside the C64

---

# Document Information

| Property | Value |
|---|---|
| Document | Stage 002 — Inside the C64 |
| Language | English |
| Type | Knowledge Trail Stage |
| Trail | Trail 001 — The Commodore 64 Machine |
| Stage | 002 |
| Status | Draft |
| Version | 0.1.0 |
| Difficulty | ⭐⭐☆☆☆ |
| Estimated Study Time | 45–60 minutes |
| Prerequisites | Stage 001 — Meet the Machine |

---

# 🥾 Destination

In Stage 001 we built our first mental map of the Commodore 64.

Now we are going to open the map.

We will look at the machine as a physical object and begin connecting what we learned conceptually with the real hardware.

By the end of this Stage you should be able to:

- distinguish the computer case from the motherboard;
- understand what a motherboard is;
- recognize the major functional areas of a C64 motherboard;
- understand that different C64 board revisions exist;
- recognize the 6510 CPU, VIC-II, SID, CIA and memory as physical components;
- understand why chip identification must always consider the board revision;
- begin reading a motherboard photograph as a technical map.

**You do not need to know Assembly language for this Stage.**

---

# 🪧 Trail Sign — Open the Machine

> The C64 is not the beige case.
>
> The case is only the shelter.
>
> The machine is inside.

Until now we have looked at the C64 from the outside.

Now we are going inside.

---

# Why Should I Care?

If you have ever looked at a C64 motherboard, you may have had the same first reaction:

> "There are a lot of chips in there."

That is perfectly normal.

A motherboard photograph can initially look like a landscape of anonymous black rectangles, capacitors, resistors and copper traces.

Our job is not to memorize the position of every component.

Our job is to learn how to **read the landscape**.

Once you can look at a motherboard and ask:

> "What role does this component play?"

the photograph stops being mysterious.

It becomes a map.

---

# 🟢 Layer 1 — Intuition

## What Is a Motherboard?

A motherboard is the physical circuit board that connects the major electronic components of a computer.

Think of it as the **terrain on which the machine's specialists live and communicate**.

The board contains:

- integrated circuits;
- memory chips;
- connectors;
- resistors;
- capacitors;
- oscillators and clock circuitry;
- power circuitry;
- copper traces;
- and many other supporting components.

The CPU does not simply sit on the board and work alone.

It needs electrical connections to memory and other devices.

The VIC-II needs access to information and timing signals.

The SID needs power, clocking and communication with the CPU.

The CIA chips connect the computer to the outside world.

The motherboard is the physical infrastructure that makes these relationships possible.

---

# The C64 Is Not One Single Hardware Design

This is our first important warning.

There is not one single C64 motherboard.

During the commercial life of the C64, Commodore produced multiple motherboard revisions.

Components moved.

Chip versions changed.

Power circuitry changed.

Memory technology changed.

The layout changed.

Some later designs integrated functions differently.

Therefore:

> **A memory address, chip number or physical position must never be interpreted without considering the hardware revision when revision-specific accuracy matters.**

This principle will become extremely important later when we study hardware behavior.

---

# 📷 The C64 From the Outside

Before opening the machine, remember what the user actually saw.

![Commodore 64 breadbin](../../../Asset/Hardware/Trail001_TheCommodore64Machine/Stage002_InsideTheC64/models/c64_breadbin.jpg)

*Figure 1 — The original "breadbin" form of the Commodore 64. Final source and licensing information must be recorded in the asset metadata before public publication.*

The famous original case is commonly nicknamed the **breadbin** because of its shape.

It became one of the most recognizable computer designs of the 1980s.

But the beige case tells us almost nothing about how the computer actually works.

For that, we need to open it.

---

# 📷 The Later C64C

![Commodore 64C](../../../Asset/Hardware/Trail001_TheCommodore64Machine/Stage002_InsideTheC64/models/c64c.jpg)

*Figure 2 — Later Commodore 64C case design. Final source and licensing information must be recorded in the asset metadata before public publication.*

The C64C is especially useful for one reason:

It reminds us that **the same product name does not necessarily mean identical internal hardware**.

As we progress through the Bible, we will learn to distinguish:

- model;
- board revision;
- chip revision;
- PAL versus NTSC systems;
- and other hardware variations.

This is essential for serious reverse engineering.

---

# 🔵 Layer 2 — Practical View

## Open the Case

Now imagine removing the keyboard/case assembly.

What appears underneath is something very different from the friendly BASIC environment we saw in Stage 001.

There is no:

```text
READY.
```

There is no BASIC prompt.

There is a circuit board.

And on that board are the components that make the prompt possible.

![C64 motherboard](../../../Asset/Hardware/Trail001_TheCommodore64Machine/Stage002_InsideTheC64/motherboard/c64_motherboard.jpg)

*Figure 3 — C64 motherboard. The exact board revision should be identified before component-level conclusions are published.*

---

# First Exercise — Do Not Read the Labels Yet

Look at the motherboard photograph for a moment.

Do not try to identify the chips.

Instead ask:

- Where are the large integrated circuits?
- Where are the memory chips?
- Where are the connectors?
- Where does power enter?
- Where does video/audio leave the machine?
- Where are there groups of similar chips?
- Where do you see large copper areas or clusters of traces?

You are learning to see the motherboard as a **system**, not as a collection of parts.

---

# 🪧 Trail Sign — Components Have Jobs

A useful rule for the rest of the project is:

> **Never learn a component only by its name. Learn its role.**

For example:

**6510**

is not merely a part number.

It is the CPU that executes the program.

**VIC-II**

is not merely a chip name.

It is the principal video controller.

**SID**

is not merely a famous Commodore chip.

It is a programmable sound synthesizer.

This distinction between **name** and **role** will make later reverse engineering much easier.

---

# 🟠 Layer 3 — Technical View

## The Major Functional Groups

At a high level we can divide the motherboard into several functional regions:

```text
                   ┌──────────────────────┐
                   │      CPU / 6510       │
                   └──────────┬───────────┘
                              │
                    ┌─────────┴─────────┐
                    │  SYSTEM INTERFACE │
                    └─────────┬─────────┘
                              │
        ┌─────────────┬───────┼────────┬─────────────┐
        ▼             ▼       ▼        ▼             ▼
      VIC-II         SID     CIA 1    CIA 2       MEMORY
      VIDEO          AUDIO     I/O      I/O       RAM / ROM
```

This is still a conceptual diagram.

It is deliberately simpler than the real electrical architecture.

That is intentional.

We are building understanding progressively.

---

# The 6510

The 6510 is the CPU at the heart of the C64.

Its job is to execute machine instructions.

Later we will study:

- registers;
- instruction set;
- addressing modes;
- stack;
- interrupts;
- timing;
- undocumented behavior;
- and the additional I/O capability of the 6510.

For now, remember only this:

> **The CPU executes instructions, but it does not perform every job in the computer.**

That distinction is fundamental.

---

# The VIC-II

The VIC-II is the C64's video controller.

It is responsible for a large part of what eventually becomes the picture on the screen.

Later we will explore:

- character display;
- bitmap modes;
- sprites;
- raster timing;
- scrolling;
- color memory;
- bad lines;
- FLI;
- FLD;
- VSP;
- and other advanced techniques.

For now:

> **The VIC-II is a hardware specialist for video.**

---

# The SID

The SID is the computer's sound chip.

It contains dedicated circuitry for sound generation and filtering.

Later we will explore:

- oscillators;
- waveforms;
- ADSR envelopes;
- filters;
- modulation;
- music players;
- sound effects;
- and techniques that exploit the SID in unexpected ways.

For now:

> **The SID is a hardware specialist for sound.**

---

# The CIA Chips

The C64 contains two CIA chips.

CIA stands for **Complex Interface Adapter**.

They provide important interfaces between the computer and the outside world.

Among their responsibilities are:

- keyboard scanning;
- joystick input;
- timers;
- parallel I/O;
- serial-related functions;
- interrupt-related functions.

Later we will separate exactly what CIA 1 and CIA 2 do.

For now:

> **The CIA chips are important bridges between the C64 and its peripherals.**

---

# Memory

Now we reach one of the most important subjects in the entire Bible.

Memory is not simply "where the program lives."

The C64 contains different kinds of memory and memory-mapped devices.

We will eventually encounter:

- RAM;
- BASIC ROM;
- KERNAL ROM;
- Character ROM;
- I/O registers;
- color RAM;
- and the mechanisms used to determine which resources are visible to the CPU.

The physical motherboard will help us understand that these are not abstract concepts.

They are real electronic resources connected to the system.

---

# 🔴 Layer 4 — Engineering View

## Why So Many Specialists?

A modern computer hides enormous amounts of hardware behind layers of abstraction.

A programmer may never need to know which physical circuit generates a pixel.

The C64 is different.

Its architecture exposes much more of the machine.

That creates both limitations and opportunities.

A programmer who understands the hardware can coordinate software with it.

This is why C64 programming eventually became an exercise in **hardware orchestration**.

The programmer can influence:

- what the CPU executes;
- when it executes;
- what the VIC-II sees;
- how memory is mapped;
- when an interrupt occurs;
- how the SID is programmed;
- and how different components interact.

That is the beginning of the path toward the techniques we will eventually reverse engineer.

---

# 🧭 Revision Matters

Suppose we find a photograph of a C64 motherboard.

Can we immediately say:

> "This is where the VIC-II is."

Not yet.

First we should ask:

1. Which motherboard revision is this?
2. Is it PAL or NTSC?
3. Which VIC-II revision is installed?
4. Which CPU revision is installed?
5. Which memory technology is used?
6. Are there board-specific differences?

This discipline prevents a very common research mistake:

> **turning one hardware example into a universal rule.**

The Bible will always try to distinguish between:

**general architectural facts**

and

**revision-specific observations**.

---

# 🔬 Laboratory Exercise

If you have a real C64:

1. Disconnect power.
2. Never open a powered machine.
3. Identify the motherboard revision.
4. Photograph the board.
5. Record every visible major chip.
6. Record the markings printed on the chips.
7. Record PAL/NTSC information if known.
8. Do not remove chips just to identify them.

If you are using an emulator, use the emulator's documentation to determine which C64 configuration it is reproducing.

Create a small research note:

```text
Machine:
Model:
Board revision:
Video standard:
CPU:
VIC-II:
SID:
CIA 1:
CIA 2:
RAM type:
Notes:
```

This note will become useful later.

---

# 🌄 Vista Point

Look at the motherboard again.

You should now be able to see it differently.

Before:

> "A board full of chips."

Now:

> "A collection of specialized systems connected together."

And eventually:

> "A coordinated electronic machine whose timing and interactions can be programmed."

That is the change we are looking for.

---

# 🎒 Put This in the Backpack

After Stage 002, keep these concepts:

- motherboard;
- hardware revision;
- 6510 CPU;
- VIC-II;
- SID;
- CIA 1;
- CIA 2;
- RAM;
- ROM;
- I/O;
- physical components versus logical architecture;
- revision-specific research.

You do not need to memorize component locations yet.

You need to understand **why they are there**.

---

# 🏕️ Next Stage

The next logical stop is:

## Stage 003 — Meet the 6510

There we will finally stop treating the CPU as a black box.

We will open it.

We will learn what an 8-bit CPU actually means.

We will meet:

- A;
- X;
- Y;
- Program Counter;
- Stack Pointer;
- Processor Status;
- memory addressing;
- instructions;
- and the first real machine-language operations.

The trail will become steeper.

But we now have a map.

---

# 🏆 Stage Checkpoint

You have reached the second small summit.

The first summit was:

> **"I know what the C64 is."**

This one is:

> **"I can look inside the C64 and recognize its major specialists."**

From here onward, the machine will become increasingly transparent.

The black boxes will start to open.

**READY.**
