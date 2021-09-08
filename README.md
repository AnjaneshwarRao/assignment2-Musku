# assignment2-Musku

# Varun Reddy Musku

### my favourite place is Manali  india

Manali is the only place in india where we can find different types of people,animals and when it comes to weather it is too cool.it is the orgin place of 3 rivers. <br>
**Dollar General** <br>
**Advance America**

---
# Marryville To Miami
 1. Start from the marryville Travell towards Farney RD
 2. At the traffic circle,take the 2nd exit onto University Dr.
 3. Merge onto I-44E
 4. Use the right 2 lanes to take exit 291 A for I-24 E/I-65 S towards Nashville 
    1. take 2nd left exit.
 5. Merge onto I-65 S
 6. keep left to continue towars I-24 E
 7. Keep left at the fork to continue on Florida's Turnpike,follow signs for Oralndo/Turnpike S
 8. Turn left onto SW 13th St
     1. continue for the 20 miles.
     2. you reach your destination.

* Dancing
- new places
* travelling
- climate

Link of AboutMe: <https://github.com/varunreddy13/assignment2-Musku/blob/main/AboutMe.md>
-----------------
# Tables

The table shows food items to try in India.

| Food                | Location             | Amount |
| :---                 | ---                  | ---    |
| Biriyani            | Pista House          | $ 20   |
| Chiken Momos        | Delhi                |  $10   |
| Mutton Soup         | Old Delhi            |  $ 7   |
| Mutter Panner       | Jagpul Restreunt     |  $ 10  |
------------

# Pithy Quotes

> A single twig breaks, but the bundle of twigs is strong. __  *Varun*

> Strength does not come from winning. Your struggles develop your strengths. When you go through hardships and decide not to surrender, that is strength. - *Arnold Schwarzenegger*

-----


# code fencing


> In graph theory, a branch of mathematics, a cycle basis of an undirected graph is a set of simple cycles that forms a basis of the cycle space of the graph. That is, it is a minimal set of cycles that allows every even-degree subgraph to be expressed as a symmetric difference of basis cycles.

A fundamental cycle basis may be formed from any spanning tree or spanning forest of the given graph, by selecting the cycles formed by the combination of a path in the tree and a single edge outside the tree. Alternatively, if the edges of the graph have positive weights, the minimum weight cycle basis may be constructed in polynomial time.

In planar graphs, the set of bounded cycles of an embedding of the graph forms a cycle basis. The minimum weight cycle basis of a planar graph corresponds to the Gomory–Hu tree of the dual graph.
code: <https://en.wikipedia.org/wiki/Cycle_basis 


'''

int n;
vector<vector<int>> adj;
vector<char> color;
vector<int> parent;
int cycle_start, cycle_end;

bool dfs(int v) {
    color[v] = 1;
    for (int u : adj[v]) {
        if (color[u] == 0) {
            parent[u] = v;
            if (dfs(u))
                return true;
        } else if (color[u] == 1) {
            cycle_end = v;
            cycle_start = u;
            return true;
        }
    }
    color[v] = 2;
    return false;
}

void find_cycle() {
    color.assign(n, 0);
    parent.assign(n, -1);
    cycle_start = -1;

    for (int v = 0; v < n; v++) {
        if (color[v] == 0 && dfs(v))
            break;
    }

    if (cycle_start == -1) {
        cout << "Acyclic" << endl;
    } else {
        vector<int> cycle;
        cycle.push_back(cycle_start);
        for (int v = cycle_end; v != cycle_start; v = parent[v])
            cycle.push_back(v);
        cycle.push_back(cycle_start);
        reverse(cycle.begin(), cycle.end());

        cout << "Cycle found: ";
        for (int v : cycle)
            cout << v << " ";
        cout << endl;
    }
}

'''

int n;
vector<vector<int>> adj;<br>
vector<bool> visited;<br>
vector<int> parent;<br>
int cycle_start, cycle_end;<br>

bool dfs(int v, int par) { // passing vertex and its parent vertex,<br>
    visited[v] = true;<br>
    for (int u : adj[v]) {<br>
        if(u == par) continue; // skipping edge to parent vertex<br>
        if (visited[u]) {<br>
            cycle_end = v;<br>
            cycle_start = u;<br>
            return true;<br>
        }
        parent[u] = v;<br>
        if (dfs(u, parent[u]))<br>
            return true;<br>
    }
    return false;<br>
}

void find_cycle() {<br>
    visited.assign(n, false);<br>
    parent.assign(n, -1);<br>
    cycle_start = -1;<br>

    for (int v = 0; v < n; v++) {<br>
        if (!visited[v] && dfs(v, parent[v]))<br>
            break;<br>
    }

    if (cycle_start == -1) {<br>
        cout << "Acyclic" << endl;<br>
    } else {<br>
        vector<int> cycle;<br>
        cycle.push_back(cycle_start);<br>
        for (int v = cycle_end; v != cycle_start; v = parent[v])<br>
            cycle.push_back(v);<br>
        cycle.push_back(cycle_start);<br>
        reverse(cycle.begin(), cycle.end());<br>

        cout << "Cycle found: ";
        for (int v : cycle)
            cout << v << " ";
        cout << endl;
    }
}

'''

source code: <https://cp-algorithms.com/graph/finding-cycle.html