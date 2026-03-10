## BFS is *NOT optimal when*

👉 **Step costs are different**.

Example:

> [!NOTE]
> `Start → A → Goal   (cost = 10 + 10 = 20) 
> Start → B → C → Goal (cost = 1 + 1 + 1 = 3)`
> 

BFS chooses the first path because it has fewer steps (depth 2),  
but the second path is cheaper.

So BFS fails.

### What to use then?

When costs are different:

👉 Use **Uniform Cost Search (UCS)**

Because UCS expands the node with **lowest total path cost**, not lowest depth.

### DFS is incomplete
because it may get stuck exploring an infinite or very deep branch and fail to explore other branches where a solution exists.

---
![[Pasted image 20260211172600.png]]

| Property | DLS | IDS |
| -------- | --- | --- |

| Strategy | DFS with limit | Repeated DLS |
| -------- | -------------- | ------------ |

| Complete | No  | Yes |
| -------- | --- | --- |

| Optimal | No  | Yes (equal cost) |
| ------- | --- | ---------------- |

| Time | O(b^L) | O(b^d) |
| ---- | ------ | ------ |

| Space | O(bL) | O(bd) |
| ----- | ----- | ----- |

| Memory usage | Low | Low |
| ------------ | --- | --- |
[[Informed Search(Heuristic)]]

