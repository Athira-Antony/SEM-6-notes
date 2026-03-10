-  Search tree with branches
- Branch policy: take lowest cost edge first
- DFBnB prunes nodes **only after** a good bound is known. 
- Before finding the optimal solution:  it may expand nodes that are not part of the optimal path.

> [!NOTE] Note :
> If h2(n) ≥ h1(n) for all n (both admissible) then h2 dominates h1
• h2 is better for search
### The Algorithm

```
function DFS_BranchAndBound(start, goal):

    best_cost = ∞
    best_path = null

    call DFS(start, 0, [start])

    return best_path, best_cost


function DFS(node, current_cost, current_path):

    ── STEP 1: PRUNING CHECK ──────────────────────
    if current_cost ≥ best_cost:
        return   ← PRUNE, no point going further ❌

    ── STEP 2: GOAL CHECK ────────────────────────
    if node == goal:
        if current_cost < best_cost:
            best_cost = current_cost      ← update best
            best_path = current_path      ← save path
        return

    ── STEP 3: EXPAND NODE ───────────────────────
    for each neighbor of node:
        if neighbor not in current_path:    ← avoid cycles

            new_cost = current_cost + cost(node → neighbor)

            ── STEP 4: BOUND CHECK BEFORE DIVING ──
            if new_cost < best_cost:        ← only explore
                                              if promising
                DFS(neighbor,
                    new_cost,
                    current_path + [neighbor])
```


> [!NOTE] Linear Conflict heuristic
> h(n) = Manhattan Distance + 2 × (number of linear conflicts)
### Why Linear Conflict is Better

```
Manhattan Distance:  ignores tile interactions → underestimates more
Linear Conflict:     accounts for blocking    → closer to true cost

Both are still ADMISSIBLE ✅
(never overestimate — 2 extra moves is the MINIMUM needed)

Linear Conflict dominates Manhattan Distance:
h_LC(n) ≥ h_MD(n) always

Better heuristic → A*/IDA* expands fewer nodes → faster!
```
---
## Pattern Database Heuristics

Instead of calculating heuristic on the fly mathematically, **precompute and store exact costs** for sub problems in a lookup table (database).

```
Divide tiles into GROUPS (patterns)
Precompute exact cost to solve each group
Store in a database
During search → just LOOK UP the cost
```

### Why Pattern Databases are Powerful

```
Manhattan Distance:
  Considers each tile independently
  Ignores ALL interactions
  Weak heuristic → many node expansions

Pattern Database:
  Precomputes EXACT cost for a group of tiles
  Captures ALL interactions within the group
  Very strong heuristic → far fewer expansions
```

[[Simulated Annealing]]