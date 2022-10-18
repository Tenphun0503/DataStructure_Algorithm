# Dynamic Programming
Dynamic Programming is a technique that can systematically and efficiently explore all possible solutions to a problem.

### *General strategy:*

### *Difference from others:*
- Greedy have optimal substructure, but not overlapping sub-problems
- DC problems have sub-problems but they are not overlapping


---

## Applications
### 1.1 Fibonacci sequence
#### *strategy: *
Analyze the problem: 
* If you want to find F(n), you can break it down into smaller ***sub-problems***: find F(n-1), F(n-2)
* Adding the solutions to these sub-problems gives the answer, which means the problem has ***optimal sub-structure***
* Sub-problems are also ***overlapping*** - for example, F(4) is needed to calculate F(5) and F(6)
```
// Pseudocode example for bottom-up

F = array of length (n + 1)
F[0] = 0
F[1] = 1
for i from 2 to n:
    F[i] = F[i - 1] + F[i - 2]
```
```
Pseudocode example for bottom-up
memo = hashmap
Function F(integer i):
    if i is 0 or 1: 
        return i
    if i doesn't exist in memo:
        memo[i] = F(i - 1) + F(i - 2)
    return memo[i]
```