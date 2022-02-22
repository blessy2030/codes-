# the-bag-of-gold-again
#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>

int max(int a,int b){
    if (a>b) return a;
    return b;
}
int knapsack(int n , int *w , int *p,int m){
    int k[n+1][m+1];
    for(int i=0;i<=n;i++){
        for(int j=0;j<=m;j++){
            if(i==0 || j==0) k[i][j]=0;
            else if(j< w[i]){k[i][j]=k[i-1][j]; }
            else{
                k[i][j]=max(k[i-1][j],p[i]+k[i-1][j-w[i]]);
            }
        }
    }
    return k[n][m];
}
int main(){
    int t;
    scanf("%d",&t);
        while (t--){
            int n ,m;
            scanf("%d%d",&n,&m);
            int w[n+1],p[n+1];
            for (int i=1;i<=n;i++){
                scanf("%d%d",&w[i],&p[i]);
            }
            printf("%d\n",knapsack(n,w,p,m));
    }
    return 0;
}
