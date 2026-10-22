# Field Report - October 21, 2026

## Overview

Today's studies focused on three areas:

- Arduino interrupt concepts and practical applications
- C programming memory management and string handling
- Historical and practical context of the C programming language through Pluralsight training

---

# Arduino

## Chapter Completed

### Hour 16 – Adding Interrupts

## Activities

- Completed reading the chapter on interrupts.
- Reviewed a new sketch and circuit demonstrating how an interrupt can dynamically modify the duration of the green-light delay in an existing traffic-light experiment.
- Continued building familiarity with event-driven programming concepts used extensively in embedded systems.

## New Glossary Terms

| Term | Definition |
|--------|------------|
| Interrupt | A hardware or software signal that temporarily halts normal program execution so a higher-priority task can be serviced. |
| Interrupt Service Routine (ISR) | A special function automatically executed when an interrupt occurs. |
| Resource-Constrained Environment (RCE) | A computing environment in which memory, processing power, storage, bandwidth, or electrical power are limited and must be carefully managed. Common in embedded systems, microcontrollers, IoT devices, and battery-powered electronics. |

## Observations

This chapter provided a practical introduction to asynchronous event handling, a foundational concept for embedded systems. Unlike polling-based solutions, interrupts allow a microcontroller to respond immediately to external events while continuing normal program execution the rest of the time.

---

# C Programming

## Objective

Extended the string and pointer experiment from the previous field report by exploring:

- String length calculation
- Pointer-array size calculation
- Character-pointer size determination
- Memory footprint comparisons
- Array indexing versus pointer arithmetic

---

## Key Concepts Explored

### 1. Contiguous Character Arrays vs. Arrays of Pointers

The program compares:

```c
char chapters[5][27];
```

with:

```c
const char *chapters_ptr[5];
```

The two-dime*sional array allocates fixed stora*e for every string, while the poin*er array stores only memory addres*es that reference existing string *iterals.

---

### 2. Array Memory*Usage

The program measures memory*consumption using `sizeof()`.

Exa*ple:

```c
printf("The chapters ar*ay uses %zu bytes of memory.\n",
 *     sizeof(chapters));
```

and

*``c
printf("The chapters_ptr array*uses %zu bytes of memory.\n\n",
  *    sizeof(chapters_ptr));
```

Th*s exercise reinforces the differen*e between storing data directly an* storing references to data.

---
*### 3. Character Arrays and Pointe*s

The experiment also compares:

*``c
char myName[] = "Paul";
char *MyName = myName;
```

**Observations:**

- The array contains the cha*acters themselves.
- The pointer c*ntains only an address.
- `sizeof(*MyName)` returns the storage requir*d for the entire array.
- `sizeof(*MyName)` returns the size of the p*inter itself.

---

### 4. Determining Array Length

The number of rows in the chapter array is calculated with:

```c
size_t counter =
   sizeof(chapters) / sizeof(chapters[0]);
```

This technique remains one of the most common and reliable methods for determining the element count of a statically allocated array.

---

### 5. Traversing Data Structures

The experiment demonstrates two traversal techniques.

#### Array Indexing

```c
for (size_t i = 0; i < counter; i++) {
    printf("chapters[%zu] is %s\n", i, chapters[i]);
}
```

#### Pointer Arithmetic

```c
for (size_t i = 0; i < counter; i++) {
    printf("(chapters_ptr + %zu) is %s\n",
           i, *(chapters_ptr + i));
}
```

The exercise reinforces the fact that arrays and pointers are closely related concepts in C while remaining distinct language constructs.

---

### 6. Calculating String Lengths

Using `strlen()`:

```c
strlen(*(chapters_ptr + i));
```

The function reports the number of visible characters in a string but excludes the null terminator (`'\0'`).

---

### 7. Pointer Array Analysis

The experiment calculates:

```c
size_t sizeOfPointerArray =
    sizeof(chapters_ptr) / sizeof(chapters_ptr[0]);
```

and

```c
size_t sizeOfCharPointer = sizeof(char *);
```

These values are then used to calculate the total storage occupied by the pointer array:

```c
sizeOfPointerArray * sizeOfCharPointer
```

This provides a concrete demonstration of how pointer-based structures consume memory.

---

## Lessons Learned

### Memory Awareness

Understanding memory footprints becomes increasingly important when moving from desktop development to resource-constrained embedded environments.

### Arrays vs. Pointers

While arrays and pointers often appear interchangeable, they have different storage characteristics and behavior. Measuring their size directly highlights those differences.

### Practical Use of `sizeof()`

`sizeof()` remains one of the most valuable compile-time tools available in C for:

- Memory analysis
- Capacity planning
- Array length calculations
- Embedded systems development

---

## Notable Takeaway

The exercise transformed several previously abstract concepts into measurable observations. By calculating actual memory usage and comparing data structures directly, the distinction between character arrays, pointer variables, and pointer arrays became significantly clearer.

---

# Pluralsight Training

## Course Started

### C Language: The Big Picture

## Topics Covered

- When, where, and why C was created.
- How C programs are structured at a high level.
- The fundamental tools required for C development:
  - Text editor
  - Compiler
- Where C fits within modern computing.
- Why C has remained relevant for decades.
- Why C continues to be heavily used in embedded systems.

## Reflection

The section discussing C's role in embedded systems was particularly relevant. As my studies continue moving toward microcontrollers and eventually STM32 development, understanding why C remains the dominant language in embedded environments helps connect current programming exercises to long-term engineering goals.

The enduring popularity of C appears to stem from its combination of simplicity, efficiency, portability, and close interaction with computer hardware. These characteristics explain why it remains the foundational language behind many operating systems, device drivers, firmware platforms, and embedded products.

---

# Daily Assessment

Today's work tied together theory and practice from multiple angles:

- Arduino introduced interrupt-driven design.
- C programming reinforced memory organization and pointer fundamentals.
- Pluralsight provided historical and architectural context for the language itself.

Taken together, the day strengthened the connection between language fundamentals and their real-world application in embedded systems. The progression from arrays and pointers to interrupts and embedded architecture makes the overall learning path feel increasingly cohesive and purposeful.
