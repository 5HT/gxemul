GXemul
======

Overview  --  What is GXemul?
-----------------------------

GXemul is a framework for full-system computer architecture emulation.
Several processor architectures and machine types have been implemented.
It is working well enough to allow unmodified "guest" operating systems to
run inside the emulator, as if they were running on real hardware.

The emulator emulates (networks of) real machines. The machines may consist
of ARM, MIPS, Motorola 88K, PowerPC, and SuperH processors, and various
surrounding hardware components such as framebuffers, busses, interrupt
controllers, ethernet controllers, disk controllers, and serial port
controllers.

GXemul, including the dynamic translation system, is implemented in portable
C++, which means that the emulator will (at least in theory) run on
practically any modern host architecture and unix-like operating system, for
which a C++ compiler is available.

The documentation lists the machines and specific guest operating systems
that can be regarded as "working" in GXemul. The guest operating system
that works best in GXemul is NetBSD/pmax.

Possible uses of GXemul include:

*  running guest operating systems in a "sandboxed" environment

*  compiling your source code inside a guest operating system which you
     otherwise would not have access to (e.g. various exotic ports of
     NetBSD or OpenBSD), to make sure that your source code is portable to
     those platforms

*  educational purposes, e.g. to learn how to write code for MIPS

*  hobby operating system development; the emulator can be used as a
     complement to testing your code on real hardware

*  preservation of computer history, by simulating old/obsolete hardware

*  simulating (ethernet) networks of computers running various
     operating systems, to study their interaction with each other

*  debugging code in general

Use your imagination :-)

Note regarding the new 0.6 framework
------------------------------------

Only very few emulation modes have been rewritten to use the 0.6 (C++)
framework; the bulk of GXemul is still made up of legacy emulation modes,
written in C.

The long-term plan is to rewrite all of the emulation modes to use the
new framework, but this will take quite some time.

GXemul's limitations
--------------------

*  GXemul is not a cycle-accurate simulator when it comes to simulating
     modern CPUs, because it does not simulate things smaller than an
     instruction. Pipe-line stalls, instruction latency effects, out-of-order
     execution etc. are more or less completely ignored.

     (Note: The new framework could possibly allow cycle-accurate models
     to be implemented; however, no such component has been written.)

*  Hardware devices have been implemented in an ad-hoc and as-needed manner,
     usually only enough to fool certain guest operating systems, e.g. NetBSD,
     that the hardware devices exist and function well enough for those guest
     operating systems to use them.

(A consequence of this is that a machine mode may be implemented well
enough to run NetBSD for that machine mode, but other guest operating
systems may not run at all, or behave strangely.)

Quick start
-----------

To compile, type './configure' and then 'make'. This should work on most
Unix-like systems. If it does not, then please mail me a bug report.

If you are impatient, and want to try out running a guest operating system 
inside GXemul, read this:  doc/guestoses.html#netbsdpmaxinstall

If you want to use GXemul for experimenting with code of your own,
then I suggest you compile a Hello World program according to the tips
listed here:  doc/experiments.html#hello

Please read the rest of the documentation in the doc/ sub-directory for
more detailed information on how to use the emulator.

Sample OS
---------

```
wget http://www.helenos.org/releases/HelenOS-0.4.3-mips32-GXemul.boot
./gxemul -E oldtestmips HelenOS-0.4.3-mips32-GXemul.boot
```

Feedback
--------

If you have found GXemul useful in some way, or feel like sending me
comments or feedback in general, then mail me at gavare@gmail.com.

Copyright
---------

Copyright (C) 2003-2014  Anders Gavare
