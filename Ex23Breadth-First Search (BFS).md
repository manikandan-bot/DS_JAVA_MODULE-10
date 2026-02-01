# Ex23 Breadth-First Search (BFS) Traversal of a City Junction Map
## DATE:
## AIM:
To design and implement a java program to perform Breadth-First Search (BFS) traversal on a city’s junction map represented as a graph, and find all reachable locations from a given source junction.
## Algorithm
1. Start the program.
2. Read the number of junctions and create an adjacency list to represent the graph.
3. Read the connections (edges) between city junctions.
4. Initialize a queue and a visited array to track visited junctions.
5. Insert the starting junction into the queue and mark it as visited.
6. While the queue is not empty:
 
   Remove the front node from the queue and print it.

   Add all unvisited adjacent junctions to the queue and mark them visited.

7. Display all traversed junctions in BFS order.

8. Stop the program.

## Program:
```java
/*
Program to perform Breadth-First Search (BFS) traversal on a city’s junction map represented as a graph
Developed by: MANIKANDAN T
RegisterNumber: 212224110037
*/

import java.util.*;

public class BFS_CityJunction {

    static void bfsTraversal(List<List<Integer>> graph, int start, int n) {
        boolean[] visited = new boolean[n];
        Queue<Integer> queue = new LinkedList<>();

        visited[start] = true;
        queue.add(start);

        System.out.print("BFS Traversal: ");

        while (!queue.isEmpty()) {
            int node = queue.poll();
            System.out.print(node + " ");

            for (int neighbor : graph.get(node)) {
                if (!visited[neighbor]) {
                    visited[neighbor] = true;
                    queue.add(neighbor);
                }
            }
        }
        System.out.println();
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter number of junctions: ");
        int n = sc.nextInt();

        List<List<Integer>> graph = new ArrayList<>();
        for (int i = 0; i < n; i++) {
            graph.add(new ArrayList<>());
        }

        System.out.print("Enter number of roads (edges): ");
        int e = sc.nextInt();

        System.out.println("Enter each road (junction1 junction2):");
        for (int i = 0; i < e; i++) {
            int u = sc.nextInt();
            int v = sc.nextInt();
            graph.get(u).add(v);
            graph.get(v).add(u);  // For undirected city map
        }

        System.out.print("Enter source junction: ");
        int start = sc.nextInt();

        bfsTraversal(graph, start, n);

        sc.close();
    }
}
```

## Output:
<img width="380" height="409" alt="image" src="https://github.com/user-attachments/assets/052e429b-8647-451f-a222-f5ab3a1a89bd" />



## Result:
The program has been successfully implemented and executed.
It performs Breadth-First Search (BFS) traversal on a city junction map and correctly lists all reachable locations from the given source node.
