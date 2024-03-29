# S2* - Silnia

Niech n będzie nieujemną liczbą całkowitą. Liczbę n! definiuje się następująco. Jeśli n ≤ 1, to n! = 1. Dla n > 1, n! jest równe iloczynowi wszystkich liczb od 1 do n, czyli n! = 1 * 2 * ... * n. Na przykład 4! = 1*2*3*4 = 24.

**Wejście**

W pierwszej linii wejścia znajduje się jedna liczba całkowia D (1≤D≤1 000 000), oznaczjąca liczbę przypadków do rozważenia. Opis każdego przypadku składa się z jednej linii, w której znajduje się jedna nieujemna liczba całkowita n (0 ≤ n ≤ 1 000 000 000).

**Wyjście**

Dla każdego przypadku z wejścia. Twój program powinien wypisać w osobnej linii dokładnie dwie cyfry (oddzielone pojedynczą spacją): cyfrę dziesiątek i cyfrę jedności liczby n! zapisanej w systemie dziesiętnym.

**Przykład**

Dla danych wejściowych:

     2
     1
     4

poprawną odpowiedzią jest:

    0 1
    2 4
    
**Kod**

     #include <stdio.h>
     int main(){
         int d,n;
         scanf("%d", &d);
         while(d--){
             scanf("%d", &n);
             if(n>9) printf("0 0\n");
             if(n<2) printf("0 1\n");
             if((4<n && n<7) || n==8) printf("2 0\n");
             if(n==2) printf("0 2\n");
             if(n==3) printf("0 6\n");
             if(n==4) printf("2 4\n");
             if(n==7) printf("4 0\n");
             if(n==9) printf("8 0\n");
     }
     return 0;
     }
