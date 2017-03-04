#G2 - Gaz

W podziemnej sieci metra rosprzestrzenia się niebezpieczny gaz. Mając dokładny opis tuneli, oblicz poziom bezpieczeństwa dla każdej stacji.
Poziom bezpieczeństwa jest liczony jako najkrótsza odległość dla danej stacji od źródła gazu.

**Zadanie**

Napisz program, który:
• wczyta ze standardowego wejścia liczbę stacji, gdzie znajduje się źródło i opis systemu tuneli,
• obliczy poziom bezpieczeństwa dla każdej ze stacji,
• wypisze wyniki na standardowe wyjście.

**Wejście**

W pierwszym wierszu standardowego wejścia znajduje się trzy liczby naturalne n,m,k (2 ≤ n ≤ 100, 1 ≤ m ≤ 100, 1 ≤ k ≤ n ). Pierwsza z nich oznacza ilość stacji druga, liczbę połączeń a k oznacza numer stacji, w której znajduje się źródło niebezpiecznego gazu. Następnie znajduje się opis tuneli - w m kolejnych liniach podane są po dwie liczby a,b (1 ≤ a,b ≤ n) mówiące między którymi stacjami istnieje połączenie.

**Wyjście**

W m kolejnych liniach należy podać po dwie liczby, numer stacji oraz jej poziom bezpieczeństwa.

**Przykład 1**

Dla danych wejściowych:

    6 5 2
    1 2
    1 4
    4 5
    5 6
    3 6

poprawną odpowiedzią jest:

    1 1
    2 0
    3 5
    4 2
    5 3
    6 4

**Przykład 2**

Dla danych wejściowych:

    6 6 2
    1 2
    1 4
    2 5
    4 5
    5 6
    3 6

poprawną odpowiedzią jest:

    1 1
    2 0
    3 3
    4 2
    5 1
    6 2

**Kod**

    #include <stdio.h>
    #include <vector>
    #include <queue>

    using namespace std;

    int main() {

      int n, m, k, l, gaz, i;
      int visited[100], lvl[100];
      vector <int> wektor[100];
      queue <int> kolejka;

        scanf("%d %d %d", &n,  &m, &gaz);

        if( 2>=n<=100 && 1>=m<=100 && 1>=k<=n  ){
            for (i=0; i<m; i++){
                scanf("%d %d", &k, &l);
                wektor[k].push_back(l);
                wektor[l].push_back(k);
            }
            for (i=1; i<=n; i++)
                visited[i] = 0;

            kolejka.push(gaz);
            visited[gaz] = 1;
            lvl[gaz]=0;

            while(!kolejka.empty()){
                int node = kolejka.front();
                kolejka.pop();
                for(i=0; i<wektor[node].size(); i++){
                    if (visited[wektor[node][i]]==0){
                        visited[wektor[node][i]] = 1;
                        kolejka.push(wektor[node][i]);
                        lvl[wektor[node][i]] = lvl[node]+1;
                    }
                }
            }
            for (i=1; i<=n; i++)
                printf("%d %d\n", i, lvl[i]);
            }
    return 0;
    }
