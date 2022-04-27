## Exemplo

Use o método da secante modificado para estimar a raiz de

𝑓(𝑥) = cos(𝑥) − 𝑥∙𝑒^(𝑥)

no intervalo −2 ≤ 𝑥 ≤ 0, utilizando com critério de parada 𝜀𝑠 = 1 %.

## Código

```C

function [raiz, iter]=sec_mod(funcao, dxi, es, maxi)
    // Cálculo das raizes pelo método da secante modificado
    // function [raiz,iter]=new_raphson(funcao, derivada, x0, es, it)
    // onde raiz é a raiz procurada de funcao
    // iter é o n. de iterações realizadas para o erro especificado
    // funcao é a função de entrada literal em x
    // dxi é a perturbação em torno de x e é opcional
    // es é o criterio de parada que é opcional
    // maxi é o numero maximo de iterações e é opcional
    // A cond. inicial x0 é escolhida com auxilio de um gráfico
    // Exemplo de chamada:
    //
    // fun = ‘log(x) + x‘
    // [raiz,iter]=new_raphson(fun, 0.001, 0.0001,50)
    //
    // Construção do gráfico da função
    a = input("Entre com o limite inferior de x a = ");
    b = input("Entre com o limite superior de x b = ");
    x = linspace(a,b,100);
    f = evstr(funcao)
    plot2d(x,f);
    xgrid;
    // escolha do valor inicial
    x0 = input("Entre com o valor inicial x0 = ");
    i = 0; x = x0;
    // se dxi não for estabelecido, adota-se 1e-6
    if argn(2) < 2 then
        dxi = 1e-6;
    end
    // se es nao foi estabelecido usa 0.0001%
    if argn(2) < 3 then
        es = 0.0001;
    end
    // se maxi nao foi estabelecido usa 50
    if argn(2) < 4 then
        maxi = 50;
    end
    printf("Iter\tRaiz\t\terro aprox. %% \n");
    // inicio do processo iterativo
    while 1 do
        fxi = evstr(funcao);
        p = x*dxi // calcula a perturbação
        x = x + p; // soma a perturbação
        fdxi = evstr(funcao);
        x = x - p // desconta a perturbação
        xi = x - fxi*p/(fdxi-fxi);
        i= i+1;
        if xi ~=0 then // xi não pode ser zero
            ea = abs((xi - x)/xi)*100;
        end
        printf("%d\t%.10f\t%f\n",i,xi,ea);
        if ea < es | i >= maxi then
            break;
        end
        x = xi;
    end
    if i == maxi then
        raiz = 'divergiu';
    else
        raiz = xi;
        printf("\nf(%f) = %f\n",xi,fxi);
    end
    iter = i;
endfunction

```

## Aplicação

--> fun='cos(x)-x.*exp(x)'
 OBS: Para ser ponto a ponto precisa ser .* para a multiplicação, porque x e exp(x) são dois vetores

--> [raiz, iter]=sec_mod(fun)
Entre com o limite inferior de x a = -2

Entre com o limite superior de x b = 0

Entre com o valor inicial x0 = -2

Iter	Raiz		erro aprox. % 

1	-1.8607392564	7.484162

2	-1.8639939047	0.174606

3	-1.8639951924	0.000069


f(-1.863995) = 0.000001

 iter  = 3

 raiz  = -1.8639952
