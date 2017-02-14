#P1 - Pompy 2D


**Zadanie**

Cały teren jest pod wodą, używająć jak najmniejszej ilości pomp spróbuj go osuszyć. Uwaga: woda na płaskim terenie bez problemu się "przelewa".

**Wejście**

W pierwszej linii standardowego wejścia znajduje się jedna liczba całkowita N z zakresu od 1 do 100, określająca długość teremu. Następnie znajduję sie N liczb opisujące teren, każda z nich jest z przedziału od 1 do 10.

**Wyjście**

Dla danego terenu program powinien wypisać minimalną liczbę pomp do jego całkowitego osuszenia.

**Przykład**

Dla danych wejściowych:
9
5 4 3 3 4 5 6 3 4

poprawną odpowiedzią jest:
2


    #include <stdio.h>
    int main(){
      int i, n, tab[100], pompa;
      scanf("%d", &n);
      for (i=0; i<n; i++) scanf("%d", &tab[i+1]);
      i=1; 
      tab[0]=11; 
      pompa = 0;
      while (i<=n){
        while (i<=n && tab[i-1]>=tab[i]) i++;
        pompa++;
        while (i<=n && tab[i-1]<=tab[i]) i++;
      }
      printf("%d\n", pompa);
      return 0;
    }			
