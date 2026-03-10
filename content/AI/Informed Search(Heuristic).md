
The hints come in the form of a heuristic function, denoted `h(n)`

```
h(n) = estimated cost of the cheapest path from the state at node n to a goal state.
```

## Greedy best first search

Greedy Best-First Search is not optimal because it ignores path cost and considers only heuristic value, and it is not complete because it may follow an infinite promising path without exploring other possible solution

> [!NOTE] head
> [^1]Why Greedy Best-First Search is **NOT optimal**
> It considers only **how close the goal appears**, not the actual cost to reach it.
> So it may choose a path that looks closer but is actually expensive.

![[Pasted image 20260219081313.png]]

	   Start
       /     \
      A(h=2)  B(h=10)
      |
      C(h=5)   ← dead end, no path to goal
      B → Goal ✅
      
**Greedy picks A first** (lower h=2), goes to C, hits a dead end. It misled by the heuristic. BFS would have found B → Goal correctly.
This shows Greedy is **not complete** — a bad heuristic can lead it into traps.

Costs:
- Start → A → Goal = 50
- Start → B → Goal = 10
If heuristic says A is closer to goal, GBFS chooses A and returns cost 50.
But a cheaper solution exists.
✅ Therefore, not optimal



> [!NOTE] Question
> Why Greedy Best-First Search is **NOT complete**

> [!NOTE] Answer 
> Reason 1: Infinite paths
> If the search space is infinite, GBFS may keep following a path that looks promising forever and never explore other branches.
> Reason 2: Can get stuck in loops
> If repeated states are not checked, it may revisit nodes endlessly.



| Property | Greedy Best First Search |
| -------- | ------------------------ |
| Uses     | Only h(n)                |
| Complete | No                       |
|          |                          |
|          |                          |
|          |                          |

## A* Search  (If want both speed + optimality)

> [!NOTE] Theorem: 
> If h(n) is admissible, A* using TREE-SEARCH is optimal


> [!NOTE] Theorem
>If h(n) is consistent, A* using GRAPH-SEARCH is optimal
>
> Why Graph Search Needs Consistency (Not Just Admissibility)
> In **Graph Search**, once a node is expanded it goes into the **closed list** and is **never expanded again**.

```
Graph Search:
- Open List  → nodes waiting to be expanded
- Closed List → nodes already expanded (NEVER revisited)
```

A* might reach node N via an expensive path first
→ N gets added to closed list
→ Later a cheaper path to N is found
→ But N is already closed → ignored!
→ Optimal path might be missed ❌

**When h(n) is consistent, f(n) values are non-decreasing along any path.**
**Proof:**
```
f(n') = g(n') + h(n')
      = g(n) + cost(n→n') + h(n')

Since h is consistent:
h(n) ≤ cost(n→n') + h(n')
→ cost(n→n') + h(n') ≥ h(n)

Therefore:
f(n') = g(n) + cost(n→n') + h(n')
      ≥ g(n) + h(n)
      = f(n)

So:  f(n') ≥ f(n)  ✅
```


> [!NOTE] Theorem
> Every consistent heuristic is also admissible.

```
Proof: Consistency → Admissibility
Optimal path: n → n1 → n2 → ... → nk → G

h(n)  ≤  c1 + h(n1)                         [consistency at n]
      ≤  c1 + c2 + h(n2)                     [consistency at n1]
      ≤  c1 + c2 + c3 + h(n3)               [consistency at n2]
      ≤  ...
      ≤  c1 + c2 + ... + ck + h(nk)         [consistency at n(k-1)]
      ≤  c1 + c2 + ... + ck + ck+1 + h(G)  [consistency at nk]
      =  c1 + c2 + ... + ck + ck+1 + 0     [h(G) = 0]
      =  h*(n)                               [definition of h*]

∴  h(n) ≤ h*(n)   →   h is ADMISSIBLE  ✅
```


- ###### The optimal cost of a relaxed problem is admissible heuristic for the original problem 
- because ->Admissible heuristic condition:
		h(n)≤h*(n)
		Since:    hr(n)≤h*(n)
the relaxed problem cost **never overestimates** the true cost.Therefore,
✅ optimal solution cost of relaxed problem is an admissible heuristic.

- Admissible heuristics can also be derived from the solution cost of a **subproblem** of a given problem.

## IDA*
IDA* → increases f-cost threshold each iteration 
Each iteration = DFS but only explore nodes where f(n) ≤ threshold
#### ==The Algorithm==
```
1. Set initial threshold = f(Start) = g(Start) + h(Start)
                                     = 0 + h(Start)
                                     = h(Start)

2. Do DFS, but PRUNE any node where f(n) > threshold

3. If goal found → STOP ✅

4. If goal not found:
   → new threshold = minimum f value that was pruned
   → Repeat from step 2 with new threshold

5. Keep repeating until goal is found
```

---
### IDA* vs A* vs IDS

| Property            | IDS       | A*              | IDA*                 |
| ------------------- | --------- | --------------- | -------------------- |
| **Uses heuristic?** | ❌ No      | ✅ Yes           | ✅ Yes                |
| **Memory**          | O(bd) low | O(b^d) high     | O(bd) low            |
| **Complete?**       | ✅ Yes     | ✅ Yes           | ✅ Yes                |
| **Optimal?**        | ✅ Yes     | ✅ Yes           | ✅ Yes (admissible h) |
| **Limit type**      | Depth     | f-cost (memory) | f-cost threshold     |
| **Redundant work?** | ✅ Yes     | ❌ No            | ✅ Yes                |

---

```
Problem                          Why IDA*?
──────────────────────────────────────────
15-puzzle, 24-puzzle             A* runs out of memory
                                 IDA* handles it easily

Large game trees                 Memory is the bottleneck

Embedded/low-memory systems      Can't afford A*'s memory

When branching factor is large   A* open list explodes
```

---

### Simple Analogy

```
A*    → Smart GPS that remembers every road explored
        Fast but needs a big notepad

IDS   → Explorer who goes deeper each time
        Low memory but no sense of direction

IDA*  → Smart explorer who uses intuition (heuristic)
        to decide which paths are worth exploring,
        resets each iteration but never wastes time
        on clearly expensive paths
        
        Best balance of smarts + low memory ✅
```

---

[[Depth First Search bound and branch]]




