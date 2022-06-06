## Código 
```c
//A partir da função Scilab do Método da Bissecção, criar uma
//função Scilab que implemente o método da Falsa Posição e utilizála 
//para resolver o exercício */

function [raiz, iter]=falsapos(funcao, xl, xu, es)
    // Cálculo das raizes pelo processo da falsa posição
    // function [raiz,iter]=falsapos(funcao, xl, xu, es)
    // onde raiz é a raiz procurada de funcao
    // iter é o num de iterações para o erro especificado
    // funcao é a função de entrada literal em x
    // xl é o limite inferior do intervalo de busca
    // xu é o limite superior do intervalo de busca
    // es é o criterio de parada que é opcional
    x = xu; fu = evstr(funcao);
    x = xl; fl = evstr(funcao);
    if (fu*fl >= 0) then
        error("Nenhuma raiz no intervalo dado.")
    end
    i = 0; ea=100; xr_novo = xl;
    // se es nao foi estabelecido usa 0.0001%
    if argn(2) < 4 then
        es = 0.0001;
    end
    // inicio do processo iterativo
    printf("Iter\tErro aprox.%%\tRaiz\t\txl\t\txu\n");
    while ea > es do
        xr_velho = xr_novo;
        xr_novo = xu + fu*(xl-xu)/(fu-fl);
        if xr_novo ~=0 then // xr_novo não pode ser zero
            ea = abs((xr_novo - xr_velho)/xr_novo)*100;
        end
        i=i+1;
        printf("%d\t%f\t%f\t%f\t%f\n",i,ea,xr_novo,xl,xu);
        x=xr_novo; fr = evstr(funcao);
        x = xl;
        fl = evstr(funcao);
        if(fl*fr < 0) then
            xu = xr_novo;
            x = xu;
            fu = evstr(funcao);
        elseif(fl*fr > 0) then
            xl = xr_novo;
            x = xl;
            fl = evstr(funcao);
        else
            break;
        end
    end
    raiz = xr_novo;
    iter = i;
endfunction

/*                  Console
--> eo = 8.9d-12; F = 1.25; q = 2d-5; r = 0.85;

--> f = '(1/(4*%pi*eo))*(q^2*x)./((x.^2+r^2)^(3/2))-F'

--> [raiz, iter]=falsapos(f, 0, 0.4)
Iter	Erro aprox.%	Raiz		xl		xu
1	100.000000	0.289749	0.000000	0.400000
2	14.472792	0.253116	0.000000	0.289749
3	3.816314	0.243811	0.000000	0.253116
4	0.888275	0.241665	0.000000	0.243811
5	0.200248	0.241182	0.000000	0.241665
6	0.044810	0.241074	0.000000	0.241182
7	0.010011	0.241050	0.000000	0.241074
8	0.002236	0.241044	0.000000	0.241050
9	0.000499	0.241043	0.000000	0.241044
10	0.000111	0.241043	0.000000	0.241043
11	0.000025	0.241043	0.000000	0.241043

raiz  = 0.2410428

iter  = 11.*/

```
