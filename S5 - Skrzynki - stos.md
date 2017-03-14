# S5 - Skrzynki - stos

**Zadanie**

Rozwiąż zadanie S4, używając stosowej wersji algorytmu DFS.

**Kod**

    #include <iostream>
    #include <vector>
    #include <stack>

    using namespace std;

    int visited[1000000];
    int open;
    vector <int> vertex[1000000];
    stack <int> stos;

    int DFS(int node, int master){
      int i;

      stos.push(node);
      stos.push(master);

      while(!stos.empty()){
        int master = stos.top();
        stos.pop();
        int node = stos.top();
        stos.pop();

        for(i=0; i<vertex[node].size(); i++){
          if(visited[vertex[node][i]]>=-1 && visited[vertex[node][i]]!=master){
            open--;
            visited[vertex[node][i]]=-2;

            stos.push(vertex[node][i]);
            stos.push(master);
          }
        }
      }
    }
    int main() {
        int i,k,n;
        cin >> n;
        for(i=0; i<n; i++){
            cin >> k;
            vertex[k-1].push_back(i);
        }
        open=n;
       for(i=0; i<n; i++)visited[i]=-1;
       for(i=0;i<n;i++){
           if(visited[i]>=-1){
               visited[i]=i;
               DFS(i, i);
       }
       }
        cout << open;
       return 0;
    }
