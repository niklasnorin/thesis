# Introduction

## Background
The traditional definition of a personal work place as a desk in a cubical is slowly, but surely, on its way to be a thing of the past. The amount of people working remotely, both self-employed and not, has literally exploded in the wake of the dramatic increase of widely available, often free, internet connectivity. 3.7 Million people in the U.S. is already working remotely at least half of the time (US Census Bureau) and working from home among non-self-employed is up more than 100% since 2005. When given the choice, as many as 80-90% of the US workforce said that they would choose to do so if they could.

The ability to work remotely is very much decided on what kind of work you do. Most non-self-employed people who work remotely today only need access to a computer to get their work done. In the engineering work community, working remotely is no impediment in areas such as architecture, electronic CAD or in most software development roles. The more dependant you are on having access to other tools than your computer however, the less likely you are to be able to work remotely, even if that would be desirable both for the employee and employer.

Within the area of electrical engineering, embedded software development is just one area of engineering that very often rely heavily on other tools than just a computer. It comes with the territory, working with electronics is bound to put you in front of a logic analyser as well as one development board or another some day. The more hardware and tools, the less the likelihood of being able to work remotely or, at the very least, increased friction of starting to do so. Dragging kits and equipments to and from work is not only tedious, it also brings with it the risk of physical breakage or ESD related damages of both hardware and tools. In addition, not everyone has the option of having a permanent electronics lab at home, so starting to work often means setting everything up and wrapping it up means packing it all up again.

The aim of this thesis is to define and, in part, implement, a suggestion for an architecture that would enable embedded software developers to remotely develop, debug and test real embedded software. This thesis will peer into existing work, look into the pros and cons of emulation versus real hardware, take a deep-dive into developing and debugging SW on a remote target as well as looking into how to stimulate inputs and view outputs remotely. It will also take a look into attaching virtual tools to the target, such as logic analyzers or serial port emulators.

The architecture itself will be developed with the latest advances in mind, in everything from scalable software containers to combined MCU-FPGA systems. The intention is to come up with an architecture that covers the most common use-cases of modern embedded software development and one that can scale from one remote developer to thousands.

## Purpose
Working with embedded software development traditionally means having access to the physical hardware, often in the form of a development kit connected to a PC. This thesis sets out to define and, in part, implement a software architecture that enables embedded software developers to develop, debug and test embedded software in an emulated environment, without access to hardware.

## Goal
Some of the questions that this thesis sets out to answer are:

1. Is it possible to set up an environment which allows an embedded software developer to perform most development related tasks without access to the physical hardware?

2. Is it possible to do this is such an unobtrusive way, that the exact same program executable can be run both on the real hardware target and in the emulation environment?

3. Is it possible to present outputs and stimulate inputs in such an environment in ways not even possible with real hardware?

4. What are the main limitations of such an emulated software environment?

## Method

## Limitation
To be able to focus on the core innovative aspects of the work, this report sets some strong limitations on scope.

### Linux
This thesis will only look into embedded software built on top of the Linux kernel.

### Architecture
Most embedded systems uses the ARM architecture, while most computers used by developers are x86 or AMD64. This means that to run a compiled program targeting an ARM architecture on the developers PC, it either needs to be cross-compiled or run through an emulator, such as QEMU. 

Because of time constraints, this thesis uses a so called interpreted programming language instead of a compiled one. This works by having a piece of software called an interpreter compiled specifically for each architecture, this in turn parses and executes the code on the fly. This setup means that the exact same code can be executed both on a PC and the target without any modification.

### Digital signals
The instrumentation and hardware emulation in this thesis focuses on digital emulation of signals and communication channels. It does not aim to accurately emulate analogue signals or physical models.

## Tools

- Add hardware that will be used in the hardware demo

The software tools used in this thesis are documented in depth in the method.

## Source code
It has yet to be decided if the source code which was written as a part of this work will be released as open-source after the publication of this thesis.

The frameworks, concepts and libraries used in the solution are thoughroughly documented. 