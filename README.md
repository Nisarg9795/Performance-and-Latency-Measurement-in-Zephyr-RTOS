# Performance-and-Latency-Measurement-in-Zephyr-RTOS
Developed an application to measure interrupt latency and context switching overhead of Zephyr RTOS. It performed 3 measurements in sequence: interrupt latency without background computing, interrupt latency with background computing, and context switching overhead. For background computing, a message passing operation between two threads via a message queue was used. For each measurement, 500 samples were collected and saved in separate buffers. A shell module was used to print out the collected samples from any one of buffer and show the results
NAME: CSE 522 Assignment-3: Measurement in Zephyr RTOS
_______________________________________________________________________________________________________________________________________________________________________________________________________

AUTHORS:  Team-13

Nisarg Trivedi (1213314867)
Nagarjun Chinnari (1213287788)
_______________________________________________________________________________________________________________________________________________________________________________________________________

INCLUDED IN REPOSITORY:

-> .c (Program Source code)
-> README
-> Report

_______________________________________________________________________________________________________________________________________________________________________________________________________

ABOUT: 

This project is about measuring the interrupt latency and the context switching overhead for 
Zephyr OS. Interrupt latency is the total delay between the interrupt signal being asserted and the start of the
interrupt service routine execution. Context switching overhead is the delay of context switching
process of saving the context of the executing thread, restoring the context of the new thread, and starting
the execution of the new thread. Here we measure the interrupt latency without a background task and 
once with the background task. The difference is observed and shown in the form of a historgram.
_______________________________________________________________________________________________________________________________________________________________________________________________________

SYSTEM REQUIREMENTS:

-> Linux machine for host
-> Zephyr 1.10.0 and SDK: Zephyr-0.9.2
-> LED
-> Intel Galileo Gen2 board
-> Connecting wires
-> CMake version 3.8.2 or higher is required
_______________________________________________________________________________________________________________________________________________________________________________________________________

SETUP:

-> Install Zephyr
-> Format SD Card as FAT
-> Create the  directories
   efi
   efi/boot
   kernel
-> after cloning find the binary at $ZEPHYR_BASE/boards/x86/galileo/support/grub/bin/grub.efi and copy it to $SDCARD/efi/boot and rename it to bootia32.efi.
-> Create a $SDCARD/efi/boot/grub.cfg file containing: 
   set default=0
   set timeout=10
   menuentry "Zephyr Kernel" {multiboot /kernel/zephyr.strip}

-> Make sure that cmake version is 3.8.2 or higher
-> Export ZEPHYR_GCC_VARIANT=zephyr
-> Export ZEPHYR_SDK_INSTALL_DIR=<sdk installation directory>
-> Export ZEPHYR_TOOLCHAIN_VARIANT=zephyr
-> Connect GPIO pins on Galileo Gen 2, IO5 is PWM and IO2 is input pin.
_______________________________________________________________________________________________________________________________________________________________________________________________________

COMPILATION:

-> type: cd $ZEPHYR_BASE/samples/measure_02
-> mkdir build
-> cd build
-> cmake -DBOARD=galileo ..
-> make

-> Copy zephyr.strip file to in $ZEPHYR_BASE/samples/measure_n/build/zephyr to $SDCARD/kernel
-> Put SD Card in board and reboot.

After the tasks are executed enter the shell commands:
-> select print_module 
-> print
_______________________________________________________________________________________________________________________________________________________________________________________________________

