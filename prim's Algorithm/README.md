# C PROGRAM
```
#include <stdio.h>
#include <limits.h>
#include <stdbool.h>

#define V 5

int minKey(int key[], bool inMST[]) {
    int min = INT_MAX, min_index = -1;

    for (int v = 0; v < V; v++) {
        if (!inMST[v] && key[v] < min) {
            min = key[v];
            min_index = v;
        }
    }
    return min_index;
}

void primMST(int graph[V][V]) {
    int parent[V];
    int key[V];
    bool inMST[V];

    for (int i = 0; i < V; i++) {
        key[i] = INT_MAX;
        inMST[i] = false;
    }

    key[0] = 0;
    parent[0] = -1;

    for (int count = 0; count < V - 1; count++) {
        int u = minKey(key, inMST);
        inMST[u] = true;

        for (int v = 0; v < V; v++) {
            if (graph[u][v] && !inMST[v] && graph[u][v] < key[v]) {
                parent[v] = u;
                key[v] = graph[u][v];
            }
        }
    }

    for (int i = 1; i < V; i++) {
        printf("%d - %d\n", parent[i], i);
    }
}

int main() {
    int graph[V][V] = {
        {0, 2, 0, 6, 0},
        {2, 0, 0, 0, 0},
        {0, 0, 0, 0, 0},
        {6, 0, 0, 0, 0},
        {0, 0, 0, 0, 0}
    };

    primMST(graph);
    return 0;
}
```
# C++ - PROGRAM
```
#include <iostream>
#include <climits>
using namespace std;

#define V 5

int minKey(int key[], bool inMST[]) {
    int min = INT_MAX, min_index = -1;

    for (int v = 0; v < V; v++) {
        if (!inMST[v] && key[v] < min) {
            min = key[v];
            min_index = v;
        }
    }
    return min_index;
}

void primMST(int graph[V][V]) {
    int parent[V];
    int key[V];
    bool inMST[V];

    for (int i = 0; i < V; i++) {
        key[i] = INT_MAX;
        inMST[i] = false;
    }

    key[0] = 0;
    parent[0] = -1;

    for (int count = 0; count < V - 1; count++) {
        int u = minKey(key, inMST);
        inMST[u] = true;

        for (int v = 0; v < V; v++) {
            if (graph[u][v] && !inMST[v] && graph[u][v] < key[v]) {
                parent[v] = u;
                key[v] = graph[u][v];
            }
        }
    }

    for (int i = 1; i < V; i++) {
        cout << parent[i] << " - " << i << endl;
    }
}

int main() {
    int graph[V][V] = {
        {0, 2, 0, 6, 0},
        {2, 0, 0, 0, 0},
        {0, 0, 0, 0, 0},
        {6, 0, 0, 0, 0},
        {0, 0, 0, 0, 0}
    };

    primMST(graph);
    return 0;
}
```

# JAVA-PROGRAM 

```
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