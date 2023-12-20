// DijkstraAlgorithm..

import java.util.*;

public class DijkstraAlgorithm 
{

    static class Edge 
    {
        int destination;
        int weight;

        Edge(int destination, int weight) 
        {
            this.destination = destination;
            this.weight = weight;
        }
    }

    static class Graph 
    {
        int vertices;
        List<List<Edge>> adjList;

        Graph(int vertices) 
        {
            this.vertices = vertices;
            adjList = new ArrayList<>(vertices);
            for (int i = 0; i < vertices; i++) 
            {
                adjList.add(new ArrayList<>());
            }
        }

        void addEdge(int source, int destination, int weight) 
        {
            Edge edge = new Edge(destination, weight);
            adjList.get(source).add(edge);
        }

        void dijkstra(int source) 
        {
            PriorityQueue<Edge> minHeap = new PriorityQueue<>((a, b) -> Integer.compare(a.weight, b.weight));
            int[] distance = new int[vertices];
            Arrays.fill(distance, Integer.MAX_VALUE);
            distance[source] = 0;
            minHeap.offer(new Edge(source, 0));

            while (!minHeap.isEmpty()) 
            {
                Edge current = minHeap.poll();
                int currVertex = current.destination;

                for (Edge neighbor : adjList.get(currVertex)) 
                {
                    int newDistance = distance[currVertex] + neighbor.weight;
                    if (newDistance < distance[neighbor.destination]) 
                    {
                        distance[neighbor.destination] = newDistance;
                        minHeap.offer(new Edge(neighbor.destination, newDistance));
                    }
                }
            }

            // Print shortest distances
            for (int i = 0; i < vertices; i++) 
            {
                System.out.println("Shortest distance from source to " + i + ": " + distance[i]);
            }
        }
    }

    public static void main(String[] args) 
    {
        int vertices; // Enter the number of vertices accordingly
        
        Scanner scanner = new Scanner(System.in);
        System.out.println("Enter the number of vertices: ");
        vertices = scanner.nextInt();
        
        Graph graph = new Graph(vertices);

        System.out.println("Enter the number of Edges: ");
        int edges = scanner.nextInt();
        
        // Since the dijkstra's algorithm is applicable for non-directional graphs. 
        // We can consider the path in both the directions 
        // Hence we have multiplied the edges with 2. 
        
        int x = edges*2;
        
        for(int i = 0; i<x; i++)
        {
            graph.addEdge(scanner.nextInt(), scanner.nextInt(), scanner.nextInt());
        }


        int source = 0; // Specify the source vertex
        graph.dijkstra(source);
    }
}
