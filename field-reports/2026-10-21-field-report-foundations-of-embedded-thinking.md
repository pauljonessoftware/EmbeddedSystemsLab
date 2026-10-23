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
|---|---|
| Interrupt | An event or signal that causes a processor to transfer control to an interrupt handler, subject to the processor's interrupt configuration and priority rules. |
| Interrupt Service Routine (ISR) | A function or handler executed in response to an interrupt. An ISR should generally execute quickly and avoid blocking operations. |
| Resource-Constrained Environment (RCE) | A computing environment in which limited resources—such as memory, processing capacity, storage, bandwidth, or electrical power—influence software design and implementation. Common examples include embedded systems, microcontrollers, and IoT devices. |


## Observations

This chapter provided a practical introduction to asynchronous event handling, a foundational concept in embedded systems. Unlike polling-based approaches, interrupts allow a microcontroller to respond to supported events without continuously checking for them in the main program.

When an interrupt is accepted, the processor transfers control to the associated interrupt handler and subsequently resumes normal execution. The timing and handling of interrupts depend on the hardware, interrupt configuration, and software implementation.

* * *

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

The two-dimensional array allocates fixed storage for every string, while the pointer array stores only memory addresses that reference existing string literals.

---




### 2. Array Memory Usage

The program measures memory consumption using `sizeof()`.

```c
printf("The chapters array uses %zu bytes of memory.\n",
       sizeof(chapters));

printf("The chapters_ptr array uses %zu bytes of memory.\n\n",
       sizeof(chapters_ptr));
```

This exercise reinforces the difference between storing data directly and storing pointers to data.

---

### 3. Character Arrays and Pointers

The experiment also compares:

```c
char myName[] = "Paul";
char *pMyName = myName;
```

Observations:

- `sizeof(myName)` returns the size of the entire array, including the null terminator.
- `sizeof(pMyName)` returns the size of the pointer itself.
- `sizeof(*pMyName)` returns the size of one character, which is `sizeof(char)` and is always 1 in C.
- `strlen(myName)` and `strlen(pMyName)` both return 4 because the string contains four visible characters.

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

size_t sizeOfPointerArray =
    sizeof(chapters_ptr) / sizeof(chapters_ptr[0]);

size_t sizeOfCharPointer = sizeof(char *);

size_t calculatedSize =
    sizeOfPointerArray * sizeOfCharPointer;

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
