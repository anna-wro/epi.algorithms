#M1 - Minimum i maksimum


**Zadanie**

Znajdź najmniejszą i największą liczbę w podanym ciągu liczb całkowitych.

**Wejście**

W pierwszej linii standardowego wejścia znajduje się jedna liczba całkowita N z zakresu od 1 do 1000, określająca liczbę zestawów danych, których opisy umieszczone są kolejno po sobie w następnych wierszach. Opis pojedynczego zestawu składa się z dwóch linii i wygląda następująco: W pierwszej linii znajduje się jedna liczba całkowita M z przedziału od 1 do 1000. W drugiej linii znajduje się M oddzielonych pojedynczymi spacjami liczb całkowitych mi (1≤i≤M, 0≤mi≤1000000).

**Wyjście**

Dla każdego zestawu danych w osobnej linii wypisz dwie liczby A i B oddzielone spacją. Liczba A jest wartością najmniejszej, a liczba B wartością największej liczby spośród danych M liczb mi.

**Przykład**

Dla danych wejściowych:

    3
    3
    1 2 3
    4
    1 2 3 4
    5
    4 3 5 2 6

poprawną odpowiedzią jest:

    1 3
    1 4
    2 6
    
Kod:

    #include <stdio.h>
    int main(void) {
      int test;
    	scanf("%d", &test);
    	for(int i=0; i<test;i++){
    		int n;
    		scanf("%d", &n);
	    	int num[n];
	    	for(int j=0; j<n;j++){
	    		scanf("%d", &num[j]);
    		}
	    	int min = num[0];
	    	int max = num[0];
	    	for(int i = 1; i<n; ++i){
      			if(num[i]<min) {
       				min=num[i];}
       			if(num[i]>max){
       				max=num[i];
	      	}	
	  	  } printf("%d %d\n",min, max);
  	  };
  	  return 0;
    }
