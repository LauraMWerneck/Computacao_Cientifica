## Problema:

Use a abordagem gráfica com o Scilab e faça uma estimativa da massa que deve ter um saltador de bungee jumping para que a sua velocidade ultrapasse 
36 m/s após 4 s de queda.
▪ Considere o coeficiente de arraste 0,25 kg/m e a aceleração da gravidade g = 9,81 m/s2

## Código:
```c
/* Use a abordagem gráfica com o Scilab e faça uma estimativa da 
massa que deve ter um saltador de bungee jumping para que a sua 
velocidade ultrapasse 36 m/s após 4 s de queda.
▪ Considere o coeficiente de arraste 0,25 kg/m e a aceleração da 
gravidade g = 9,81 m/s2. */

CD = 0.25 
G = 9.81 
v =36     
t = 4
m = linspace(50,200,100)  // Cria o eixo da massa, vetor de pontos entre 50 e 200
fm = sqrt(G*m/CD).*tanh(sqrt(G*CD./m)*t) - v
xlabel('Massa m')   // Nomeia o eixo x
ylabel('f(m)')      // Nomeia o eixo y
plot2d(m,fm,style=[color('blue4')])  // plot2d (x,y,style(cordo grafico))
xgrid
```


