#Q1 - QuickSort

**Zadanie**

Napisz standardowego quicksorta.

**Wejście**

W pierwszym wierszu znajduje się liczba d zestawów testowych( 1≤ d ≤ 100 000 ). Każdy zestaw składa się z dwóch wierszy. W pierwszym wierszu dana jest liczba n ( 2≤n≤ 500000), gdzie n oznacza ilość liczb do posortowania. W wierszu drugim znajduje się ciąg liczb o długości n.

**Wyjście**

Na wyjściu należy wypisać d wierszy, w każdym wierszu posorotwane ciągi liczb dla danego zestawu.

**Przykład**

Dla danych wejściowych:

    3
    3
    1 2 3
    6
    6 5 4 3 2 1
    2
    20 12
    
poprawną odpowiedzią jest:

    1 2 3
    1 2 3 4 5 6
    12 20
    
Kod:

    #include<iostream>
    using namespace std;

    int podzial(int tablica[], int p, int r){
        int x = tablica[p];
        int i = p, j = r, w;
        while (true){
            while (tablica[j] > x)
                j--;
            while (tablica[i] < x)
                i++;
            if (i < j){
                w = tablica[i];
                tablica[i] = tablica[j];
                tablica[j] = w;
                i++;
                j--;
            } else
                return j;
        }
    }

    void quicksort(int tablica[], int p, int r){
        int q;
        if (p < r){
            q = podzial(tablica,p,r);
            quicksort(tablica, p, q);
            quicksort(tablica, q+1, r);
        }
    }

    int main(){
        int liczba_zestawow, ile_liczb, i, j;
        cin >> liczba_zestawow;
        if (liczba_zestawow>=1 && liczba_zestawow<=100000){
            for(i=0;i<liczba_zestawow;i++){
                cin >> ile_liczb;
                if (ile_liczb>=2 && ile_liczb<=500000){
                    int tablica[ile_liczb];

                    for (j = 0; j < ile_liczb; j++)
                        cin >> tablica[j];
                        quicksort(tablica,0,ile_liczb-1);
                    for (j = 0; j < ile_liczb; j++){
                        cout << tablica[j] << " ";
                    }
                    cout << endl;
                }
            }
        }
    return 0;
    }
