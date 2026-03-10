- When you run encryption on a device (like a smart card or IoT sensor), an attacker can measure the device's power consumption and figure out the secret key — this is called a **side-channel attack**


- ### The S-Box
Every block cipher (encryption algorithm) uses an **S-Box** — a lookup table that scrambles bits in a nonlinear way. Think of it as a substitution cipher at the bit level. For it to be secure, it must be:

- **Bijective** (one-to-one mapping, reversible)
- **High nonlinearity** (hard to approximate with simple math)
- **Low differential uniformity** (small changes in input don't predictably change output)

A 4×4 S-Box that hits all three goals optimally is called **cryptographically optimal**.

**Threshold Implementation (TI)**
it has three rules:

1. **Uniformity** — shares look random
2. **Non-completeness** — each sub-function is missing at least one share (so glitches can't leak everything)
3. **Correctness** — combining shares gives the right answer

> [!NOTE] **The Core Idea: S-Boxes from Cellular Automata (CA)**
> Instead of designing a complex S-Box directly, use a **simple 4-input, 1-output local rule** (called a CA rule) and apply it **four times** with cyclically shifted inputs:
> S(X,Y,Z,W) = ( f(X,Y,Z,W), f(Y,Z,W,X), f(Z,W,X,Y), f(W,X,Y,Z) )




