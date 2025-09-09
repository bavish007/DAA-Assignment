# SETS — Weight Methods (Union by Size / Union by Rank)

##  Introduction
**Weight methods** are optimization techniques used in the **Disjoint Set Union (DSU)** or **Union–Find** data structure.  
They decide which tree becomes the parent when merging two sets, keeping the structure balanced and efficient.

Two main types:
- **Union by Size** → attach the smaller tree under the larger one.
- **Union by Rank** → attach the shallower tree under the deeper one.

These methods prevent tall, skewed trees and ensure operations are *almost constant time*.

---

##  Representation
Each element belongs to a set represented as a rooted tree.

- `parent[i]` → parent of node *i*  
- `size[i]` → number of nodes in tree (used in union by size)  
- `rank[i]` → height estimate of tree (used in union by rank)  

Initially, every element is its own parent (a singleton set).

---

##  Operations
1. **MakeSet(x)** → Create a new set with one element.  
2. **Find(x)** → Locate the representative (root) of the set containing *x*.  
   - Uses **path compression** for efficiency.  
3. **Union(a, b)** → Merge the sets containing *a* and *b* using size or rank rule.

---

## ⏱ Complexity
- **Find / Union (with weight methods + path compression):** Amortized `O(α(n))`  
  *(α = inverse Ackermann function, < 5 for all practical n)*  
- **Space:** `O(n)`  

Without weight methods, worst-case complexity could degrade to `O(n)`.

---

##  Applications
- **Kruskal’s Algorithm** (Minimum Spanning Tree)  
- Detecting **cycles in graphs**  
- **Connectivity** queries in networks  
- **Clustering / grouping problems**  
- **Merging accounts / dynamic equivalence problems**  

---

##  Example
Initial: 5 nodes → parent = [0,1,2,3,4], size = [1,1,1,1,1]  

1. `union(0,1)` → attach 1 under 0 → size[0]=2  
2. `union(2,3)` → attach 3 under 2 → size[2]=2  
3. `union(1,2)` → merge sets → final root is 0  

Final structure: all {0,1,2,3} connected under root 0.

---

