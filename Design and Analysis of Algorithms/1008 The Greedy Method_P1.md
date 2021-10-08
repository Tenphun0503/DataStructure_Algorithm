# The Greedy Method
the greedy method is primarily an ***Optimization*** technique

### *General strategy：*
At every step:  
* selcet the ***best*** element from the ***remaining input***
* delete it from the input, and put it in the output

---

## Applications 
### 1.1. Greedy Sort 1
#### *strategy：*
At every step:  
* select the ***minimum*** from the ***remaining input***
* delete it from the input, and put it in the output  
> Then the algorithm becomes ***Selection Sort***
#### *time complexity：* `O(n^2)`

### 1.2. Greedy Sort 2
In order to find the minimun faster, use data structure -- ***min-heap***
#### *strategy：*
At every step:
* creat ***min-heap*** of the input
* do ***delete_min()*** (This func does both the selection and deletion)
#### *time complexity：* `O(nlogn)`

```
Proc GreedySort(in : A[1:n]; out : B[1:n])
begin
  H = create_heap(A[1:n]); k=1;   // there are two ways to build a min-heap. Insertion takes O(nlogn). Recursion takes O(n).
  while (k < n) do:               // while loop takes O(nlogn)
    x = delete_min(H);            // delete_min() takes O(logn)
    B[k] = x; k++;
   endwhile
end
```

> ***Min-heap*** and its creation method: ***Insertion*** & ***Recursion***

### 2 Optimal Merge Patterns
Input:    n **sorted** arrays A1[1:L1], A2[1:L2], ..., An[1:Ln]  
Output:   The whole input combined into a **single sorted** array
#### *strategy:*
At every step:
* select and remove the two ***shortest*** array from the all (why shortest: b/c every merge(Ai,Aj) takes length(Ai) + length(Aj) 
* do ***merge(Ax, Ay)*** and put the combined one into all
#### *time complexity:* `O(n)`

```
Proc OptimalMerge(in : A1[1:L1], A2[1:L2], ..., An[1:Ln]; out : B[1:L]
begin
  H = create_heap(length(A1):length(An)); k=1;  // it takes O(n)
  while (k < n) do:                             
    x = delete_min(H); y = delete_min(H);       // each delete_min() takes O(logn)
    B = merge(Ax, Ay);                          // merge() takes O(n)
    insert(H, x + y); k++;                      // insert() takes O(logn)
  endwhile
end
```

### 3 The Knapsack Problem
Input:    Capacity, Items, Weights, Prices  
Output:   Take item of total weights is <= C, and the total price is maximized (item can be taken portion of it)
#### *strategy:*
At every step:
* select the item which has ***max(Pi/Wi)***  
* if item fits the ***c*** (remain capacity of C), take all; otherwise, take ***c/Wi*** of the item  
`why compute xi = c/Wi? -> total price then: x1P1 + x2P2 +,,,+ xnPn`

### 4 The Minimum Spanning Tree Problem
### 5 The Single-Source Shortest Path Problem
