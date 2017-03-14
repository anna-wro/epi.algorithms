# S6 - Skrzynki - własny stos

**Zadanie**

Rozszerzenie do zadania S5: zaimplementuj własny stos i rozwiąż zadanie S4, używając stosowej wersji algorytmu DFS - rozwiązanie nie może korzystac z bliblioteki stack.

**Kod**

    #include <iostream>
    #include <vector>

    using namespace std;

    int visited[1000000];
    int open;
    vector <int> vertex[1000000];

    int tab[100000];
    int W =0;

    void s_push(int x){
      tab[W] =x;
      W++;
    }

    void s_pop(){
      W--;
    }

    int s_top(){
    return tab[W-1]; 
    }

    bool s_empty(){
      if (W==0)
        return true;
      else 
        return false;
    }

    int DFS(int node, int master){
      int i;

      s_push(node);
      s_push(master);

      while(!s_empty()){
        int master = s_top();
        s_pop();
        int node = s_top();
        s_pop();

        for(i=0; i<vertex[node].size(); i++){
          if(visited[vertex[node][i]]>=-1 && visited[vertex[node][i]]!=master){
            open--;
            visited[vertex[node][i]]=-2;

            s_push(vertex[node][i]);
            s_push(master);
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
