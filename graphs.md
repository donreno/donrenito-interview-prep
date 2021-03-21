# Graphs
Graphs might fall as a category of n-ary tree, but it has different charasteritics that makes it a struct of it's own.

## Kinds of graphs
Graphs can be directed (1 direction) or undirected (2 directions), and among these directions might also be weighted representing the cost of traversing from one Graph node to the other.

## How to represent a Graph
Graph can be represented in many ways here we are going to list couple of them.

### Adjacency list
It's a list which represents all graph nodes and the nodes it "points" to.
e.g:

```go
adjacencyList := [][]int {
    {1},
    {2},
    {0,3},
    {2}
}
```

### Adjacency matrix
Similar to adjacency matrix but it looks more like a table of node's edges and their weights

|     |  0  |  1  |  2  |  3  |
| --- | --- | --- | --- | --- | 
|**0**|  0  |  1  |  0  |  2  |
|**1**|  1  |  0  |  0  |  0  |
|**2**|  0  |  0  |  0  |  1  |
|**3**|  0  |  0  |  3  |  0  |

### Graph struct
As a graph struct with a collection of pointers or edges representing node edges

```go
// Graph Graph data struct
type Graph struct {
	nodeLookup map[int]*GraphNode
}

// GraphNode a Graph node
type GraphNode struct {
	ID     int
	Value  int
	Childs []*GraphNode
}
```

## Graph Search or traversal
There are two very well known ways to traverse or find a path to a node on a Graph.

### DFS (Depth First Search)
Depth first search will traverse trough the depth of a single edge and it's following paths and then it will come back and traverse next edge, regularly in order to not pass by the same node again you can memoize visited nodes.

Code implementation:

```go
func (g *Graph) HasPathDFS(source, destination int) bool {
	srcNode := g.nodeLookup[source]
	destNode := g.nodeLookup[destination]
	return g.hasPathDFS(srcNode, destNode, make(map[int]bool))
}

func (g *Graph) hasPathDFS(source, destination *GraphNode, visited map[int]bool) bool {
	if visited[source.ID] {
		return false
	}

	if source.ID == destination.ID {
		return true
	}

	visited[source.ID] = true

	for _, child := range source.Childs {
		if g.hasPathDFS(child, destination, visited) {
			return true
		}
	}

	return false
}
```

### BFS (Breadth First Search)
Breadth first search will traverse trough every adjacent node before going in depth like DFS, it will ensure to traverse all neighbors or adjacent nodes level by level.

```go
func (g *Graph) HasPathBFS(source, destination int) bool {
	srcNode := g.nodeLookup[source]
	destNode := g.nodeLookup[destination]
	nextToVisit := []*GraphNode{srcNode}
	visited := make(map[int]bool)

	var current *GraphNode

	for len(nextToVisit) > 0 {
		current, nextToVisit = nextToVisit[0], nextToVisit[1:]

		if current.ID == destNode.ID {
			return true
		}

		if visited[current.ID] {
			continue
		}

		visited[current.ID] = true

		for _, child := range current.Childs {
			nextToVisit = append(nextToVisit, child)
		}
	}

	return false
}
```