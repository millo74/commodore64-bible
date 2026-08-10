# READY.

# Trail 001 -- The Commodore 64 Machine

## Stage 001 -- Meet the Machine

---

# Document Information

| Property             | Value                                |
| -------------------- | ------------------------------------ |
| Document             | Stage 001 -- Meet the Machine         |
| Language             | English                              |
| Type                 | Knowledge Trail Stage                |
| Trail                | Trail 001 -- The Commodore 64 Machine |
| Stage                | 001                                  |
| Status               | Draft                                |
| Version              | 0.1.0                                |
| Last Update          | 2026-08-08                           |
| Difficulty           | ?????                                |
| Estimated Study Time | 30-45 minutes                        |
| Prerequisites        | None                                 |

---

# ? Destination

At the end of this Stage, you will be able to:

* recognize the major components of a Commodore 64;
* understand the basic role of the CPU, memory, video, audio and I/O systems;
* understand why the Commodore 64 is more than "a computer with a CPU";
* identify the main chips inside the machine;
* understand the basic relationship between CPU, memory and hardware devices;
* build a mental map that will support all future Knowledge Trails.

You do **not** need to know Assembly language to complete this Stage.

You do not even need previous computer knowledge.

We start from the beginning.

---

# ? Trail Sign -- Before We Begin

> **There is no single way to learn the Commodore 64.**
>
> There are many trails leading to the same summit.
>
> This is the first step.

---

# Why Should I Care?

You could start learning 6502/6510 Assembly immediately.

You could memorize registers.

You could learn hexadecimal addresses.

You could write your first `LDA` and `STA` instructions.

But there is a problem.

If you do not know what the machine is actually doing, Assembly quickly becomes a collection of mysterious numbers.

The goal of this Trail is different.

Before learning how to control the Commodore 64, we will first learn **who we are controlling**.

---

# The Story Begins

## 1983

Imagine opening a brand-new box.

Inside is a beige computer keyboard.

There is no mouse.

No hard disk.

No graphical desktop.

No Internet connection.

No modern operating system waiting to be installed.

You connect the machine to a television.

You switch it on.

The screen comes alive.

And then you see:

```text
 **** COMMODORE 64 BASIC V2 ****

 64K RAM SYSTEM 38911 BASIC BYTES FREE

READY.
```

That word looks almost insignificant.

**READY.**

But it is an invitation.

The machine is telling you:

> I am waiting for you.

You can type something.

You can experiment.

You can make mistakes.

You can write a program.

You can create a game.

You can make music.

You can make pictures.

And eventually, if you learn how the hardware really works, you can make the machine do things its designers never expected ordinary users to achieve.

Welcome to the machine.

---

# ? Layer 1 -- Intuition

## Think of the C64 as a Small Team

A useful way to understand the Commodore 64 is to imagine that it is not one machine, but a team of specialists.

Each specialist has a different job.

### ? The CPU

The CPU is the machine's main worker.

It executes instructions.

It performs calculations.

It reads and writes data.

It decides what the program should do next.

The Commodore 64 uses a variant of the MOS Technology 6502 called the **6510**.

---

### ? The VIC-II

The VIC-II is responsible for the computer's video system.

It helps produce:

* characters;
* graphics;
* colors;
* sprites;
* scrolling;
* raster effects.

Later, we will discover that programmers learned to exploit the VIC-II far beyond what a simple description such as "video chip" suggests.

---

### ? The SID

The SID is the machine's sound synthesizer.

It generates electronic sound and music.

It provides hardware features for:

* multiple voices;
* waveform generation;
* envelopes;
* filtering;
* modulation.

The SID is one of the reasons the Commodore 64 became famous for its distinctive sound.

---

### ? The CIA Chips

The Commodore 64 contains two CIA chips.

CIA stands for **Complex Interface Adapter**.

They provide several important functions, including:

* input/output;
* timers;
* keyboard scanning;
* joystick handling;
* communication with external devices;
* interrupt-related functions.

We will study them much more deeply later.

---

### ? Memory

The machine also needs somewhere to store things.

Programs.

Variables.

Characters.

Graphics.

Music data.

Tables.

Buffers.

Temporary results.

That is the job of memory.

The Commodore 64 was advertised as having **64 KB of RAM**.

But already here we encounter one of the most interesting characteristics of the machine:

> Having 64 KB of RAM does not mean that the CPU can simply see all of it in the same way at the same time.

That mystery will become one of our future Trails.

---

# ? Layer 2 -- Practical View

Let's imagine what happens when you perform some simple actions.

## You type a character

You press a key.

