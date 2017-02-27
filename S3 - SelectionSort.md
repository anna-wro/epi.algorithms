#S3 - SelectionSort

**Zadanie**

Napisz selection sorta.

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

Code:

    #include <stdio.h>

    void swap(int *x, int *y){
        int temp = *x;
            *x = *y;
            *y  = temp;
    }
    void selsort(int d, int *l){
        int i, j, min, posmin;

        for (j=0; j<d; j++){
            posmin = j;
            for (i=j+1; i<d; i++){
                if (l[posmin]>l[i]) posmin = i;
            }
        swap(&l[j], &l[posmin]);
        }
    }
    int main(){
        int zestawy_testowe, ile_liczb_do_posortowania, i, j;

        scanf("%d",&zestawy_testowe);
            if (zestawy_testowe>=1 && zestawy_testowe<=100000){
                for (i=0; i< zestawy_testowe; i++){
                    scanf("%d", &ile_liczb_do_posortowania);
                    if (ile_liczb_do_posortowania>=2 && ile_liczb_do_posortowania<=500000){
                        int liczby[ile_liczb_do_posortowania];
                        for(j=0; j<ile_liczb_do_posortowania; j++){
                            scanf("%d", &liczby[j]);
                        }
                        selsort(ile_liczb_do_posortowania, liczby);
                        for(j=0; j<ile_liczb_do_posortowania; j++){
                            printf("%d ", liczby[j]);
                        }
                        printf("\n");
                    }
                }
            }
    return 0;
    }
