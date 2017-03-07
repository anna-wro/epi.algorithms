#K2 - Krążki O(m log n)

**Zadanie**

Rozwiąż zadanie K1 używając binarysearch

**Kod**

    #include <stdio.h>
    int BS(int x,int left,int right,int rurka[]){
      int mid = (left+right+1)/2;
      if (left!=right){
        if (x<=rurka[mid]) return BS(x,mid,right,rurka);
        else if(x>rurka[mid]) return BS(x,left,mid-1,rurka);
      } else return mid;
    }
    int main(void) {
      int m,i,n,j;
      scanf("%d", &n);
      scanf("%d", &m);
      int rurka[n], krazki[m];
      for (i=0; i<n; i++) scanf("%d", &rurka[i]);
      for (i=1; i<n; i++) if(rurka[i]>rurka[i-1]) rurka[i]=rurka[i-1];
      for (i=0; i<m; i++) scanf("%d", &krazki[i]);
      for (i=0; i<m; i++){
        if (BS(krazki[i],0,n-1,rurka)==0 && i!=n-1){
          printf("0");
          return 0;
        }
        n=BS(krazki[i],0,n-1,rurka);
      }
      printf("%d", n+1);
      return 0;
    }
