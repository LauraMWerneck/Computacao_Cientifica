## Exemplo
Na Série de Taylor, se h for suficientemente pequeno,
poucos termos serão suficientes para se obter uma
estimativa adequada.
Com o auxílio de um script Scilab, use expansões em
série de Taylor com n = 0 até 6 para aproximar f(x) =
cos x em xi+1 = π/3 com base no valor de f(x) e suas
derivadas em xi = π/4
Note que h = π/3 – π/4
Calcule o erro relativo para cada expansão.

## Código
```c
x1 = %pi/3; x0 = %pi/4;
fx = cos(x0); i = 0; j = 0; vreal = cos(x1);
while i<=6 do
    e = abs((vreal-fx)/vreal)*100
    printf("Ordem = %d, f(x_i+1)= %.10f , erro = %.2e\n",i, fx, e);
    i=i+1;
    j=j+1;
    if j==1 then
        der = -sin(x0);
    elseif j==2 then
        der = -cos(x0); 
    elseif j==3 then
        der = sin(x0);
    elseif j==4 then
        der = cos(x0); 
        j = 0;
    end
    fx = fx + der*((x1-x0)^i)/factorial(i); 
end
```

## Console
Ordem = 0, f(x_i+1)= 0.7071067812 , erro = 4.14e+01

Ordem = 1, f(x_i+1)= 0.5219866588 , erro = 4.40e+00

Ordem = 2, f(x_i+1)= 0.4977544914 , erro = 4.49e-01

Ordem = 3, f(x_i+1)= 0.4998691469 , erro = 2.62e-02

Ordem = 4, f(x_i+1)= 0.5000075508 , erro = 1.51e-03

Ordem = 5, f(x_i+1)= 0.5000003040 , erro = 6.08e-05

Ordem = 6, f(x_i+1)= 0.4999999878 , erro = 2.44e-06
