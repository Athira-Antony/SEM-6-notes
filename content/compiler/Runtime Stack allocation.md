when an ExpL function is invoked, space has to be allocated for storing
- the arguments to the function,
- return value of the function,
- local variables declared in the function.

Each activation record has a base, and the **base pointer (BP)** is a machine register that points to the base of the activation record of the currently executing function. When one function invokes another, the base pointer value of the caller is pushed on to the stack and BP is set to point to the new activation record base. Upon return, the activation record is popped off the stack and old value of base pointer is restored. The **stack pointer (SP)** must always point to the top of the stack.

Function A calls another function B.
1. A pushes its machine state (registers in use) into the stack so that the registers are free for use in B.
2. A pushes the arguments to B in the order they appear in the declaration.
3. A pushes one empty space in the stack for B to place its return value.
4. A invokes B. (This results in generation of a CALL instruction which results in pushing the instruction pointer into the stack and transfer of control to B).

Inside B, the following space allocations take place:

5. B saves the BP value of A to the stack and sets BP to the top of the stack.
6. B allocates space for local variables (in the order in which they appear in the declaration).

When B completes execution the following sequence of actions take place:

1. B computes the return value and stores it in the space allocated for it in the stack.
2. B pops out the local variables.
3. The old BP value is popped off and saved into BP.
4. B returns (this results in generation of a RET instruction which results in setting the instruction pointer to the value saved in the stack).

On re-entry, A does the following:

5. Retrieve the return value from stack and save it to a new register. This is the result of the function call.
6. Pop off the arguments.
7. Restore the saved register context.