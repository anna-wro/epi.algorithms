#G1* - Gra

Student MPU (Mało Prestiżowego Uniwersytetu) Paweł uważa, że jest najlepszy w każdą grę planszową. Generalnie zawsze wygrywa. Jego kolega z PU, Szymek wpadł na pomysł, że zrobią pojedynek w gre, którą on wymyślił.
Gra się składa z szachownicy, domina, oraz dwóch pionków. Zasady są następujące:
1) Szymek wybiera dwa niekoniecznie różne pola na szachownicy na których stawia pionki.
2) Po położeniu pionków przez Szymka, Paweł musi pokryć wszytskie pola szachownicy kostkami domina, tak aby 
- ani jedno pole na szachownicy nie zostało wolne
- nie może układać domina na polu z pionkiem
- domino nie może wystawać poza szachownice
- domina nie mogą się nakładać
- każde domino musi leżeć idealnie tylko na dwóch przyległych polach.

Każde jedno domino zajmuje dokładnie dwa pola szachownicy. Należy założyć, że do dyspozycji mamy nieskończoną ilość domin. Paweł nie chce liczyć na przypadek, może zrezygnować z każdego wyzwania, dlatego prosi Ciebie, znanego programistę abyś napisał program, który podpowie czy wygra.

**Zadanie**

Napisz program, który wczyta ustawienie pionków na planszy i odpowie który z zawdoników wygra.

**Wejście**

Pierwsza i jedyna linia wejścia zawiera 5 liczb całkowitych n,x1,y1,x2,y2. Liczba n (2 ≤ n ≤ 64 ) oznacza szerokość i zarazem wysokość szachownicy, n jest liczbą parzystą; x1,y1 (1 ≤ x1,y1 ≤ n) pozycja pierwszego pionka; x2,y2 (1 ≤ x2,y2 ≤ n) pozycja drugiego pionka Można zalożyć, że czarny kwadrat jest na pozycji 1,1.

**Wyjście**

Dla danego ustawienia należy stwierdzić, który z zawodników wygra. Jeśli nie da się pokryć planszy dominem wtedy wygrywa Szymek i należy wypisać SZYMEK, jeśli da się ułożyć domino wtedy wygrywa Pawel i program powinien napisać PAWEL.

**Przykład**

Dla danych wejściowych:

    8 1 1 8 8
    
poprawną odpowiedzią jest:

    SZYMEK
    
Nie da się w tym przypadku ułożyć domina ale dla danych wejściowych:

    4 1 1 2 3
    
poprawną odpowiedzią jest:

    PAWEL
    
Code:

    #include <stdio.h>
    int main(){
      int n, x[2], y[2];
      scanf("%d", &n);
      if (2 <= n && n <= 64){
        scanf("%d %d %d %d", &x[0], &y[0], &x[1], &y[1] );
        if((1 <= x[0]) && (1 <= x[1]) && (1 <= y[0]) && (1 <= y[1]) && (x[0] <= n) && (x[1] <= n) &&  (y[0] <= n) && (y[0] <= n)){
          if ( ((x[0]==y[0]) && (x[1]==y[1])) || ((((x[0] + y[0]) % 2 == 0) && ((x[1] + y[1]) % 2 == 0)) || (((x[0] + y[0]) % 2 != 0) && ((x[1] + y[1]) % 2 != 0))) ){
            printf("SZYMEK");
          }else printf("PAWEL");
        }
      }
    }
