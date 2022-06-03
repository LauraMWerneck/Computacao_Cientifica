## Exemplo
Use a aproximação por diferenças progressiva e regressiva
de O(h) e uma aproximação por diferença centrada de
O(h2
) para estimar a derivada primeira de
f(x) = 25x3 – 6x2 + 7x - 88
Avalie a derivada em x = 2 usando o passo de cálculo de
0,5 e 0,25. Compare as suas estimativas com o valor real
da derivada. Interprete seus resultados com base no resto
da expansão em séries de Taylor.
Calcule manualmente e com o auxilio de um script Scilab

## Código Corrigir
```c
xi = input('Entre com o valor de xi: ');
h = input('Entre com o passo de cálculo: ');
disp('Entre com os coef da f. polinomial entre ');
vetor=input(' no formato [a0 a1 . . . an]:');
f = poly(vetor,'x','c');
disp('f(x)’, f)
flinha = derivat(f);
disp('f´(x)’, flinha);
vreal = horner(flinha,xi);
printf(“Val. real da der. em x = %f é %f\n",xi,vreal);
a = horner(f,xi-h)
b = horner(f,xi)
c = horner(f,xi+h)
diferenca = 'progressiva'
dfdt = (c - b)/h;
for i=1:3
    printf("Diferença %s :\n",diferenca);
    et = 100*abs((vreal - dfdt)/vreal) ; 
    printf(“Val. aprox. em x = %f é %f \n",xi,dfdt);
    printf("Com erro relativo de %f %%\n\n",et);
    if i==1 then
        diferenca =
        'regressiva';
        dfdt = (b - a)/h;
    elseif i==2 then
        diferenca = 'centrada';
        dfdt = (c - a)/(2*h);
    end
end
```
