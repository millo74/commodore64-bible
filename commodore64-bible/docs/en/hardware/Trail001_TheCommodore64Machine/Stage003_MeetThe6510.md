# READY.

# Trail 001 -- The Commodore 64 Machine

## Stage 003 -- Meet the 6510

---

# Document Information

| Property             | Value                                                    |
| -------------------- | -------------------------------------------------------- |
| Document             | Stage 003 -- Meet the 6510                                |
| Language             | English                                                  |
| Type                 | Knowledge Trail Stage                                    |
| Trail                | Trail 001 -- The Commodore 64 Machine                     |
| Stage                | 003                                                      |
| Status               | Draft                                                    |
| Version              | 0.1.0                                                    |
| Difficulty           | ?????                                                    |
| Estimated Study Time | 60-90 minutes                                            |
| Prerequisites        | Stage 001 -- Meet the Machine; Stage 002 -- Inside the C64 |

---

# ? Trail Destination

We have seen the Commodore 64 from the outside.

We have opened the machine.

We have met its major hardware specialists.

Now we are going to meet the component that actually **executes the instructions that make the computer do things**.

The CPU.

More precisely:

**the MOS 6510.**

By the end of this Stage, you should understand:

* what a CPU actually does;
* why the CPU is different from RAM, ROM and I/O devices;
* what an instruction is;
* what registers are;
* what the Program Counter does;
* what the Stack Pointer does;
* what the Processor Status Register represents;
* why the 6510 is related to the 6502 family;
* what makes the 6510 special inside the C64;
* why understanding the CPU is essential for understanding Assembly language.

You do **not** need to know Assembly before starting this Stage.

In fact, this Stage is deliberately designed to prepare you for it.

---

# ? Trail Sign -- Something Has to Execute the Program

When you typed:

```text
PRINT "HELLO"
```

into the Commodore 64, something had to interpret that command.

When a game moved a sprite across the screen, something had to calculate its position.

When a music player changed a SID register, something had to execute the instructions responsible for doing it.

When an interrupt occurred, something had to react.

That something was the CPU.

But what exactly does a CPU do?

---

# Why Should I Care?

The word **CPU** is everywhere.

We hear about:

* CPUs in desktop computers;
* CPUs in smartphones;
* multi-core CPUs;
* GHz;
* ARM;
* x86;
* RISC;
* superscalar processors.

It is easy to think of a CPU as a mysterious black box.

For our purposes, it is much more useful to remove that mystery.

A CPU is essentially a machine capable of repeatedly:

1. obtaining an instruction;
2. understanding what that instruction means;
3. obtaining the data required by the instruction;
4. performing an operation;
5. storing the result;
6. moving to the next instruction.

That simple cycle is the foundation of everything we are going to study.

---

# ? Layer 1 -- Intuition

## Imagine a Very Small Worker

Imagine a worker sitting at a desk.

On the desk there is:

* a notebook containing instructions;
* some storage drawers;
* a small number of temporary working spaces;
* and a set of rules describing what operations the worker understands.

The worker repeatedly asks:

> "What should I do next?"

He reads an instruction.

He performs it.

He records the result.

Then he asks again:

> "What should I do next?"

The 6510 is our worker.

The memory is the notebook and storage.

The registers are the small working spaces.

The instruction set is the collection of operations the worker understands.

The clock provides the rhythm that coordinates the process.

This is obviously a simplification.

But it gives us the correct mental model.

---

# The CPU Does Not Contain the Whole Computer

This is one of the most important concepts of this Stage.

The CPU is not:

* the RAM;
* the video chip;
* the sound chip;
* the keyboard;
* the disk drive;
* the display.

It is the component that **executes instructions and coordinates operations**.

The Commodore 64 becomes useful because the CPU communicates with many other components.

Conceptually:

```text
                   +-------------+
                   |    CPU      |
                   |    6510     |
                   +------+------+
                          |
             +------------+------------+
             |            |            |
             ?            ?            ?
           Memory       VIC-II        CIA
             |            |            |
             ?            ?            ?
            Data         Video       I/O
```

The real architecture is considerably more complex.

This diagram is intentionally simple.

We are building the mountain one step at a time.

---

# What Is an Instruction?

An instruction is an operation that the CPU understands.

For example, conceptually:

```text
LOAD A VALUE
```

or:

```text
ADD A VALUE
```

or:

```text
STORE A
```

The actual 6510 instruction set does not use English sentences like these.

It uses machine-code instructions represented by binary values.

