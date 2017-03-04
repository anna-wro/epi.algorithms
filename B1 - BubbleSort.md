#B1 - BubbleSort

**Zadanie**

Napisz bubblesorta.

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

**Kod**
    
    #include <iostream>

    void sortuj(int, int*);

    int main(){

        int zestawy, i, j, dlugosc, liczby[500000];

        std::cin >> zestawy;

        if (zestawy>0 && zestawy<100000){
            for (i = 0; i<zestawy; i++){
                std::cin >> dlugosc;
                if (dlugosc != 0 && dlugosc < 500000){
                    for (j = 0; j < dlugosc; j++){
                        std::cin >> liczby[j];
                    }
                    if(dlugosc != 1){
                        sortuj(dlugosc, liczby);
                    }

                    for (j = 0; j < dlugosc; j++){
                        std::cout << liczby[j] << " ";
                    }
                    std::cout << "\n";
                }
            }
        }
        return 0;
    }
