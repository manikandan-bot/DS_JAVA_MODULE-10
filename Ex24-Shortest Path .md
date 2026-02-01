# Ex24 Shortest Path and Reachability in a Heritage Town using BFS
## DATE:
## AIM:
To design and implement a java program that, given a map of attractions in a heritage town connected by walking paths, recommends:
The shortest number of paths (minimum hops) from a starting attraction to a target attraction.
The number of reachable attractions from the same starting point using Breadth-First Search (BFS)


## Algorithm
1. Start the program.
2. Read the number of attractions and initialize an adjacency list.
3. Read the walking paths (edges) connecting attractions.
4. Use BFS to find:

   Shortest path (minimum hops) from start node to destination node using a distance array.

   Reachability count, i.e., number of attractions reachable from the start.

5. Initialize arrays for visited and distance, and a queue for BFS.
6. Set the starting node as visited and enqueue it.
7. While the queue is not empty:
   
  Dequeue the current node.

  For each adjacent node, if not visited, enqueue it and update its distance.

8. After BFS completes:

9. Display reachable attractions and count.

10. Display the shortest distance to the destination node.

11. Stop the program.

## Program:
```java
/*
Program to determine Shortest Path and Reachability in a Heritage Town using BFS
Developed by:MANIKANDAN T
RegisterNumber: 212224110037
*/
import java.util.*;

public class HeritageTownBFS {

    public static void bfs(int start, List<List<Integer>> graph, int n, int destination) {
        boolean[] visited = new boolean[n];
        int[] distance = new int[n];
        Arrays.fill(distance, -1);

        Queue<Integer> queue = new LinkedList<>();
        visited[start] = true;
        distance[start] = 0;
        queue.add(start);

        int reachableCount = 0;

        System.out.print("Reachable Attractions: ");

        while (!queue.isEmpty()) {
            int node = queue.poll();
            System.out.print(node + " ");
            reachableCount++;

            for (int next : graph.get(node)) {
                if (!visited[next]) {
                    visited[next] = true;
                    distance[next] = distance[node] + 1;
                    queue.add(next);
                }
            }
        }

        System.out.println("\nTotal reachable attractions: " + reachableCount);

        if (distance[destination] != -1)
            System.out.println("Shortest path (minimum hops) to attraction " + destination + ": " + distance[destination]);
        else
            System.out.println("Destination attraction is not reachable.");
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter number of attractions: ");
        int n = sc.nextInt();
        List<List<Integer>> graph = new ArrayList<>();

        for (int i = 0; i < n; i++) {
            graph.add(new ArrayList<>());
        }

        System.out.print("Enter number of walking paths: ");
        int e = sc.nextInt();

        System.out.println("Enter paths (attraction1 attraction2):");
        for (int i = 0; i < e; i++) {
            int u = sc.nextInt();
            int v = sc.nextInt();
            graph.get(u).add(v);
            graph.get(v).add(u); // undirected
        }

        System.out.print("Enter starting attraction: ");
        int start = sc.nextInt();

        System.out.print("Enter destination attraction: ");
        int destination = sc.nextInt();

        bfs(start, graph, n, destination);
        sc.close();
    }
}
```

## Output:

<img width="538" height="500" alt="image" src="https://github.com/user-attachments/assets/5c316122-d16b-4743-b5b3-341f81b28788" />


## Result:
The program has been successfully implemented and executed.
It correctly computes:
The shortest number of paths (minimum hops) between two attractions.
The total number of reachable attractions from a given starting point using BFS traversal.
