```JAVA
import java.util.*;
class prim {
    static final int V = 5;

    int minkey(int key[], boolean mstSet[]) {

        int min = Integer.MAX_VALUE, minIndex = -1;
        for (int v = 0; v < V; v++)
            if (!mstSet[v] && key[v] < min) {
                min = key[v];
                minIndex = v;

            }
        return minIndex;
    }

    void primMST(int graph[][]) {
        int parent[] = new int[V];
        int key[] = new int[V];
        boolean mstSET[] = new boolean[V];

        Arrays.fill(key, Integer.MAX_VALUE);
        Arrays.fill(mstSET, false);

        key[0] = 0;
        parent[0] = -1;

        for (int count = 0; count < V - 1; count++) {
            int u = minkey(key, mstSET);
            mstSET[u] = true;

            for (int v = 0; v < V; v++)
                if (graph[u][v] != 0 && !mstSET[v] && graph[u][v] < key[v]) {
                    parent[v] = u;
                    key[v] = graph[u][v];
                }
        }
        System.out.println("edges \tweight");
        for(int i = 1; i < V; i++)
            System.out.println(parent[i] + " _ " + i + "\t" +graph[i] [parent[i]]);
    }
    public static void main(String[] args) {
        prim p = new prim();

        int graph[][] = {
                {0, 2, 0, 6, 0},
                {2, 2, 3, 6, 5},
                {0, 3, 9, 5, 7},
                {6, 8, 0, 4, 9},
                {0, 5, 7, 9, 0}
        };

        p.primMST(graph);
    }

}
```