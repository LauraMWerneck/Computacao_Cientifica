## Código

```C
function [raiz, iter]=new_raphson(funcao, derivada, es, maxi)
    // Cálculo das raizes por Newton-Raphson
    // onde raiz é a raiz procurada de funcao
    // iter é o número de iterações realizadas para o erro especificado
    // funcao é a função de entrada literal em x
    // derivada é a derivada da função de entrada literal em x
    // es é o criterio de parada/tolerância que é opcional
    // maxi é o numero maximo de iterações
    // A condição inicial x0 é escolhida com o auxilio de um grafico
    // Exemplo de chamada:
    //
    // fun = ‘log(x) + x‘
    // dxdt = ‘(1/x) + 1‘
    // OBS log x = ln x     log10=~logx
    // [raiz,iter]=new_raphson(fun, dxdt, 0.0001,50)
    //
    // Construção do gráfico da função
    a = input("Entre com o limite inferior de x a = ");
    b = input("Entre com o limite superior de x b = ");
    x = linspace(a,b,100); //Cria entre a e b uma variavél x(vetor) com um intervalo de 100 pontos
    f = evstr(funcao) 
    plot2d(x,f);
    xgrid;
    // escolha do valor inicial
    x0 = input("Entre com o valor inicial x0 = "); //A partir do gráfico escolhe o valor inicial adequado 
    i = 0; x = x0;
    // se es nao foi estabelecido usa 0.0001%
    if argn(2) < 3 then
        es = 0.0001;
    end
    // se maxi nao foi estabelecido usa 50
    if argn(2) < 4 then
        maxi = 50;
    end
    printf("Iter\tRaiz \terro aproximado %% \n"); //Cabeçalho
    // inicio do processo iterativo
    while 1 do
        fxi = evstr(funcao); //Função para x0
        dxi = evstr(derivada); //Derivada para x0
        if dxi == 0
            error('Derivada igual a zero, o processo divergiu');
        end
        xi = x - (fxi/dxi);  //Se a derivada não deu 0
        i= i+1;
        if xi ~=0 then // xi não pode ser zero
            ea = abs((xi - x)/xi)*100; //Erro aproximado
        end
        printf("%d\t%.10f\t%f\n",i,xi,ea);
        if ea < es | i >= maxi then  //Se o erro for menor que a tolerância ou o número de interações for maior ou igual ao máximo de iterações sai do laço infinito
            break;
        end
        x = xi;
    end
    if i == maxi then  //Se o i for igual ao máximo sai do laço sem encontrar a raiz
        raiz = 'divergiu';
    else
        raiz = xi;
        printf("\nf(%f) = %f\n",xi,fxi);
    end
    iter = i;
endfunction
```

## Aplicação

--> fun='exp(-x)-x'


--> der='-exp(-x)-1'


--> [raiz, iter]=new_raphson(fun, der)
Entre com o limite inferior de x a = 0

Entre com o limite superior de x b = 1

Entre com o valor inicial x0 = 0.2

Iter	Raiz 	erro aproximado % 
1	0.5401992032	62.976621
2	0.5670108503	4.728595
3	0.5671432872	0.023352
4	0.5671432904	0.000001

f(0.567143) = 0.000000
 iter  = 4

 raiz  = 0.5671433
