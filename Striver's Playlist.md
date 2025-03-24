### Graphs
Graphs are Data Structures which are comprised of a one or more nodes connected by edges.
- **Un-Directed Graphs:** Graphs without Direction.
- **Directed Graphs:** Graphs with Direction.

*Paths* contains Nodes and are connected by Edges and a node can only exist once in a Path and the Nodes need to be connected to each other.

*Degree* of a Node is the number of edges that point towards that Node for an Undirected Graph

Total Degree of the Graph = $2 \times E$

For a Directed Graph:
- Indegree: Edges pointing towards the Node.
- Outdegree: Edges pointing away from the Node.

**Unit Weight**: 1

Representing a Graph:
- Un-Directed:
	- Adjacency Graph: $O(N^{2})$ Space Complexity
	- Adjacency List: $O(2E)$ Space Complexity
- Directed:
	- Non-Weighted:
		- Adjacency List: $O(N)$ Space Complexity
	- Weighted:
		- Store Weights along with Edges in Adjacency List
		- Store Weights instead of 1 in Adjacency Matrix
#### Connected Graphs:
> Whenever you are solving a Traversal Problem. Use visited node array.

### Traversal Algorithms:
--
*Breadth First Search* is a queue based Algorithm which traverses the Graph level by level.

**Time Complexity:** $O(N+E)$
**Space Complexity:** $O(N)$

```python
from collections import deque

def breadthFirstSearch(V, adj):
    vis = [0] * V
    vis[0] = 1
    q = deque([0])
    bfs = []

    while len(q) != 0:
        node = q.popleft()
        bfs.append(node)

        for i in adj[node]:
            if not (vis[i]):
                vis[i] = 1
                q.append(i)
    
    return bfs

if __name__ == "__main__":
    V = 5
    adj = [[1, 2], [0, 3, 4], [0, 3], [1, 2, 4], [1, 3]]
    print(breadthFirstSearch(V, adj))
```

*Depth First Search* is a stack-based Algorithm which traverses the Graph in Depth

***Time Complexity:** $O(N+E)$
**Space Complexity:** $O(N)$

```python
from typing import List

def depthFirstSearch(V: int, adj: List[int]):
    vis = [0] * V
    start = 0
    ls = []
    dfs(start, adj, vis, ls)
    return ls  

def dfs(node: int, adj: List[int], vis: List[int], d: List[int]):
    vis[node] = 1
    d.append(node)
    for i in adj[node]:
        if not vis[i]:
            dfs(i, adj, vis, d)

if __name__ == "__main__":
    V = 5
    adj = [[1], [2], [3], [4], []]
    print(depthFirstSearch(V, adj))
```

#### Detecting Cycles:
- Breadth First Search
```python
def detectCycle(src: int, adj: List[List[int]], vis: List[int]):
    vis[src] = -1
    q = deque()
    q.append((src, -1))

    while not q.count():
        node, parent = q.popleft()
        for i in adj[node]:
            if not vis[i]:
                vis[i] = 1
                q.append((i, node))
            elif parent != i:
                return True

        return False
```
- Depth First Search
```python
def cycleDFS(n, p, vis, adj):
    vis[n] = 1

    for i in adj[n]:
        if not vis[i]:
            if cycleDFS(i, n):
                return True
        elif i != p:
            return True
            
    return False
```
#### Union and Find
Two or more sets with nothing in common are called *Disjoint Sets.*
- Used to keep track of the *Set* and element belongs to. Given two elements we can find whether they belong to the same subset or not. (*Find*)
- Used to merge 2 Sets (*Union*)
- Code without Rank
	```python
	class UnionFind:
		def __init__(self, n):
			self.parent = list(range(n))
			self.size = [1] * n
		def find(self, x):
			if x != self.parent[x]:
				self.parent[x] = self.find(self.parent[x])
			return self.parent[x]
		def union(self, x, y);
			rx = self.find(x)
			ry = self.find(y)
			if rx != ry:
				self.parent[ry] = rx
	```
#### Bipartite Graph:
Color the Graph using Two Colors such that no two *Adjacent Nodes* have the same color.
- Linear Graphs with no Cycles are always Bi-Partite
- Even Graphs can be Bi-Partite
```python
from collections import deque

def bipartiteDetection(V: int, adj: List[List[int]]):
	q = deque()
	q.append(0)
	color = [-1] * V
	while q:
		node = q.popleft()
		for i in adj[node]:
			if color[i] == -1:
				color[i] = not color[node]
				q.append(i)
			elif color[i] == color[node]:
				return False
	return True 

```
#### Detect a Cycle in a Directed Graph
```python
	def detectCycleDirectedDFS(
	    i: int, adj: List[List[int]], vis: List[int], p_vis: List[int]
	) -> bool:
	    vis[i] = 1
	    p_vis[i] = 1
	
	    for j in adj[i]:
	        if not vis[j]:
	            if detectCycleDirectedDFS(i, adj, vis, p_vis) == True:
	                return True
	        elif p_vis[i]:
	            return True
	
	    p_vis[i] = 0
	    return False


def isCyclicDirectedDFS(V: int, adj: List[List[int]]):
    vis = [0] * V
    p_vis = [0] * V

    for i in range(len(adj)):
        if not vis[i]:
            if detectCycleDirectedDFS(i, adj, vis, p_vis) == True:
                return True

    return False
```

