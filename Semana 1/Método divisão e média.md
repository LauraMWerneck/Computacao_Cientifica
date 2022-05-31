## Código

```c
xn = 0 
x = 1 
erro=100 
n_sig = 4
es = 0.5*10^(2-n_sig); // condição de parada relativa %
a = input("Entre com um numero real positivo:")
while (erro >= es)do
xn = (x + a/x)/2
erro = abs((xn - x)/xn)*100
x = xn
printf(" e = %.6f \n",erro)
end
printf(" Valor exato = %.6f\nValor calculado = %.6f ",sqrt(a),xn);

```

## Console

Entre com um numero real positivo:6

e = 71.428571 

e = 34.246575 

e = 6.229443 

e = 0.194407 

e = 0.000189 

Valor exato = 2.449490

Valor calculado = 2.449490 