Assembly language gives programmers a readable textual representation of those instructions.

For example:

```asm
LDA #$10
```

means:

> Load the hexadecimal value `$10` into the accumulator.

We are not going to study this instruction yet.

For now, simply remember:

> **Assembly language is a human-readable way of expressing CPU instructions.**

This is the first bridge between the hardware we are studying and the Assembly programming we will soon begin.

---

# ? Layer 1 -- The CPU's Basic Job

At the most fundamental level:

```text
             +--------------+
             |    FETCH     |
             +------+-------+
                    ?
             +--------------+
             |    DECODE    |
             +------+-------+
                    ?
             +--------------+
             |    EXECUTE   |
             +------+-------+
                    |
                    +--------------? NEXT INSTRUCTION
```

This is the famous **fetch-decode-execute cycle**.

It is one of the fundamental ideas of computer architecture.

The 6510 performs this process continuously while it is running.

---

# ? Layer 2 -- Practical View

## Meet the Registers

A CPU needs a small amount of extremely fast internal storage.

The 6510 provides several registers.

They are not RAM.

They are small storage locations directly inside the processor.

The most important ones for our first encounter are:

| Register | Purpose          |
| -------- | ---------------- |
| A        | Accumulator      |
| X        | X Index Register |
| Y        | Y Index Register |
| PC       | Program Counter  |
| SP       | Stack Pointer    |
| P        | Processor Status |

These registers will become familiar companions during our journey.

---

# The Accumulator -- A

The **Accumulator**, usually called **A**, is one of the most important registers in the 6510.

It is used by many arithmetic, logical and data manipulation instructions.

For example:

```asm
LDA #$05
```

means:

> Load the value `$05` into A.

Conceptually:

```text
Before:

A = ????????

        LDA #$05

After:

A = 00000101
```

The accumulator is therefore one of the CPU's main working registers.

---

# The X Register

The **X register** is an index register.

It is particularly useful when working with:

* arrays;
* tables;
* loops;
* indexed memory access.

For example:

```asm
LDX #$00
```

loads zero into X.

Later we will discover that X can be incremented and decremented and used to navigate through memory.

For now:

> **Think of X as a small numerical tool the CPU can use to keep track of positions.**

---

# The Y Register

The **Y register** is another index register.

It has many similarities to X, although the instruction set does not treat X and Y as completely interchangeable.

Y is also extremely useful for:

* loops;
* tables;
* indexed addressing;
* navigating through memory.

Later, when we study addressing modes, the difference between X and Y will become much clearer.

---

# The Program Counter -- PC

Now we meet one of the most important registers in the entire CPU.

The **Program Counter**, usually called **PC**, tells the CPU where the next instruction is located.

Imagine memory containing:

```text
$0800   LDA #$01
$0802   STA $D020
$0805   RTS
```

The Program Counter might contain:

```text
PC = $0800
```

The CPU fetches the instruction located there.

After executing it, the PC advances to the next instruction, unless something changes the normal flow.

Branches, jumps, subroutines and interrupts can change the Program Counter.

This means that:

> **The Program Counter is effectively the CPU's position on the program's path.**

And this gives us another perfect hiking metaphor.

The program is the trail.

The Program Counter tells the CPU:

> **"You are here."**

---

# The Stack Pointer -- SP

The 6510 also has a **Stack Pointer**.

The stack is a special area of memory used by the CPU for temporary information.

It is particularly important for:

* subroutine calls;
* returning from subroutines;
* interrupts;
* temporary storage;
* saving CPU state.

We will dedicate much more time to the stack later.

For now, remember:

> **SP tells the CPU where the current top of the stack is located.**

---

# The Processor Status Register -- P

The Processor Status Register contains several individual status flags.

These flags tell the CPU about the result or state of previous operations.

Among them are flags related to:

* Carry;
* Zero;
* Interrupt Disable;
* Decimal Mode;
* Break;
* Overflow;
* Negative.

For example, after an operation produces a zero result, the Zero flag can be affected.

This becomes extremely important for conditional branches.

Conceptually:

```text
        RESULT
           |
           ?
    +-------------+
    | STATUS FLAGS|
    +------+------+
           |
           ?
   "Was the result zero?"
           |
           ?
       Branch?
```

We will study each flag individually when we begin working with instructions.

---

# ? Trail Sign -- Registers Are Not Variables

A beginner may be tempted to think:

> "A register is just a variable."

That is useful as a first approximation.

But it is not completely correct.

A register is part of the CPU itself.

