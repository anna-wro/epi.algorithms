#K3 - Krążki O(m + n)

**Zadanie**

Rozwiąż zadanie K1 w czasie liniowym.

Code:

    #include <stdio.h>
    int main() {
      int m,i,n,a,j;
      scanf("%d %d", &n, &m);
      int rurka[n], krazki[m];
      for (i=0; i<n; i++) scanf("%d", &rurka[i]);
      for (i=1; i<n; i++) if(rurka[i]>rurka[i-1]) rurka[i]=rurka[i-1];
      for (i=0; i<m; i++) scanf("%d", &krazki[i]);
      for (i=0; i<m; i++){
            if((i!=m-1 && n==0) || krazki[i]>rurka[0]){ //sprawdzenie czy krazek nie zapcha rurki, jak zapcha, to "0"
                printf("0");
                return 0;
            }
            for(j=n-1;j>0;j--){
                if (krazki[i]<=rurka[j])break; //idzie od dołu rurki, jak znajdzie miejsce, to wychodzi z pętli
            }
            n=j;
      }
        printf("%d", j+1);
        return 0;
    }
