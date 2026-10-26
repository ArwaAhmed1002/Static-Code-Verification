# C++ Static Code Review Report

**Project:** Monster Battle Game  
**Source File:** game.cpp

| Line No. | Defect Type | Why Is It Important? | Suggested Correction | Severity |
|---|---|---|---|---|
| 41–42, 119 | Array Overflow | More monsters are added than the array can store, which may corrupt memory. | Check available capacity before inserting a monster. | Critical |
| 47 | Incorrect Comparison | The assignment operator changes the monster ID instead of comparing it with the requested ID. | Replace `=` with `==`. | High |
| 54–56 | Null Pointer and Arithmetic Error | A missing monster can cause a crash, and unsigned arithmetic makes the health check unreliable. | Check for `nullptr` and validate damage before subtraction. | Critical |
| 64–65 | Loop Boundary Error | The loop reads one element beyond the valid monster entries. | Change `i <= monsterCount` to `i < monsterCount`. | High |
| 70–73 | Dangling Reference | The function returns a reference to a local string that no longer exists after the function ends. | Return `std::string` by value. | High |
| 77–80 | Uninitialized Variable | The total attack value starts with an undefined value, and division by zero is possible. | Initialize `sum = 0.0` and handle an empty monster list. | High |
| 83–86 | Use After Deletion | The monster is deleted before its name is printed, and its pointer remains in the array. | Print the name first, then remove the monster safely from the collection. | Critical |
| 94–99 | Missing Return Value | Scores of 100 or below do not produce a defined return value. | Add a suitable default return statement. | High |
| 102–109 | Buffer and Memory Error | The boss name may exceed the buffer, and `delete` is used incorrectly for an allocated array. | Use `std::string` or safe bounded input, and use `delete[]` for arrays. | High |
| 121 | Memory Leak | The dynamically created bonus monster is never deleted. | Remove the unused allocation or manage it with a smart pointer. | Medium |
| 133 | Shallow Copy | Copying `Game` duplicates raw pointers, which can cause double deletion. | Implement safe copying or use smart pointers and suitable containers. | Critical |
| 91 | Arithmetic Precision | Integer division may discard fractional damage values. | Use `100.0` if fractional damage is intended. | Low |
| 31–33 | Object Initialization | The pointer array is not explicitly initialized, making safe state management harder. | Initialize pointer entries to `nullptr` and maintain valid array state. | Medium |
| 40–43 | Missing Validation | The spawning function does not check array capacity or validate monster attributes. | Validate capacity and input values before creating a monster. | High |

## Final Assessment

The review identified memory management errors, incorrect conditions, array boundary problems, and missing return paths. These defects should be addressed to improve program safety and correctness.

**Review Method:** Static inspection of the source code.
