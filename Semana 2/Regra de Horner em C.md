## Código

```c
#include <stdio.h>
int main()
{
int n,i;
float x, a[10],y;
printf("Entre com o grau do polinomio: ");
scanf("%d",&n);
printf("Entre com o valor de x : ");
scanf("%f",&x);
printf("Entre com os coeficientes: \n" );
printf("a%d = ",n);
scanf("%f",&y);
for(i=n-1; i>=0; i--) {
printf("a%d = ",i);
scanf("%f",&a[i]);
y = y*x + a[i];
}
printf("O valor do polinomio em x = %f vale %f", x, y);
return 0;
}
```
