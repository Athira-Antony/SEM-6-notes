### Simulated Annealing's Solution

```
"What if we SOMETIMES allow moving to a WORSE state?"
→ This lets us escape local maxima
→ Cross the valley → reach global peak

BUT we can't always accept worse moves
→ That would just be random wandering

Solution: Accept worse moves LESS and LESS
          over time (as "temperature" decreases)
```

Temperature = how willing we are to accept bad moves

HIGH temperature (early on):
→ Accept bad moves OFTEN
→ Explore widely, escape local traps
→ Like hot metal — atoms moving freely

LOW temperature (later):
→ Accept bad moves RARELY
→ Settle into good solutions
→ Like cooling metal — atoms stabilizing

Temperature = 0:
→ NEVER accept bad moves
→ Behaves exactly like Hill Climbing

### The Algorithm

```
function SIMULATED-ANNEALING(problem):

    current ← random initial state
    T ← initial high temperature

    loop:
        T ← COOLING(T)          ← reduce temperature

        if T = 0: return current ← done cooling, stop

        next ← RANDOM neighbor of current (any neighbor)
        ΔE  ← value(next) - value(current)

        if ΔE > 0:              ← next is BETTER
            current ← next      ← always accept ✅

        else:                   ← next is WORSE
            accept with probability e^(ΔE/T)
            → sometimes accept, sometimes reject
```

> [!NOTE] Common cooling schedule:
>  T(t+1) = α × T(t) where α = 0.95 or 0.99

## Local beam search

• Idea: Keeping only one node in memory is an extreme reaction to memory problems.
• Keep track of k states instead of one
	Initially: k randomly selected states
	Next: determine all successors of k states
	If any of successors is goal -> finished
	Else select k best from successors and repeat

## Genetic Algorithms

Individual  = one candidate solution
Population  = set of all current solutions
Chromosome  = encoded representation of a solution
Gene        = single element of a chromosome
Fitness     = how good a solution is
Generation  = one round of evolution
### Visual Overview
```
Initial Population (random)
        ↓
┌───────────────────────────┐
│  Evaluate FITNESS         │
│  of each individual       │
└───────────────────────────┘
        ↓
┌───────────────────────────┐
│  SELECTION                │
│  Pick best individuals    │
└───────────────────────────┘
        ↓
┌───────────────────────────┐
│  CROSSOVER                │
│  Combine pairs → children │
└───────────────────────────┘
        ↓
┌───────────────────────────┐
│  MUTATION                 │
│  Randomly alter genes     │
└───────────────────────────┘
        ↓
New Population
        ↓
Repeat until SOLUTION FOUND ✅
```


![[Pasted image 20260219114556.png]]

> [!NOTE] Simulated annealing with T = 0
>  at all times: ignoring the fact that the termination step  would be triggered immediately, the search would be identical to first-choice hill climbing because every downward successor would be rejected with probability 1. 

> [!NOTE] Simulated annealing with T = ∞
>   at all times is a random-walk search: it always accepts a new state.

