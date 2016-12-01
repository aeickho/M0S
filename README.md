# M0S
1KB Cortex M0 Real Time Operating System

Full blown RTOS written in Thumb ARM assembly language to fit in 1024 bytes.
It supports the following features:

- real time preemptive scheduling
- system tick counter
- idle task (which acts as memory janitor and combines consecutive free blocks)
- task creating
- task killing
- task sleeping
- mutexes (with blocking or non-blocking functionality)
- malloc and free
- IPC - inter-process communication

It was written for the Hackaday 1KB contest : https://hackaday.io/contest/18215-the-1kb-challenge

Where is it ?
-------------
All functionality of M0S is in m0s.asm file. There are some hard coded constants available in stm32f072.inc.
The demo cam be found in demo.c and demo.h

How to Build ?
--------------
Use one of the two shell scripts included :
- build_os_only
- build_demo
You have to edit them to replace the path of the ARM tools according to your setup

You can also use the included Makefile. By default it builds the OS only. 
You have to uncomment and comment two lines inside to build the demo. 
Instructions are provided in the Makefile.
You build by issuing "make" command. 
There is also a "make gdb" command which launches the debugger.

You will see a text message displaying the size of the actual code from the .elf file like this:

   text	   data	    bss	    dec	    hex	filename
   1024	      0	      0	   1024	    400	m0s.elf

This is the .bin file which is also generated buy the build commands

How to use ?
------------
I used a NUCLEO-F072RB board from ST Micro for testing. 
If you want to use a different microcontroller you will have to change the peripheral 
addresses and OS details in stm32f072.inc to match your Cortex-M0 system.

What does the demo do ?
-----------------------
Currently the demo plays with tasks and blinks two LED lights on the board, one already present 
on the board and one added externally:

	GPIOA pin 5
	GPIOB pin 5

License ?
---------
This software is being distributed as "Public Domain". You can do whatever you want with it, use it,
sell it, buy it, eat it, juggle it, you name it. There is a catch though, I will not be held responsible
for anything resulting from you doing those things to this code.
You are on your own !

I might be able to reply if you write me a message (I usually do if you are a polite person) but this 
feature is totally up to me and it should not be considered as "support for m0s".

