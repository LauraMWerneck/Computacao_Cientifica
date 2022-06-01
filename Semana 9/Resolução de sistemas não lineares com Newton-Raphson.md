## Código

```c
function [x, iter]=newraph_n(fun, jac, es, maxi)
    // Res. de sist. não lineares por Newton-Raphson
    // function [x,iter]=new_raphson(fun, jac, es, it)
    // onde x é o vetor solução procurado pela funcao
    // iter é o n. de iterações realizadas para o erro especificado
    // fun é a função de entrada literal em {x}
    // jac é a matriz Jacobiana do sistema
    // es é o criterio de parada que é opcional
    // maxi é o numero maximo de iterações
    // Exemplo de chamada:
    // exec('path\newraph_n.sci',-1)
    // fun = '[(x(1))^2+x(1)*x(2)-10 ; x(2)+3*x(1)*x(2)^2-57]'   -> OBS: tudo tem que ser fornescido na forma literal, com '...'
    // jac = '[2*x(1)+x(2) x(1); 3*x(2)^2 1+6*x(1)*x(2)]'
    // [x,iter]=newraph_n(fun,jac,es,maxi)
    // escolha do valor inicial
    x0 = input("Entre com as aprox. inicial x0 = ");          // -> OBS: é um vetor coluna, entao tem que enrtrar com x0 = [a ; b ; c]
    i = 0; x = x0; ea=100;
    // se es não foi estabelecido usa 0.0001%
    if argn(2) < 3 then
        es = 0.0001;
    end
    // se maxi não foi estabelecido usa 50%
    if argn(2) < 4 then
        maxi = 50;
    end
    // inicio do processo iterativo
    while ea > es & i < maxi do
        f = evstr(fun);
        J = evstr(jac);
        y = J\f;                                     // -> É possivel utilizar outras funções já vistas, como gaus(J, f) e fatoraçãolu
        xi = x - y;
        i= i+1;
        if xi ~=0 then // xi não pode ser zero
            ea = max(abs(y./xi))*100;
        end
        x = xi;
    end
    if i == maxi then
        raiz = 'divergiu';
    else
        raiz = xi;
    end
    iter = i;
endfunction

```

## Console

--> fun = '[exp(x(1))-x(2)-1 ; x(1)-log(x(1))-x(2)^2/2]'
 fun  = 

 [exp(x(1))-x(2)-1 ; x(1)-log(x(1))-x(2)^2/2]


--> jac = '[exp(x(1)) -1 ; 1-1/x(1) -x(2)]'
 jac  = 

 [exp(x(1)) -1 ; 1-1/x(1) -x(2)]


--> [x, iter]=newraph_n(fun, jac)
Entre com as aprox. inicial x0 = [1;2]

 iter  = 

   4.

 x  = 

   0.8835233
   
   1.419409
