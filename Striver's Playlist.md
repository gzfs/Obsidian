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

