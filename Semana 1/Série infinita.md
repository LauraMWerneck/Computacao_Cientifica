## Código em C
```c
#include <stdio.h>
#include <stdlib.h>
#include <math.h>
int main()
{
float i, fn = 0;
double const real = pow(M_PI,4)/90;
double erro;
for(i=1;i<=10000;i++)
{
fn = fn + (1/(i*i*i*i));
}
printf("real = %.11f\n",real);
erro = (real - fn)*100/real;
printf("Crescente: fn = %f com erro de %f\n",fn,erro);
fn = 0;
for(i=10000;i>=1;i--)
{
fn = fn + (1/(i*i*i*i));
}
erro = (real - fn)*100/real;
printf("Decrescente: fn = %f com erro de %f",fn,erro);
return 0;
}

```
