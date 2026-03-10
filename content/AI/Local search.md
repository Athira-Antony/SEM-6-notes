-  **Satisfaction** → “Is this acceptable?”
- **Optimisation** → “Which is the best?”

A **satisfaction problem** is one where we only need to find **any solution that satisfies all constraints**.
👉 We are **not looking for the best solution**, just a valid one.

An **optimisation problem** requires finding the **best solution** according to some cost or objective function.
👉 Many solutions may exist, but we want the **optimal one**.

example:  MST, travelling salesman etc

===Local search is designed to find the **best solution** by improving upon the current state — which is exactly what optimization is about.===

## Hill Climbing — Does it Jump to Random Neighbours?

```
Basic Hill Climbing → NO ❌
It does NOT jump to random neighbors

It always moves to the BEST neighbor
(deterministic, greedy)
```

---

### Basic Hill Climbing — Strictly Greedy

```
function HILL-CLIMBING(problem):

    current ← initial state

    loop:
        neighbor ← BEST among all neighbors
                    (lowest h / highest value)

        if neighbor is NOT better than current:
            STOP → return current   ← stuck here forever

        current ← neighbor
```
### Variants of Hill Climbing (Russell's)

**1. Simple Hill Climbing**

```
Move to FIRST neighbor that is better
than current state
→ Faster per step but less informed
```

**2. Steepest Ascent Hill Climbing**

```
Examine ALL neighbors
Move to the BEST one (highest value / lowest h)
→ More work per step but better decisions
→ This is what we described above for 8 Queens
```

**3. Sideways Move**

```
Allow moves to EQUAL value neighbors
→ Helps escape plateaus
→ Must limit sideways moves (e.g., max 100)
  otherwise infinite loop on flat regions

Russell's result with sideways moves:
Solves 94% of 8 Queens instances ✅
(up from 14%!)
```

**4. Random Restart Hill Climbing**

```
When stuck → start over with new random state
Keep best solution found across all restarts

For 8 Queens:
→ Each restart has ~14% success rate
→ Expected restarts needed = 1/0.14 ≈ 7
→ Finds solution quickly ✅

Russell: "Trivially complete" with random restarts
         because eventually random start = solution
```

**5. Stochastic Hill Climbing**

```
Don't always pick BEST neighbor
Choose randomly among UPHILL neighbors
→ weighted by how much better they are
→ Slower but explores more diverse paths
```

[[Simulated Annealing]]