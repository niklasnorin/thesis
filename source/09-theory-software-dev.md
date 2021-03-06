# Software Development Workflow

The way software is developed varies depending on if the application is intended to run natively on the developer's PC or if it is targeted to run on an embedded device.

## Native Application Software Development
Traditionally, one of the most wide-spread applications is a software application which runs natively on a PC. This could be a word processor, card game or massive industrial process management software suite.

![Native application software development cycle \label{2_1}](source/figures/2_1.png)

No matter what the software a developer writes, the workflow for a compiled language will be similar to what Figure \ref{2_1} shows. That is:

1. Write code
2. Compile code
3. Test code
4. Debug any problems
5. Repeat

The program is targeting a similar type of environment as the software developer's computer and is written, compiled, run and debugged on the developer's computer.

## Embedded Software Development
From a bird's-eye perspective, embedded software development might not seem to differ much from native application software development, see Figure \ref{2_2}.

![Embedded application software development cycle \label{2_2}](source/figures/2_2.png)

The workflow is similar:

1. Write code
2. *Cross-compile* code
3. Test code by executing it on the target
4. Debug any problems on the target
5. Repeat

Most modern laptops and desktops run on a x86 architecture [@ee-time-x86-marketshare] while modern embedded systems often run on an ARM processor architecture. Instead of using a traditional compiler, a cross-architecture compiler (or cross-compiler for short) is used to build and link a non-native application which can be executed on the target platform, but typically not on the local computer [@cross-compile].

When working with embedded software, the hardware which is intended to run the software is often referred to explicitly as the *target*. Once an executable has been built, it has to be moved to the target before being executed. This is typically done via a memory card, serial link or network connection to the target. This same connection can then be used to control the execution of the software on the target.

Working with another target than the local computer has far reaching implications on the development workflow. Debugging embedded software is also generally a bit harder to set up than debugging native applications, but very similar once set up correctly. For traditional debugging, which includes setting breakpoints and inspect variables, most embedded development environments come with a way of setting up a remote debug target. GDB, for example, the GNU Project Debugger, makes it possible to set up a remote debugging server on the target to which GDB connects [@gdb]. Once connected, GDB can be used in the same way as if developing a native application, often with full IDE, Integrated Desktop Environment, support for setting per-line breakpoints and inspecting memory.

### Hardware Abstraction Layer
When working with embedded software, having some sort of Hardware Abstraction Layer, or HAL, can make the developer's life easier. The main idea with a HAL is to decouple the application facing hardware interfaces from the actual hardware [@hal]. It makes it possible to run the same code on several platforms without having to worry about the underlying hardware being different. This is illustrated in Figure \ref{2_2_1}.

![Hardware Abstraction Layer \label{2_2_1}](source/figures/2_2_1.png)
