#S1 - Samochody


**Zadanie**

W sobotę rano studenci PU (Prestiżowego Uniwersytetu) zorientowali się, żę ktoś powrzucał im kluczyki do samochodów. Taka sytuacja zdarza się prawie co tydzień. Niezindytyfikowany troll ma taką zasadę, że do każdego auta wrzuca losowo tylko jeden kluczyk i zamyka drzwi. Pod koniec zostawia kartkę z rozmieszczeniem kluczyków w samochodach. Studenci składają się razem na naprawę szyb (500 CBL/sztuka) i poprosili Ciebie abyś napisał'a program, który będzie liczył najmniejszy koszt naprawy.

**Wejście**

W pierwszej linii standardowego wejścia znajduje się jedna liczba całkowita m oznaczająca liczbe samochodów na parkingu. Następnie znajduję się opis położenia kluczyków, czyli m liczb z przedziualu 1 do m. Liczba k na pozycji i'tej oznacza, że samochód i ma klucz do k.

**Wyjście**

Dla danego rozmieszczenia kluczyków oblicz ile najmniej mogą zapłacić studenci.

**Przykład**

Dla danych wejściowych:
5
3 1 2 5 4
poprawną odpowiedzią jest:
1000


    #include <stdio.h>
    int main(){
      int tab[100];
      int n;
      scanf("%d",&n);
      int wybite;
      wybite=0;
      int samochod, pomocnicza;
      int i;
      for(i=0; i<n; i++) scanf("%d",&tab[i]);
      for(i=0; i<n; i++){
        if(tab[i]!=0){
        samochod = tab[i];
        tab[i]=0;
        wybite++;
      while (tab[samochod-1]!=0){
        pomocnicza = samochod;
        samochod = tab[samochod-1];
        tab[pomocnicza-1]=0;
      }
      }
    }
    printf ("%d\n", wybite*500);
    return 0;
    }
