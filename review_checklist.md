# Static Code Verification Checklist

**Project:** Monster Battle Game  
**Source File:** game.cpp

| Category | Result (Issues / OK) | Defect Found | Static Verification |
|---|---|---|---|
| Initialization | Issues | The variable `sum` is used without an initial value. | Initialize `sum` to 0 before adding attack values. |
| Pointers | Issues | Some functions may use a null pointer or access an object after deletion. | Check pointers before use and avoid accessing deleted objects. |
| Arrays / Buffers | Issues | The monster array can exceed its capacity, and the boss name buffer has no safe input limit. | Check array capacity and use `std::string` for names. |
| Loops | Issues | The total health loop uses an incorrect boundary condition. | Use `i < monsterCount` to access only valid entries. |
| Arithmetic | Issues | Damage calculations use unsafe unsigned arithmetic, and average attack may divide by zero. | Validate damage values and check the monster count before division. |
| Control Flow | Issues | The `playerRank()` function does not return a value for every score. | Add a default return value for the remaining cases. |
| Function Call | Issues | Functions do not properly handle missing monster IDs, and an allocated array is released incorrectly. | Validate function inputs and use the correct memory deallocation method. |
| Classes | Issues | The `Game` class copies raw pointers, which can cause the same objects to be deleted twice. | Use safe copy operations or smart pointers to manage ownership. |