The keyboard hardware detects it.

The C64's I/O system processes the input.

Software determines what that key means.

The character may eventually appear on the screen.

Several hardware and software components have participated in what looks like a single action.

---

## You display something on the screen

A program changes information in memory.

The VIC-II reads the appropriate information.

The video hardware generates the corresponding display.

The television or monitor receives the video signal.

You see the result.

From the user's perspective:

> "I printed a character."

From the machine's perspective:

> Several subsystems cooperated to produce that character.

---

## You play a sound

A program writes values to SID registers.

The SID interprets those values.

Its internal circuitry generates the requested waveform and processes it through its sound-generation facilities.

The resulting electrical signal eventually reaches the audio output.

From the user's perspective:

> "The computer played a sound."

From the machine's perspective:

> The CPU communicated with a dedicated sound-generation device.

---

# ? Layer 3 -- Technical View

Now we can begin introducing the real architecture.

A simplified view looks like this:

```text
                       +-----------------+
                       |    6510 CPU     |
                       +--------+--------+
                                |
                                |
                         SYSTEM INTERFACE
                                |
              +-----------------+-----------------+
              |                 |                 |
              ?                 ?                 ?
          +--------+       +--------+       +--------+
          | VIC-II |       |  SID   |       | CIA 1  |
          +--------+       +--------+       +--------+
                                |
                                |
                             +-------+
                             | CIA 2 |
                             +-------+

                 +--------------------------+
                 |          MEMORY          |
                 |                          |
                 | RAM / ROM / I/O mapping  |
                 +--------------------------+
```

This is intentionally simplified.

It is a **mental model**, not yet an electrical schematic.

That distinction is important.

As we progress through the Trail, we will replace simplified models with increasingly accurate ones.

---

# The Main Components

A Commodore 64 system contains several major subsystems.

| Component     | Primary Role                      |
| ------------- | --------------------------------- |
| 6510          | CPU                               |
| VIC-II        | Video and graphics                |
| SID           | Sound synthesis                   |
| CIA 1         | I/O, timers and related functions |
| CIA 2         | I/O, timers and related functions |
| RAM           | Working memory                    |
| BASIC ROM     | BASIC interpreter                 |
| KERNAL ROM    | System routines                   |
| Character ROM | Character graphics                |
| I/O circuitry | Communication with peripherals    |

Each of these will eventually become its own area of study.

---

# ? Trail Sign -- One Machine, Many Specialists

Do not think of the Commodore 64 as:

> **CPU + memory + screen**

Think of it as a collection of specialized systems cooperating with one another.

This way of thinking will become extremely important later.

When we study:

* sprites;
* raster interrupts;
* scrolling;
* music;
* disk loading;
* joystick input;
* fast loaders;
* demos;

we will constantly ask:

> **Which subsystem is doing the work?**

And then:

> **How are the other subsystems being coordinated?**

That is where the real architecture begins to emerge.

---

# ? Layer 4 -- Engineering View

Here the Commodore 64 starts becoming truly interesting.

The hardware was not designed simply to provide maximum flexibility.

It was designed under severe cost and technological constraints.

The designers had to produce an affordable home computer while providing capabilities that would make it attractive to consumers.

The result was a system in which specialized chips performed tasks that might otherwise have required much more work from the CPU.

This created an important opportunity.

Programmers could control hardware directly.

And eventually they learned to exploit timing, memory layout, interrupts and hardware behaviour to achieve results that were not obvious from the official programming model.

---

# The Hidden Power of Specialization

Imagine asking the CPU to draw every pixel on the screen.

That would be expensive.

Instead, the VIC-II performs much of the video generation independently.

Imagine asking the CPU to generate every individual sound waveform.

Again, expensive.

The SID contains dedicated sound-generation circuitry.

This division of labour is one of the fundamental ideas behind the C64.

But it also creates something else:

**timing.**

The CPU and the hardware chips must cooperate.

Sometimes they compete for access to memory.

Sometimes one chip changes what another chip can see.

Sometimes the exact moment at which an operation occurs matters.

And this is where the programmers of the 1980s and 1990s became extraordinarily creative.

---

# ? Engineering Insight

Many of the famous C64 techniques that we will study later are not simply "software tricks".

They are often the result of understanding the interaction between:

* CPU timing;
* VIC-II timing;
* memory configuration;
* interrupts;
* bus access;
* hardware registers;
* video raster position.

The programmer is not merely writing instructions.

The programmer is **orchestrating hardware**.

That idea will become fundamental to this entire project.

---

# ? Laboratory -- Meet Your C64

