- The **minimax algorithm** performs a complete depth-first exploration of the game tree.
- If the maximum depth of the tree is m and there are b legal moves at each point, then the time complexity of the minimax algorithm is O(b^m ). 
- The space complexity is O(bm) for an algorithm that generates all actions at once, or O(m) for an algorithm that generates actions one at a time

> [!NOTE] MiniMax Algorithm
> Time Complexity : O(b^m)
> Space Complexity : O(bm)

![[Pasted image 20260218121550.png]]

Evaluation functions
Features
Expected value
A heuristic evaluation function E VAL(s, p) returns an estimate of the expected utility of state
s to player p, just as the heuristic functions of Chapter 3 return an estimate of the distance to
the goal. For terminal states, it must be that E VAL(s, p) = U TILITY(s, p) and for nonterminal
states, the evaluation must be somewhere between a loss and a win: U TILITY(loss, p) ≤
E VAL(s, p) ≤ U TILITY(win, p)