It has:

* a specific hardware implementation;
* a specific size;
* specific instructions that can operate on it;
* specific side effects;
* specific relationships with the CPU's internal operation.

This distinction will become increasingly important as we move from programming concepts to hardware-level reasoning.

---

# ? Layer 3 -- Technical View

## The 6510 and the 6502 Family

The 6510 belongs to the same general processor family as the famous MOS 6502.

The 6502 became one of the most influential 8-bit CPUs of its generation.

Variants of the architecture appeared in many systems.

The 6510 can be understood as a member of this family with additional functionality designed for systems such as the Commodore 64.

The C64's CPU is therefore not an arbitrary processor.

It is part of a historically important CPU architecture that became deeply connected with the rise of affordable personal computing.

---

# The Special Feature of the 6510

One of the most interesting differences is the additional I/O capability built into the 6510.

The processor provides a small set of pins that can be controlled through an internal I/O port.

In the C64, this capability is used for important system functions, including memory configuration.

This is one of the reasons the 6510 is particularly interesting to C64 programmers.

The CPU does not merely execute instructions.

It also participates directly in the machine's memory configuration.

Later we will see how this connects to the famous C64 memory banking mechanisms.

For now, remember:

> **The 6510 is not simply "a 6502 with a different name."**

Its role in the C64 architecture is worth studying in its own right.

---

# 8 Bits -- What Does That Actually Mean?

The 6510 is an **8-bit CPU**.

But what does that mean?

Very roughly, it means that many of the CPU's primary data operations are designed around 8-bit quantities.

An 8-bit value contains:

```text
8 bits
?
11111111
```

There are:

```text
2? = 256
```

possible combinations.

Therefore an unsigned 8-bit value can represent:

```text
0 - 255
```

For example:

```text
00000000 = 0
00000001 = 1
00000010 = 2
...
11111111 = 255
```

This small range is one of the fundamental characteristics of an 8-bit machine.

And yet...

The C64 accomplished astonishing things within those constraints.

That is one of the reasons we are here.

---

# 8-Bit Does Not Mean 8-Bit Everything

This is an important clarification.

Calling the 6510 an 8-bit CPU does **not** mean that every quantity inside the architecture is always 8 bits.

For example, the Program Counter is 16 bits wide.

This allows the CPU to address a 64 KB address space.

Conceptually:

```text
8-bit data processing
+
16-bit addressing
=
6510 system architecture
```

This distinction will become very important when we study the C64 memory map.

---

# The 64 KB Address Space

The 6510 uses a 16-bit address.

A 16-bit address provides:

```text
2¹? = 65,536
```

possible addresses.

That corresponds to:

```text
64 KB
```

of address space.

Therefore the CPU can address locations from:

```text
$0000
```

through:

```text
$FFFF
```

This does **not** mean that all 64 KB are always RAM.

That is one of the most important things we will discover next.

The address space is a map.

Different addresses can correspond to:

* RAM;
* ROM;
* I/O registers;
* Character ROM visibility;
* or different underlying resources depending on memory configuration.

The CPU sees addresses.

The hardware decides what those addresses represent.

---

# ? A First Look at the Bus

The CPU communicates with the rest of the system through electrical signals.

At a simplified level we can think in terms of:

```text
        CPU
         |
 +-------+--------+
 |       |        |
 ?       ?        ?
Address  Data    Control
 Bus     Bus      Signals
```

The **address bus** tells the system which location the CPU wants to access.

The **data bus** carries the data being read or written.

Control signals coordinate the operation.

This is a simplification, but it gives us the correct conceptual foundation.

Later we will examine the actual 6510 signals and timing in much greater detail.

---

# ? The CPU Is Not Alone

At this point we can connect the previous Stage to this one.

We have already met:

* the VIC-II;
* the SID;
* CIA 1;
* CIA 2;
* memory.

Now we can see the CPU in context.

```text
                         +---------------+
                         |     6510      |
                         |      CPU      |
                         +-------+-------+
                                 |
                         ADDRESS / DATA
                                 |
             +-------------------+------------------+
             |                   |                  |
             ?                   ?                  ?
         MEMORY               VIC-II              I/O
       RAM / ROM              VIDEO          CIA / SID etc.
```

The C64 is not powerful because the 6510 is individually extraordinary.

It is powerful because **all of these components work together**.

And later we will discover that programmers learned how to exploit their interaction.

---

# ? Layer 4 -- Engineering View

## The CPU as a Deterministic Machine

