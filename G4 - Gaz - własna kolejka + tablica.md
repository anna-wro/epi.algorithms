#G4 - Gaz - własna kolejka + tablica

**Zadanie**

Rozwiąż zadanie G2 używając swojej własnej kolejki oraz macierzy sąsiedztwa do reprezentacji grafu - czyli nie wolno Ci użyć klasy queue oraz vector. Możesz założyć, że maksymalnie będziemy mieli nie więcej niż 100 wierzchołków.

**Kod**

    #include <stdio.h>
    using namespace std;

    int tab[100000];
    int p=0;
    int k=0;

    bool k_empty(){
      if (k==p)
        return true;
      else 
        return false;
    }
    void k_push(int x){
      tab[k] =x;
      k++;
    }
    void k_pop(){
      p++;
    }
    int k_front(){
      return tab[p]; 
    }

    int main() {
      int n, m, k, l, gaz, i, a, b;
      int visited[100], lvl[100];
      int macierz[100][100];
      
        scanf("%d %d %d", &n,  &m, &gaz);

      for (a=0;a<100;a++){
        for (b=0;b<100;b++){
          macierz[a][b] = 0;
        }
      }

        if( 2>=n<=100 && 1>=m<=100 && 1>=gaz<=n  ){
            for (i=0; i<m; i++){
                scanf("%d %d", &k, &l);
          macierz[k][l] =1;
          macierz[l][k] =1;
            }
            for (i=1; i<=n; i++)
                visited[i] = 0;

            k_push(gaz);
            visited[gaz] = 1;
            lvl[gaz]=0;

            while(!k_empty()){
              int node = k_front();
              k_pop();
              for(i=0; i<100; i++){
                if (macierz[node][i] == 1){
                  if (visited[i] == 0){
                    visited[i] = 1;
                    k_push(i);
                    lvl[i] = lvl[node]+1;
                  }
                }					
              }
            }
            for (i=1; i<=n; i++)
                printf("%d %d\n", i, lvl[i]);
            }

    return 0;
    }
