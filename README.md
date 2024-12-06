# Exercise 6: Eliminating Resource Contention by Suspending the Scheduler

This project demonstrates the control of access to shared resources using **FreeRTOS Critical Sections**. The system is designed to manage synchronization between tasks operating multiple LEDs. The implementation uses the **STM32F103C8T6** as the main microcontroller.

---

## **Diagram Task**
[Insert your task scheduling diagram here]

---

## **Required Hardware**
- **STM32F103C8T6** Microcontroller
- LEDs (Green, Red, Yellow)

---

## **Required Software**
- **STM32CubeIDE**
- **FreeRTOS**

---

## **How It Works**

### **Semaphore and Task Initialization**
The project utilizes two main tasks:
1. **GreenTask** 
2. **RedTask**

Both tasks compete to access a shared resource (`AccessSharedData`) that is protected by a **Critical Section**.

### **Task Description**

#### **RedTask**
- Turns on the **red LED**.
- Enters the critical section to access the shared resource.
- Turns off the red LED.
- Delays for **100ms** before repeating.

#### **GreenTask**
- Turns on the **green LED**.
- Enters the critical section to access the shared resource.
- Turns off the green LED.
- Delays for **500ms** before repeating.

---

## **Critical Section Mechanism**
- A **critical section** is used to prevent other tasks from accessing the shared resource simultaneously.
- The task currently in the critical section locks the resource, forcing other tasks to **wait** until the section is released.
- Functions used:
  - **`taskENTER_CRITICAL()`**
  - **`taskEXIT_CRITICAL()`**

---

### **Task Behavior**

#### **GreenTask and RedTask**
- Both tasks alternate in their attempts to access the critical section.
- If contention occurs (e.g., the resource is already in use), the **yellow LED** lights up as an indicator.

#### **Critical Section Control**
- The critical section ensures exclusive access to the shared resource, eliminating resource contention.

---

## **LED Operation Cycle**

| **LED**   | **Behavior**                                                                                 |
|-----------|-----------------------------------------------------------------------------------------------|
| **Green** | Lights up when the **GreenTask** accesses the shared resource and turns off after 500ms.       |
| **Red**   | Lights up when the **RedTask** accesses the shared resource and turns off after 100ms.         |
| **Yellow**| Lights up when contention occurs, indicating that the shared resource is already in use.       |

---

## **Hardware Overview**
- **Microcontroller**: STM32F103C8T6
- **LEDs**: 
  - **Green** (for GreenTask)
  - **Red** (for RedTask)
  - **Yellow** (for contention indicator)

---

## **Demo Video**

