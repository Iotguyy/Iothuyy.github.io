---
title: Dijkster
date: 2022-05-21 12:00:00 -500
categories: [algorithms,computer science,Pathfinding]
tags: [algorithms,computer science,pathfinding ,graphs]     # TAG names should always be lowercase
---

# Whats Dijkstra's algorithm

Dijkstra's algorithm is an algorithm for finding the shortest paths between nodes in a weighted graph, which may represent, for example, road networks. It was conceived by computer scientist Edsger W. Dijkstra in 1956 and published three years later.

## A Brief Introduction to Graphs
Graphs are non-linear data structures representing the "connections" between the elements. These elements are known as the Vertices, and the lines or arcs that connect any two vertices in the graph are known as the Edges. More formally, a Graph comprises a set of Vertices (V) and a set of Edges (E). The Graph is denoted by G(V, E).


### Components of a Graph
- Vertices:Vertices are the basic units of the graph used to represent real-life objects, persons, or entities. Sometimes, vertices are also known as Nodes.
- Edges:Edges are drawn or used to connect two vertices of the graph. Sometimes, edges are also known as Arcs.


![sample](https://static.javatpoint.com/tutorial/daa/images/dijkstras-algorithm.png)

---



## Understanding the Working of Dijkstra's Algorithm



#### A graph and source vertex are requirements for Dijkstra's Algorithm. This Algorithm is established on Greedy Approach and thus finds the locally optimal choice (local minima in this case) at each step of the Algorithm.

Each Vertex in this Algorithm will have two properties defined for it:

* Visited Property
* Path Property   

1. Visited Property:
The 'visited' property signifies whether or not the node has been visited.


2. Path Property:
The 'path' property stores the value of the current minimum path to the node.
The current minimum path implies the shortest way we have reached this node till now.



![example](https://static.javatpoint.com/tutorial/daa/images/dijkstras-algorithm6.png)


## In the given graph
1. **Input Graph and Source Node:** Use graph with node A as source.
2. **Mark Nodes Unvisited:** Initially, mark all nodes unvisited.
3. **Set Path Values:** Set path to 0 for node A, INFINITY for others.
4. **Mark Source Node Visited:** Mark A as visited, access neighbors.
5. **Update Path to Node B:** Update path to B to 4.
6. **Update Path to Node C:** Update path to C to 5.
7. **Visit Node B:** Visit B, perform relaxation on unvisited neighbors.
8. **Relaxation at Node E:** Relax path values at E, path to F becomes 14.
9. **Visit Node D:** Visit D, relax path to F remains 14.
10. **Visit Node F:** Visit F without relaxation.
11. **Conclusion:** Program ends when all nodes visited.


## Code Implementation



```javascript
// Define a graph using an adjacency list
const graph = {
    A: { B: 1, C: 4 },      // Node A is connected to Node B with a weight of 1 and Node C with a weight of 4
    B: { A: 1, C: 2, D: 5 },  // ... and so on for other nodes
    C: { A: 4, B: 2, D: 1 },
    D: { B: 5, C: 1 }
};

function dijkstra(graph, start) {
    // Create an object to store the shortest distance from the start node to every other node
    let distances = {};

    // A set to keep track of all visited nodes
    let visited = new Set();

    // Get all the nodes of the graph
    let nodes = Object.keys(graph);

    // Initially, set the shortest distance to every node as Infinity
    for (let node of nodes) {
        distances[node] = Infinity;
    }
    
    // The distance from the start node to itself is 0
    distances[start] = 0;

    // Loop until all nodes are visited
    while (nodes.length) {
        // Sort nodes by distance and pick the closest unvisited node
        nodes.sort((a, b) => distances[a] - distances[b]);
        let closestNode = nodes.shift();

        // If the shortest distance to the closest node is still Infinity, then remaining nodes are unreachable and we can break
        if (distances[closestNode] === Infinity) break;

        // Mark the chosen node as visited
        visited.add(closestNode);

        // For each neighboring node of the current node
        for (let neighbor in graph[closestNode]) {
            // If the neighbor hasn't been visited yet
            if (!visited.has(neighbor)) {
                // Calculate tentative distance to the neighboring node
                let newDistance = distances[closestNode] + graph[closestNode][neighbor];
                
                // If the newly calculated distance is shorter than the previously known distance to this neighbor
                if (newDistance < distances[neighbor]) {
                    // Update the shortest distance to this neighbor
                    distances[neighbor] = newDistance;
                }
            }
        }
    }

    // Return the shortest distance from the start node to all nodes
    return distances;
}

// Example: Find shortest distances from node A to all other nodes in the graph
console.log(dijkstra(graph, "A")); // Outputs: { A: 0, B: 1, C: 3, D: 4 }
```

---

![meme](https://www.meme-arsenal.com/memes/c8994588e4691f44dec49f4fe3791027.jpg)

