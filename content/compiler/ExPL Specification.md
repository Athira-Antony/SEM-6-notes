##### Type Definitions[](https://silcnitc.github.io/expl-docs/expl/#type-definitions "Permanent link")
All user-defined types in a program must be defined in the type definition section. The Type Definition section starts with the keyword **type** and ends with the keyword **endtype.**

-  Array type variables can be declared only globally.
- Variables **cannot be assigned values during the declaration phase.**
- **Arrays cannot be passed as arguments.**

#### Function Definitions and the Main Function[¶](https://silcnitc.github.io/expl-docs/expl/#function-definitions-and-the-main-function "Permanent link")

All globally declared variables are visible inside a function, unless suppressed by a re-declaration within the function. Variables declared inside a function are invisible outside

- Intialize() must be invoked before any allocation is made and it resets the heap to default values. 
- A call to alloc() allocates contiguous memory locations in the **heap memory** (memory reserved for dynamic memory allocation) and returns the address of the starting location.
- A call to free() deallocates contiguous memory locations in the heap memory that is referenced by the user defined type variable. The function free() returns NULL on successful deallocation
