# Graphs

Graphs are mathematical structures used to model pairwise relationships between objects. They consist of vertices (nodes) and edges (connections). Graphs are versatile structures with diverse types (directed, weighted, bipartite, trees, DAGs) and properties (degree, connectivity, cycles, coloring). They are fundamental in Computer Science, Mathematics, and Network Theory.

## Definition
A graph \( G \) is formally defined as:
\[ G = (V, E) \]
- **V**: Set of vertices (nodes)  
- **E**: Set of edges (pairs of vertices)

Edges may be directed (ordered pair) or undirected (unordered pair).

## Types of Graphs

1. Based on Direction
- Undirected Graph: Edges have no direction; relationship is bidirectional.  
- Directed Graph (Digraph): Edges have direction, represented as ordered pairs.

2. Based on Weights
- Unweighted Graph: All edges are equal.  
- Weighted Graph: Each edge has an associated cost, distance, or weight.

3. Based on Connectivity
- Connected Graph: Every vertex is reachable from any other.  
- Disconnected Graph: At least one vertex is isolated.  
- Strongly Connected (for digraphs): Every vertex is reachable from every other via directed paths.  
- Weakly Connected: Connectivity exists if edge directions are ignored.

4. Based on Cycles
- Acyclic Graph: Contains no cycles.  
- Cyclic Graph: Contains at least one cycle.  
- Directed Acyclic Graph (DAG): Directed graph with no cycles, widely used in scheduling and dependency resolution.

5. Special Graphs
- Complete Graph: Every pair of vertices is connected.  
- Bipartite Graph: Vertices can be divided into two disjoint sets with edges only across sets.  
- Tree: A connected acyclic graph.  
- Forest: A collection of disjoint trees.  
- Planar Graph: Can be drawn on a plane without edge crossings.  
- Multigraph: Allows multiple edges between the same vertices.  
- Regular Graph: All vertices have the same degree.  
- Null Graph: Contains vertices but no edges.

---

## Properties of Graphs

1. Degree of a Vertex
   - Number of edges incident to a vertex.  
   - In directed graphs: **in-degree** (incoming edges), **out-degree** (outgoing edges).

2. Path and Cycle
   - **Path**: Sequence of vertices connected by edges.  
   - **Cycle**: Path that starts and ends at the same vertex without repeating edges.

3. Connectivity
   - Minimum number of vertices/edges that must be removed to disconnect the graph.  
   - **Cut-vertex** and **cut-edge** are critical points of failure.

4. Subgraph
   - A graph formed from a subset of vertices and edges of another graph.

5. Isomorphism
   - Two graphs are isomorphic if they have identical structure, differing only in labeling.

6. Adjacency
   - Two vertices are adjacent if connected by an edge.  
   - Represented using **adjacency matrix** or **adjacency list**.

7. Graph Coloring
   - Assignment of colors to vertices such that no two adjacent vertices share the same color.  
   - Used in scheduling, register allocation, and map coloring.

8. Planarity
   - A graph is planar if it can be drawn without edge crossings.  
   - Kuratowski’s theorem characterizes non-planar graphs.

## Applications
- **Computer Networks**: Routers and connections modeled as graphs.  
- **Social Networks**: Users as vertices, friendships as edges.  
- **Pathfinding**: GPS navigation using shortest path algorithms (Dijkstra, A*).  
- **Dependency Resolution**: DAGs in compilers and task scheduling.  
- **Biology**: Protein interaction networks.  

* Simple Graph: A graph is simple if and only if it has no self-loops (edges where both​ the vertices are same) or multi-edges (repetitive pairs of edges).

* Bipartite Graph: A bipartite graph is a graph where it is possible to color each vertex black or white satisfying the following condition: 
    * For every edge, the two vertices connected by that edge have different colors.