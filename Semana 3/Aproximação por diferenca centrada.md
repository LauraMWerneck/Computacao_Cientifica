## Código:

```c
/* Use uma aproximação por diferença centrada de O(h2) para estimar a 
derivada primeira da função a seguir em x = 0,5.
f(x) = – 0,1x4 – 0,15x3 – 0,5x2 – 0,25x +1,2
▪ Utilizando o Scilab, faça o cálculo iniciando com h = 2 e divida 
progressivamente o tamanho do passo por um fator 8 para demonstrar 
que o erro de arredondamento torna-se dominante à medida que o tamanho 
do passo é reduzido.
▪ Com o auxílio de um gráfico erro total x h, relacione os resultados 
obtidos com a equação de hotm.*/

/* Diferença centrada -> f'(xi) = f(xi+h)-f(xi-h)/2h */

clear; //Limpa a memória
j = 1;
xi = input('Entre com o valor de xi: ');
h = input('Entre com o passo de cálculo inicial: ');
disp('Entre com os coef da f. polinomial entre ')
vetor = input(' no formato [a0 a1 . . . an] : ');
f = poly(vetor,'x','c'); //Cria polinomio x
disp('f(x)',f);          //mostra na tela
flinha = derivat(f);     //funcao que faz a derivada
disp('f´(x)',flinha);
vreal = horner(flinha,xi); //calcula o valor exato da derivada, valor real
printf("O valor real da derivada em x = %f é %f\n",xi,vreal);
printf(" tamanho do passo | diferenca finita | erro total\n ");
while h >= 1.0D-10  //passo de calculo
    H(j) = h;       // guarda passo de calculo em um vetor
    dfdt(j) = (horner(f,xi+h)-horner(f,xi-h))/(2*h); //diferenca centrada
    e(j) = 100*abs((vreal - dfdt(j))/vreal);         //calculo do erro em valor absoluto
    printf("%16.10f | %16.10f | %16.10f\n ",h,dfdt(j),e(j));
    h = h/8; // divisao do passo de calculo
    j=j+1;   // proximo elemento do vetor 
end
xlabel('Tamanho do passo');
ylabel('Erro total');
plot2d(H,e,style=[color('blue4')],logflag='ll'); //vetor com erro em funcao de um vetor com passo de calculo, e os dois eixos vao ser logaritimos
xgrid;
f2linha = derivat(flinha);  //derivada segunda
f3linha = derivat(f2linha); // derivada terceira
M = abs(horner(f3linha,xi));
disp('M', M,);
hotm = (3*%eps/M)^(1/3.); //avalia o passo otimo
disp('hotm',hotm);

/* Console

Entre com o valor de xi: 0.5

Entre com o passo de cálculo inicial: 2

  "Entre com os coef da f. polinomial entre "
 no formato [a0 a1 . . . an] : [1.2 -0.25 -0.5 -0.15 -0.1]


  "f(x)" = 1.2 -0.25x -0.5x² -0.15x³ -0.1x⁴

  "f´(x)" = -0.25 -x -0.45x² -0.4x³
  
O valor real da derivada em x = 0.500000 é -0.912500

 tamanho do passo | diferenca finita | erro total
     2.0000000000 |    -2.3125000000 |   153.4246575342
     0.2500000000 |    -0.9343750000 |     2.3972602740
     0.0312500000 |    -0.9128417969 |     0.0374571918
     0.0039062500 |    -0.9125053406 |     0.0005852686
     0.0004882813 |    -0.9125000834 |     0.0000091448
     0.0000610352 |    -0.9125000013 |     0.0000001428
     0.0000076294 |    -0.9125000000 |     0.0000000022
     0.0000009537 |    -0.9125000000 |     0.0000000026
     0.0000001192 |    -0.9125000001 |     0.0000000102
     0.0000000149 |    -0.9125000015 |     0.0000001633
     0.0000000019 |    -0.9124999940 |     0.0000006532
     0.0000000002 |    -0.9124999046 |     0.0000104512
 
  "M" = 2.1

  "hotm" = 0.0000068*/

```
