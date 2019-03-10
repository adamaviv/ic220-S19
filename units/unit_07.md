# Processor Design

Readings: Chapter 4.1-4.4

> These unit notes are **not** design to replace readings from the book! There
> are to provide structure to material covered in class and provide you an
> outline for using the book. **You are still required to do the course
> readings** in which you will find much more detail, and those details will be
> evaluated in quizzes, homework, and exams.

Images from *Computer Organization and Design* used here under fair-use for
educational purposes. Not intended for reproduction or redistribution, and
subject to the copyright owners of *Computer Organization and Design*. 

## Single-Cycle CPU

In this unit, we will explore how to build a *single-cycle CPU* that can
implement a subset of the MIPS language. A single-cycle CPU assumes that we
execute one instruction at a time, with as many clock cycles as needed to finish
that instruction before moving on to the next instruction. To put it another
way, one instruction at a time, and the performance of the CPU is how many
cycles of the clock it takes to complete that instruction (or any instruction,
on average). 

This is not how CPU's are built today. Single-Cycle CPU design is slow, and we
have a number of ways to improve the performance. Notably, pipeline (or
multi-cycle CPU) design will allow for multiple instructions to be in the
process of executing, at the same time. We will explore this in a later unit. 

## Simplified Model

As we proceed, we will assume a simplified model of MIPS. This includes

* Memory-References: `lw`, `sw`
* Arithmetic: `add`, `sub`, `and`, `or`, `slt`
* Control: `beq`, `j`

While clearly a subset of the MIPS instructions, this is a very expressive
subset that will allow us to reason about a number of programs. As we understand
the design better, we will explore what new components would be needed to add
additional instructions.

Additionally, as part of our generic implementation, we will assume we have
access to other data/control components:

* Program Counter: `pc` register that supplies the address of the next
  instruction to be executed.
  
* Read/Write Registers: we will have access to the standard 32-bit registers of
  MIPS, including `$a`, `$s`, `$v`, and `$t` registers. Typically, we will refer
  by number, but these are the same register types

* ALU: We have the existing circuitry of an arithmetic-logic-unit. Refer to prior
  units for information.

* Mux'es: Control components that will allow us to select between different
  inputs based on signal wires.

## Timing Methodology

In the single-cycle design, we will use an abstraction to simplify the
presentation. Each box/rectangle will represent a state element (plus some other
logic) and transitions between elements will occur at clock edges. One full
cycle of the clock takes us from one sate element to the next, passing through
some combination logic describing which state element receives the signal from
the previous element.


```
  .--------.                             .--------.
  | state  |                             | state  |
  | element| -> ( combination logic ) -> | element|
  |   1    |                             |   2    |
  '--------'                             '--------'
    .-------------------.                  .---------
    |                   |                  |  
----'                   '------------------'
clock cycle

```

For example, *state element 1* may refer to logic that reads from an instruction
from memory and stores in the state-memory. After which, the bits of that
instructions are processed in the digital, combination logic, leading to the
next state element which may be associated with some form of executing that
instruction. After a series of clock cycles, linking state elements together
through some logic, we will eventually execute a instruction to produce a
result.

## Data Path 


Below is our simplified view of the data path of a single-cycle CPU. Note, much
of the control elements are not present, and instead we only concern ourselves
with where data is flowing to.


![simple-data-path](/imgs/cpu/simple-data-path.png "Copyright © 2014 Elsevier Inc. All rights reserved.")


From this diagram, we can start to see the various major components of the data
path.


1. (**PC**) Managing the PC: the program counter feeds into loading
   instructions, will be incremented (by 4), and also be used to determine
   branching/jumping. 
   
1. (**Instruction Memory**) Fetching Instructions: Using the PC address, load
   the next instruction that is to be executed.
   
1. (**Registers**) Loading data from registers: Breaking apart the data of the
   instructions, loading/reading/writing of the appropriate registers as
   referred by their numbers in the instructions, and using these as output to
   the ALU or the data storage elements.
   
1. (**Data Memory**) Storing/Loading from Memory: This unit processes
   loading/storing instructions that have to go out to main memory, separate
   from loading instructions.

As we zoom into each of these pieces, we will de-abstract some of the components
and expand on the procedures therein to see how all these parts connect together. 

### Fetching Instructions

First, let's take a closer look at the **instruction memory** component and the
role of the PC.

![fetching](/imgs/cpu/fetching.png "Copyright © 2014 Elsevier Inc. All rights reserved.")

Following the diagram, the PC component is read into the *read address* logic of
the **instruction memory**. This logic will load the bits of the instruction
into the state element, which will write out as *instruction* on the end of this
clock cycle.

The PC, which is an address/number, will also feed into an *add* ALU unit, with
fixed input of 4. Why 4? Well, the width of a MIPs instruction is 4-bytes, so
the next instructions is 4 bytes more than the current instruction. The result
of the add loops around and gets stored back in the PC register.

Note, that if the instructing is a jump (`j`), then the offset from the current
PC address (+4) *plus* the address encoded in the j-type instruction is the next
PC. Looking back in the larger diagram (previous subsection), you can see this
data flow as part of the output from *instruction* leading to a second ALU that
can calculate the next PC in cases of a jump.

### R-Type Instructions


![r-type](/imgs/cpu/r-type.png "Copyright © 2014 Elsevier Inc. All rights reserved.")


### Load and Store


![load-store](/imgs/cpu/load-store.png "Copyright © 2014 Elsevier Inc. All rights reserved.")


### Branching 

![branching](/imgs/cpu/branching.png "Copyright © 2014 Elsevier Inc. All rights reserved.")