At a deeper level, the 6510 is not "thinking."

It does not understand:

> "This is a game."

It does not understand:

> "This is a sprite."

It does not understand:

> "This is music."

It executes electrical operations according to the architecture defined by its instruction set and timing.

If the programmer writes a sequence of instructions that modifies a VIC-II register, the CPU does not know that it is "changing the screen."

It simply performs a write operation.

The meaning comes from the interaction between the CPU and the hardware.

This distinction is fundamental to reverse engineering.

---

# Why Timing Matters

Suppose we execute an instruction that changes a VIC-II register.

It is tempting to think:

```text
CPU writes value
        ?
VIC-II changes
        ?
done
```

But real hardware is temporal.

The operation takes time.

The VIC-II is also operating according to its own timing.

The raster beam is moving.

Memory accesses are occurring.

Interrupts can happen.

The CPU and VIC-II interact during specific clock cycles.

This is where C64 programming becomes particularly fascinating.

Later we will discover techniques that deliberately exploit **when** something happens, not merely **what** happens.

That is the territory of:

* raster interrupts;
* cycle-exact programming;
* bad lines;
* VIC-II timing tricks;
* sprite multiplexing;
* FLI;
* VSP;
* and many other advanced techniques.

We are not there yet.

But now we know why they are possible.

---

# ? Laboratory Exercise -- Your First CPU Thought Experiment

Imagine the following conceptual program:

```asm
LDA #$01
LDA #$02
LDA #$03
```

What will be inside A at the end?

The answer is:

```text
A = $03
```

Why?

Because each instruction replaces the previous value.

The CPU is not remembering all three values in A.

It executes them sequentially.

Now imagine:

```asm
LDA #$01
STA $0400
LDA #$02
STA $0401
```

Now the CPU is interacting with memory.

Conceptually:

```text
A = $01
    ?
$0400 = $01

A = $02
    ?
$0401 = $02
```

This tiny example already contains the fundamental relationship:

```text
CPU
 ?
register
 ?
memory
```

Soon we will turn this conceptual understanding into real machine code.

---

# ? Cartello del Sentiero -- Non Correre

At this point it may be tempting to jump directly into Assembly.

Don't.

The mountain is still ahead.

Before writing complex routines, we need to understand:

* binary;
* hexadecimal;
* memory addresses;
* registers;
* instructions;
* addressing modes;
* stack;
* flags;
* interrupts.

These are the basic tools of the trail.

Once they become familiar, Assembly stops looking like a wall of mysterious symbols.

It becomes a language.

---

# ? Put Into the Backpack

After this Stage, carry these concepts with you:

* CPU;
* 6510;
* 6502 family;
* instruction;
* fetch-decode-execute cycle;
* accumulator A;
* X register;
* Y register;
* Program Counter;
* Stack Pointer;
* Processor Status;
* flags;
* 8-bit data;
* 16-bit addresses;
* 64 KB address space;
* address bus;
* data bus;
* control signals;
* CPU/VIC-II interaction;
* timing.

You do not need to memorize every detail yet.

Understanding the relationships is more important.

---

# ? Vista Point

Look back at the previous Stage.

We started with a motherboard containing many mysterious chips.

Now one of those chips has become a little less mysterious.

The 6510 is no longer simply:

> "the CPU."

It is:

> a small 8-bit processor executing instructions, using registers, accessing a 16-bit address space and communicating with the other hardware components of the C64.

That is already a significant step.

---

# ? Next Stage

## Stage 004 -- Understanding Memory

The next major question is:

> **Where does the CPU get its instructions and data?**

The answer leads us directly into memory.

We will discover:

* RAM;
* ROM;
* addresses;
* the C64 memory map;
* BASIC ROM;
* KERNAL ROM;
* Character ROM;
* I/O space;
* Color RAM;
* memory banking;
* and why "64 KB" does not tell the whole story.

The trail will become steeper.

Because this is where the C64 begins to reveal one of its most important secrets:

> **The CPU sees a 64 KB address space, but the machine contains more complexity behind that map.**

---

# ? Stage Checkpoint

The previous checkpoint was:

> **"I can look inside the C64 and recognize its main hardware specialists."**

This checkpoint is:

> **"I understand what the CPU is, what the 6510 does, and how it communicates with the rest of the machine."**

The next summit is already visible.

**Memory.**

And once we understand memory, we will finally be able to ask the question that every C64 Assembly programmer eventually asks:

> **"What exactly happens when I write to an address?"**

**READY.**
