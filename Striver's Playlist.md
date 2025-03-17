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



