# Ex25 Finding the Fastest Route to a Charging Station using Dijkstra’s Algorithm
## DATE: 
## AIM:
To design and implement a java program that helps an electric vehicle (EV) find the shortest travel time from its current block to the nearest charging station using Dijkstra’s shortest path algorithm.
## Algorithm
1. Start the program and input the number of blocks (nodes) and roads (edges).
2. Construct a graph using an adjacency matrix or adjacency list where each edge contains the time taken to travel between blocks.
3. Input the current block of the EV and the list of blocks that contain charging stations.
4. Apply Dijkstra’s algorithm from the EV’s current block to compute the shortest travel time to every other block.
5. Identify the block from the charging station list that has the minimum travel time.
6. Display the shortest time and the corresponding charging station.
7. If no charging station is reachable, display an appropriate message.
8. Stop the program.

## Program:
```java
/*
Program to find the Fastest Route to a Charging Station using Dijkstra’s Algorithm
Developed by: MANIKANDAN T
RegisterNumber: 212224110037
*/
import java.util.*;

class DijkstraEV {
    private static final int INF = Integer.MAX_VALUE;

    public static int dijkstra(int[][] graph, int src, boolean[] charger) {
        int V = graph.length;
        int[] dist = new int[V];
        boolean[] visited = new boolean[V];

        Arrays.fill(dist, INF);
        dist[src] = 0;

        for (int i = 0; i < V - 1; i++) {
            int u = getMinDistanceNode(dist, visited);
            visited[u] = true;

            for (int v = 0; v < V; v++) {
                if (!visited[v] && graph[u][v] != 0 && dist[u] != INF &&
                    dist[u] + graph[u][v] < dist[v]) {
                    dist[v] = dist[u] + graph[u][v];
                }
            }
        }

        int minTime = INF;
        for (int i = 0; i < V; i++) {
            if (charger[i] && dist[i] < minTime) {
                minTime = dist[i];
            }
        }
        return minTime;
    }

    private static int getMinDistanceNode(int[] dist, boolean[] visited) {
        int min = INF, minIndex = -1;
        for (int v = 0; v < dist.length; v++) {
            if (!visited[v] && dist[v] < min) {
                min = dist[v];
                minIndex = v;
            }
        }
        return minIndex;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter number of blocks: ");
        int V = sc.nextInt();

        int[][] graph = new int[V][V];
        System.out.println("Enter travel time matrix (0 if no direct connection): ");
        for (int i = 0; i < V; i++) {
            for (int j = 0; j < V; j++) {
                graph[i][j] = sc.nextInt();
            }
        }

        System.out.print("Enter current EV position (0 to " + (V - 1) + "): ");
        int src = sc.nextInt();

        boolean[] charger = new boolean[V];
        System.out.print("Enter number of charging stations: ");
        int n = sc.nextInt();
        System.out.println("Enter charging station positions:");
        for (int i = 0; i < n; i++) {
            charger[sc.nextInt()] = true;
        }

        int minTime = dijkstra(graph, src, charger);

        if (minTime == INF) {
            System.out.println("No reachable charging station!");
        } else {
            System.out.println("Shortest travel time to nearest charging station: " + minTime + " minutes");
        }
    }
}
```

## Output:

<img width="648" height="443" alt="image" src="https://github.com/user-attachments/assets/1b009bad-d4fe-40aa-85a0-5afa4ecc7836" />


## Result:
The program has been successfully implemented and executed.
It uses Dijkstra’s algorithm to determine the shortest travel time from the EV’s current location to the nearest charging station and correctly handles cases where no station is reachable.
