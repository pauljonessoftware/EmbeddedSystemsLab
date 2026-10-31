# 10302026 Field Report

## C Programming — Pointers & Memory Management

### Overview

Today's work focused on additional C programming memory-management concepts, specifically **pointer-to-pointer indirection, arrays of character pointers, and passing pointers to functions**.

The experiments build on earlier work with pointers and arrays. The goal was to understand how pointers reference other objects in memory, how multiple levels of indirection work, and what happens when an array of pointers is passed to a function.

---

## Sample Program #1 — Pointer to a Pointer

**File:** `PointerToPointer.c`

```c
/*******************************************************************************
 *
 * File:        PointerToPointer.c
 * Author:      Paul A. Jones, Jr.
 * Created:     [2026-10-30]
 *
 * Description: A pointer variable stores the memory address of another object.
 *              A pointer to a pointer stores the address of another pointer
 *              variable. Each level of indirection requires an additional
 *              dereference operator to access the underlying object. This
 *              experiment demonstrates that the same character value can be
 *              accessed directly, through a single pointer, or through a
 *              pointer to a pointer.
 *
 * Target:      Native Desktop
 * Blog/Ref:    https://pauljonessoftware.com
 *
 ******************************************************************************/

#include <stdio.h>

int main(void) {
    char letter = 'A';
    char* ptr = &letter;
    char** pPtr = &ptr;

    // Display the addresses of each variable
    printf("Address of letter: %p\n", (void*)&letter);
    printf("Address of ptr:    %p\n", (void*)&ptr);
    printf("Address of pPtr:   %p\n\n", (void*)&pPtr);

    // Display the character through each level of access
    printf("Direct access: %c\n", letter);
    printf("Dereferencing ptr: %c\n", *ptr);
    printf("Dereferencing pPtr twice: %c\n", **pPtr);

    return 0;
}
```

### Output #1

Actual memory addresses will vary by execution.

```text
Address of letter: 0061FF18
Address of ptr: 0061FF14
Address of pPtr: 0061FF14

Direct access: A
Dereferencing ptr: A
Dereferencing pPtr twice: A
```

### Observations

The experiment demonstrates three levels of access to the same character:

- `letter` accesses the character directly.
- `*ptr` dereferences a pointer to access the character.
- `**pPtr` dereferences a pointer to a pointer, ultimately accessing the same character.

The declarations establish the following relationships:

| Variable | Type | What it stores |
|---|---|---|
| `letter` | `char` | The character `'A'` |
| `ptr` | `char*` | The address of `letter` |
| `pPtr` | `char**` | The address of `ptr` |

Each additional pointer level introduces another level of indirection. The expression `**pPtr` follows the pointer chain back to the original character.

---

## Sample Program #2 — Passing an Array of Pointers to a Function

**File:** `Prophets.c`

```c
/*******************************************************************************
 *
 * File:        Prophets.c
 * Author:      Paul A. Jones, Jr.
 * Created:     [2026-10-30]
 *
 * Description: Demonstrates passing an array of strings to a function.
 *              The array consists of character pointers. When passed to
 *              the function, the array expression decays to a pointer
 *              to its first element.
 *
 * Target:      Native Desktop
 * Blog/Ref:    https://pauljonessoftware.com
 *
 ******************************************************************************/

#include <stdio.h>
#include <stddef.h>

void displaySeers(const char** seers, size_t numberOfElements);

int main(void) {

    // This is an array of character pointers
    const char* seers[] = {
        "Abraham",
        "Isaac",
        "Jacob",
        "Moses",
        "Joshua"
    };

    // Calculate the number of elements in the array
    size_t numberOfElements = sizeof(seers) / sizeof(seers[0]);

    // Pass the array and its element count to the function
    displaySeers(seers, numberOfElements);

    return 0;
}

void displaySeers(const char** seers, size_t numberOfElements) {
    for (size_t i = 0; i < numberOfElements; i++) {
        printf("Seer: %s\n", *(seers + i));
    }
}
```

### Output #2

```text
Seer: Abraham
Seer: Isaac
Seer: Jacob
Seer: Moses
Seer: Joshua
```

### Observations

Although `seers` looks like an ordinary array of strings, it is actually an array of five character pointers. Each element points to the first character of a string literal.

When `seers` is passed to `displaySeers()`, the array expression decays to a pointer to its first element.

Because each element is a `const char*`, the resulting pointer is a `const char**`.

The function receives that pointer along with the number of elements. The element count must be passed separately because the function parameter is a pointer, not the original array.

The expression:

```c
*(seers + i)
```

is equivalent to:

```c
seers[i]
```

Both expressions access the pointer at position `i` in the array. That pointer is then supplied to `printf()` using the `%s` format specifier to display the corresponding string.

The `const` qualifier is intentional. The strings are string literals, and the program has no reason to modify their contents.

---

## Key Concepts Reinforced

Today's experiments helped connect several related C programming concepts:

1. **Pointer indirection:** A pointer stores the address of another object. A pointer-to-pointer stores the address of a pointer variable.
2. **Dereferencing:** Each level of indirection requires another dereference operator.
3. **Arrays of pointers:** An array can contain pointers rather than the actual data being referenced.
4. **Array decay:** When an array expression is passed as a function argument, it generally converts to a pointer to its first element.
5. **Function parameters:** An array parameter is adjusted to a pointer parameter. The function does not receive a copy of the original array.
6. **Pointer arithmetic:** Adding an integer to a pointer advances it by that number of elements, based on the type being pointed to.
7. **Array sizing:** `sizeof(array) / sizeof(array[0])` can determine the element count while the array is still in scope as an actual array. A pointer parameter does not retain that information.

## Conclusion

These experiments provided a practical opportunity to explore how C handles pointers, arrays, and function arguments.

The first program demonstrated multiple levels of pointer indirection. The second extended that understanding by showing how an array of character pointers is passed to a function and accessed through pointer arithmetic.

One particularly important discovery was **array decay**. An array is not itself a pointer, but in most expressions it is automatically converted to a pointer to its first element. Understanding that distinction helps explain why arrays and pointers can appear interchangeable in some situations while behaving very differently in others.

Further experiments will focus on passing arrays and pointers to functions, modifying the original data through pointers, and understanding the difference between changing a pointer's local value and changing the data it references.

**Measure it. Build it. Test it. Document it.**

---

## Suggested Future Exercises

The following exercises are natural extensions of today's work. Each isolates another aspect of pointers, arrays, and memory management.

### Exercise 1 — Compare `sizeof` Inside and Outside a Function

Create a program that prints:

- `sizeof(seers)` in `main()`.
- `sizeof(seers)` inside `displaySeers()`.

Observe the difference between the actual array's size and the size of the pointer parameter.

On a typical 64-bit system, the five-element array of pointers will occupy 40 bytes, while the pointer parameter will typically occupy 8 bytes.

### Exercise 2 — Modify an Array Element Through a Function

Pass an integer array to a function and change one of its elements. Then print the array in `main()`.

This demonstrates that although the pointer is passed by value, the function can use its copy of the address to modify the original array elements.

### Exercise 3 — Change a Pointer Through a Pointer-to-Pointer

Write a function that accepts an `int **` parameter and changes the caller's pointer to reference a different integer.

This demonstrates why pointer-to-pointer parameters are useful when a function needs to change the caller's pointer variable itself.

### Exercise 4 — Compare Array Indexing with Pointer Arithmetic

Using `Prophets.c`, print each name twice:

```c
printf("%s\n", seers[i]);
printf("%s\n", *(seers + i));
```

The output should be identical. This reinforces that array indexing is defined in terms of pointer arithmetic and dereferencing.