If you have a real Commodore 64, use it.

If you do not, use an emulator such as VICE.

For this first experiment, do not worry about Assembly.

Start the machine.

Wait for:

```text
READY.
```

Now type:

```basic
PRINT 2+2
```

You should obtain:

```text
 4
```

Now try:

```basic
10 PRINT "HELLO"
20 GOTO 10
```

Run it:

```basic
RUN
```

Watch the screen.

Then stop the program with ESC key.

---

# ? Laboratory Question

You have just written only two BASIC lines.

But how many different parts of the computer participated?

Think about:

* the keyboard;
* the CPU;
* memory;
* the BASIC interpreter;
* the VIC-II;
* the display.

You do not need to know the answer yet.

The purpose of this experiment is to create the question.

Later Trails will provide the answers.

---

# ? Historical Stop

For many programmers, this simple BASIC prompt was their first programming environment.

But the BASIC environment represented only one layer of the machine.

Underneath BASIC was a much more powerful hardware system.

As programmers became more experienced, many began moving beyond the limitations of the built-in BASIC environment.

They discovered that they could communicate directly with hardware.

They learned to use machine language.

They learned to manipulate memory.

They learned to synchronize code with the video raster.

They learned to exploit hardware timing.

And eventually they produced effects that seemed impossible for an 8-bit computer.

This transition--from **using the computer** to **understanding and controlling the machine itself**--is one of the central themes of the Commodore 64 Bible.

---

# ? Vista Point

Stop here for a moment.

Look back at the machine we have just met.

We began with a keyboard and a television.

Now we can see something very different.

Inside that apparently simple home computer are several specialized systems:

```text
                    COMMODORE 64
                          |
        +-----------------+-----------------+
        |                 |                 |
       CPU              VIDEO             AUDIO
      6510              VIC-II             SID
        |                 |                 |
        +-----------------+-----------------+
                          |
                        I/O
                     CIA 1 / CIA 2
                          |
                       MEMORY
                          |
                  RAM / ROM / I/O
```

This is our first mental map.

We will refine it repeatedly.

Every future Trail will add detail.

---

# ? What We Have Not Learned Yet

We have deliberately left many questions unanswered.

For example:

* How can a CPU address only 64 KB?
* How does memory banking work?
* Where exactly is RAM?
* Where are the hardware registers?
* How does the VIC-II access memory?
* What exactly is a raster?
* How are sprites generated?
* How does the SID communicate with the CPU?
* What happens when an interrupt occurs?
* Why does the CPU sometimes appear to "lose" cycles?
* How can programmers synchronize code with the video beam?

These are not problems.

They are **signposts**.

Each question points toward another part of the mountain.

---

# ? What Goes Into the Backpack?

After this Stage, you should carry these concepts with you:

* CPU
* memory
* video hardware
* audio hardware
* I/O hardware
* specialized chips
* hardware/software cooperation
* timing
* interrupts
* memory mapping

You do not need to memorize all of them yet.

You only need to recognize them.

---

# ? Recommended Next Stages

The next recommended path is:

### Stage 002 -- Inside the C64

Explore the physical machine and its major chips.

### Stage 003 -- The 6510 CPU

Meet the processor that executes the programs.

### Stage 004 -- Memory

Understand RAM, ROM, I/O and the C64 memory architecture.

### Stage 005 -- The VIC-II

Discover the video chip that made the C64 famous.

### Stage 006 -- The SID

Enter the world of sound synthesis.

### Stage 007 -- The CIA Chips

Explore I/O, timers, keyboard, joystick and related hardware.

These stages will eventually branch into more specialized Trails.

---

# ? Summit Checkpoint

You are **not expected to be an expert** after this Stage.

You have reached a much smaller summit:

> **You now have a map of the machine.**

From this point forward, whenever you encounter the words:

**6510**

**VIC-II**

**SID**

**CIA**

**RAM**

**ROM**

you should no longer see mysterious names.

You should see the members of a team.

And that team is the Commodore 64.

---

# Final Thought

The Commodore 64 does not look particularly impressive when viewed only from the outside.

A keyboard.

A television.

A few chips.

64 KB of RAM.

Yet inside that machine was enough engineering ingenuity to keep programmers discovering new possibilities for decades.

Every time somebody declared:

> **"The C64 has reached its limit."**

someone else eventually found another way to move that limit.

That is why we are here.

Not simply to learn what the Commodore 64 could do.

But to understand **how programmers made it do things nobody thought it could do.**

The machine is waiting.

The next trail begins with a question:

> **What is really inside this box?**

**READY.**
