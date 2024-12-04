Exercise 6 – Demonstrate a simple way to eliminate
resource contention - suspending the scheduler.

This project demonstrates the control of access to shared resources using FreeRTOS Critical Sections. The system is designed to manage synchronization between tasks operating multiple LEDs. The implementation uses the STM32F401CCU6 as the main microcontroller.


Diagram Task :


Required Hardware:

STM32F401CCU6
LEDs
Required Software:

STM32CubeIDE
FreeRTOS
How It Works:

Semaphore and Task Initialization:

The project utilizes two main tasks: GreenTask and RedTask.
Both tasks compete to access a shared resource (the AccessSharedData function) protected by a Critical Section.
Task Description:

a. RedTask:

Turns on the red LED.
Enters the critical section to access the shared resource.
Turns off the red LED and delays for 100ms before repeating.

b. GreenTask:

Turns on the green LED.
Enters the critical section to access the shared resource.
Turns off the green LED and delays for 500ms before repeating.

Critical Section Mechanism:

The critical section is used to prevent other tasks from accessing the shared resource simultaneously.
The task currently in the critical section locks the resource, forcing other tasks to wait until the section is released.
Task Behavior:

a. GreenTask and RedTask:

Both tasks attempt to enter the critical section alternately.
If a conflict occurs (e.g., the resource is already in use), the yellow LED lights up to indicate contention.
b. Critical Section Control:

The use of taskENTER_CRITICAL() and taskEXIT_CRITICAL() ensures exclusive access to the shared resource.
LED Operation Cycle:

The green and red LEDs light up alternately with their respective delay times.
The yellow LED lights up only when contention occurs while accessing the shared resource

Hardware Overview:

Demo vidoe:
