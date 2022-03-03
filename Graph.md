# Graph

```cpp
#include<bits/stdc++.h>
using namespace std;

void addEdge(vector<int> adj[], int u, int v){ 
    adj[u].push_back(v); 
    adj[v].push_back(u); 
} 
   
void printGraph(vector<int> adj[], int V){ 
    for (int i = 0; i < V; i++){ 
        for (int x : adj[i]) 
           cout << x <<" "; 
        cout<<"\n"; 
    } 
} 

// Breadth First Search
vector<int> bfs(vector<int> adj[], int V, int s){
    vector<int> bfsOrder;
    vector<bool> vis(V, false);
    queue<int> q;
    q.push(s);
    vis[s] = true;
    while(q.empty() == false){
        int u = q.front(); q.pop();
        bfsOrder.push_back(u);
        for(int v: adj[u]){
            if(vis[v] == false){
                q.push(v);
                vis[v] = true;
            }
        }
    }
    return bfsOrder;
}

// BFS for disconnected components
// Print number of islands in a graph or Number of connected components in a graph
void bfsUtil(vector<int> adj[], int s, vector<bool> &vis, vector<int> &bfsOrder){
    queue<int> q;
    q.push(s);
    vis[s] = true;
    while(q.empty() == false){
        int u = q.front(); q.pop();
        bfsOrder.push_back(u);
        for(int v: adj[u]){
            if(vis[v] == false){
                q.push(v);
                vis[v] = true;
            }
        }
    }
}

vector<int> bfs(vector<int> adj[], int V, int s){
    vector<int> bfsOrder;
    int countOfComponents = 0;
    vector<bool> vis(V, false);
    for(int i = 0; i < V; i++){
        if(vis[i] == false){
            bfsUtil(adj, s, vis, bfsOrder);
            countOfComponents++;
        }
    }
    return bfsOrder;
}

// Depth First Search
void dfsUtil(vector<int> adj[], int s, vector<int> &vis, vector<int> &dfsOrder){
    vis[s] = true;
    dfsOrder.push_back(s);
    for(int v: adj[s])
        if(vis[v] == false)
            dfsUtil(adj, v, vis, dfsOrder);
}

vector<int> dfs(vector<int> adj[], int V, int s){
    vector<bool> vis(V, false);
    vector<int> dfsOrder;
    dfsUtil(adj, s, vis, dfsOrder);
    return dfsOrder;
}

// DFS for disconnected components
// Print number of islands in a graph or Number of connected components in a graph
void dfsUtil(vector<int> adj[], int s, vector<int> &vis, vector<int> &dfsOrder){
    vis[s] = true;
    dfsOrder.push_back(s);
    for(int v: adj[s])
        if(vis[v] = false)
            dfsUtil(adj, v, vis, dfsOrder);
}

vector<int> dfs2(vector<int> adj[], int V){
    vector<bool> vis(V, false);
    int countOfComponents;
    vector<int> dfsOrder;
    for(int i = 0; i < V; i++){
        if(vis[i] == false){
            dfsUtil(adj, s, vis, dfsOrder);
            countOfComponents++;
        }
    }
    return dfsOrder;
}

// Driver code 
int main(){ 
    int V = 4; 
    vector<int> adj[V]; 
    addEdge(adj, 0, 1); 
    addEdge(adj, 0, 2); 
    addEdge(adj, 1, 2); 
    addEdge(adj, 1, 3); 
    printGraph(adj, V); 
    return 0; 
}

```
