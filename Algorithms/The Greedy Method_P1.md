# The Greedy Method
the greedy method is primarily an ***Optimization*** technique

### *General strategy：*
At every step:  
* select the ***best*** element from the ***remaining input***
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
In order to find the minimum faster, use data structure -- ***min-heap***
#### *strategy：*
At every step:
* create ***min-heap*** of the input
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
Input:  A weighted graph G: **W[1:n,1:n]**, where for non-edges(i,j): W[i,j] = infinity  
Output: A spanning tree **T** that has all the nodes of G and minimum weight
#### *strategy:*
At every step:
* select a min-weight edge e out of the remaining edges and delete e from the graph;
* if e does not create a cycle in T, then add e to T

>? how to do selection and deletion  
1 ***min-heap*** of weight  
2 ***sort*** the edges by weight   

>? how to do if check  
`If each nodes of an edge is in the same small tree, the edge makes the tree cycle`  
***Union-Find*** can find the root of each node, and also can combine two trees.

#### *time complexity:* `O(ElogE)`
```
Proc ComputesMST(in: W[1:n,1:n]; out: T)
begin
  int PARENT[1:n] = [-1,-1,...,-1];
  minheap H[1:E];                                   //O(E) to build the heap
  Put in T all the n nodes and no edges;
  while (T has less than n-1 edges) do:
    e = delete-min(H);        // assume e = (x,y)   // up to E calls to delete-min(): O(ElogE)
    r1 = F(x); r2 = F(y);     // Find()             // up to E calls to U and F: O(Elogn)
    if (r1 != r2) then:   
      U(r1, r2)               // Union()
    endif
  end while
end
```

### 5 The Single-Source The Shortest Path Problem
Input: A weight connected graph G: **W[1:n,1:n]**, where for non-edges(i,j): W[i,j] = infinity & A source node **s** of G  
Output: Shortest paths from source s to every other node in the graph: **Distance[1:n]**, where Distance[i] is s to i

#### *time complexity:* `O(n^2)`
```
Proc SSSP( in:W[1:n,1:n], s; out: DIST[1:n]);
begin
  for i =1 to n do: DIST[i] := W[s,i]; endfor
  // implement Y as Boolean array Y[1:n] : Y[i]= 1 if i ∈Y, 0 otherwise
  Boolean Y[1:n]; // initialized to 0
  Y[s] := 1; // add s to set Y
  for num =2 to n do
    Select a node u from out of Y (i.e., Y[u]==0) such that DIST[u] = min {DIST[i] | Y[i] = 0};
    Y[u] := 1; // Add u to Y
    // update the DIST values of the other nodes
    for all node v where Y[v] = 0 do
      DIST[v]= min (DIST[v], DIST[u]+W[u,v]);
    endfor
  endfor
end
```
