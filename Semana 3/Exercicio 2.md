## Função

```C
function [raiz, i]=bissecao(funcao, xl, xu, es)
    // Cálculo das raizes pelo processo da bisseção
    // function [raiz,iter]=bissecao(funcao, xl, xu, es)
    // onde raiz é a raiz procurada de funcao
    // i é o num de iterações para o erro especificado
    // funcao é a função de entrada literal em x
    // xl é o limite inferior do intervalo de busca
    // xu é o limite superior do intervalo de busca
    // es é o criterio de parada que é opcional
    // Exemplo de chamada:
    // exec('path\ bissecao.sci',-1)
    // fun = 'log(x) + x'
    // [raiz,iter]=bissecao(fun, 0.1, 2, 0.1)
    // preparação
    x = xu; fu = evstr(funcao)
    x = xl; fl = evstr(funcao)
    if (fu*fl >= 0) then
        error('Nenhuma raiz no intervalo dado')
    end
    i = 0 
    ea=100 //erro aproximado em 100%
    xr_novo = xl
    // se es nao foi estabelecido usa 0.0001%
    if argn(2) < 4 then  
        es = 0.0001
    end
    // inicio do processo iterativo
    printf("Iter\tErro aprox.%%\tRaiz\t\txl\t\txu\n");
    while ea > es do
        xr_velho = xr_novo
        xr_novo = (xu + xl)/2
        if xr_novo ~=0 then // xr_novo não pode ser zero
            ea = abs((xr_novo - xr_velho)/xr_novo)*100
        end
        i=i+1;
        printf("%d\t%f\t%f\t%f\t%f\n",i,ea,xr_novo,xl,xu)
        x=xr_novo; fr = evstr(funcao)
        x = xl; fl = evstr(funcao)
        if(fl*fr < 0) then
            xu = xr_novo
        elseif(fl*fr > 0) then
            xl = xr_novo
        else
            break
        end
    end
    raiz = xr_novo
endfunction


```

## Aplicação

--> fun = 'cos(x) - x*exp(x)'
 fun  = cos(x) - x*exp(x)
 
--> [raiz, i]=bissecao(fun, -2, 0, 0.01)
Iter	Erro aprox.%	Raiz		xl		xu

1	100.000000	-1.000000	-2.000000	0.000000

2	33.333333	-1.500000	-2.000000	-1.000000

3	14.285714	-1.750000	-2.000000	-1.500000

4	6.666667	-1.875000	-2.000000	-1.750000

5	3.448276	-1.812500	-1.875000	-1.750000

6	1.694915	-1.843750	-1.875000	-1.812500

7	0.840336	-1.859375	-1.875000	-1.843750

8	0.418410	-1.867188	-1.875000	-1.859375

9	0.209644	-1.863281	-1.867188	-1.859375

10	0.104712	-1.865234	-1.867188	-1.863281

11	0.052383	-1.864258	-1.865234	-1.863281

12	0.026199	-1.863770	-1.864258	-1.863281

13	0.013098	-1.864014	-1.864258	-1.863770

14	0.006549	-1.863892	-1.864014	-1.863770

 i  = 14.

 raiz  = -1.8638916
