[[Runtime allocation]]
[[Runtime Stack allocation]]

The declaration specifies that _factorial_ is a function that takes as input one integer argument and returns an integer. This is sometimes called the **signature** of the function. Conceptually, to invoke the factorial function, the **caller** must know:

1. The memory address to which the function call must be directed (**binding**).
2. The **types and names of the formal parameters** to the function and the order in which the actual **arguments** must be given as input to the function.
3. The **return type** of the function.

This precisely is the information that the symbol table stores.

> [!NOTE] A function **definition** contains:
> 
> a. The function's signature. 
> b. The declaration of **local variables** of the function. 
> c. The code of the function.

- If a global variable is re declared inside a function, _the local declaration overrides the global declaration_.
- The compiler needs to know the binding addresses and types of the local variables for translation of statements of the function to assembly code. However, this information is irrelevant outside the function.
- To keep track of the local variable and scope information, our strategy is to keep global and local variables in different symbol tables.
- A single **global symbol table** storing the _(name, type, size, binding)_ information of global variables as well as _(name, type, parameters, binding)_ information for functions.
- Several **local symbol tables** - one for each function containing the _(name, type, binding)_ information for each local variable of the function. (Note that since the language does not permit arrays to be defined within a function, the size value of local variables is always 1, hence the field is not required). 

### Task 2
For each function for which code is not yet generated
- a) Check for **name equivalence** of the formal parameters of the function definition with the declaration. Name equivalence requires that the type and name of each formal parameter of the function in the declaration and the definition must agree.
- b) Create local symbol table containing local variables and parameters.
- c) Build AST for the function. (Do type-checking when the tree is being built, as was done in the previous stages.)
- d) Recursively traverse the tree and generate code for the function in the target file.

**After generating code for a function, the local symbol table and the abstract syntax tree for the function can be deallocated.**

**To generate code for calling one function from another function, only the global symbol table information of the callee is needed. The global symbol table is maintained throughout the compilation process.**

![[Pasted image 20260303192559.png]]

```
Note that a variable appearing in a function must first be searched for in the local symbol table of the function and then in the global symbol table, if not found in the local symbol table.
```

- 1. Each **activation record must have a base (memory location)** which is determined at run time. The machine register **BP (base pointer)** is generally used to point to the base of the activation record of the function executing currently.
- 2. **Relative to the base, the address of each argument, each local variable, the address where the return value is stored etc are fixed by the compiler statically** (at compile time).
- 3. Initially, the activation record for the main function is created in the stack. BP is initialized to the base of this activation record and the main function starts execution.
- 4. **If function A calls function B, a new activation record is created in the stack for function B above the activation record of function A**. The BP is made to point to the base of activation record of B. Upon return from B, the activation record of B is popped off the stack and BP is set back to the activation record of A.
- 5. If function A calls function B, the address of the instruction in A to resume execution (**return address** – value of current-IP +2 in XSM machine- why?) upon return from B must be saved. Similarly, the **base pointer of the caller** (BP value) of A **must be saved in the stack** before BP is changed to point to the base of B. Both the return address and BP values will be stored in pre-defined locations of the activation record of B.
- 6. In addition to the above, one additional **space** must be reserved in the activation record of B **to store the return value**.


- 1.**Save the BP of the caller** by pushing the BP register into the stack.
- 2.**Set BP** to the present value of SP register.
- 3. Push enough space in the stack for storing the local variables.

Relative to the BP value set in step 2 above, [BP-2] is the address to which the return value must be stored. [BP-3] stores arg_1, [BP-4] stores arg_2 and so on. [BP+1] is for loc_1, [BP+2] for loc_2 and so on. Thus, after seeing the local variable declarations, the compiler can set the binding values for local variables relative to the base of activation record (BP) value as:

![[Pasted image 20260303193534.png]]

Finally, the code for a return statement must:

1. **Pop out the local variables** from the stack.
2. Calculate the return expression and store the value in [BP-2].
3. **set BP to the old value** of BP in the stack.
4. **Execute the RET instruction** to pass control back to the caller.