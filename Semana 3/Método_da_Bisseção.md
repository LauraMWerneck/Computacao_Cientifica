## Código

```C
/*Use o método da bisseção para obter a massa que deve ter um
saltador de bungee jumping para que a sua velocidade ultrapasse 
36 m/s após 4 s de queda.
• Considere o coeficiente de arraste 0,25 kg/m e a aceleração da 
gravidade g = 9,81 m/s2.
• Pare o processo quando 𝐸𝑎 < 0,1.
• Registre cada iteração no papel, utilizando o auxílio do console 
do Scilab.*/

function [raiz, i] = bissecao(funcao, xl, xu, es)
    // Cálculo das raizes pelo processo da bisseção
    // function [raiz,iter] = bissecao(funcao, xl, xu, es)
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
    x = xu; fu = evstr(funcao)  // avaliação de expressões
    x = xl; fl = evstr(funcao)
    if (fu*fl >= 0) then
        error('Nenhuma raiz no intervalo dado')
    end
    i = 0 
    ea = 100 //erro aproximado em 100%
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
        if xr_novo ~= 0 then // xr_novo não pode ser zero
            ea = abs((xr_novo - xr_velho)/xr_novo)*100
        end
        i = i+1;
        printf("%d\t%f\t%f\t%f\t%f\n",i,ea,xr_novo,xl,xu)
        x = xr_novo; fr = evstr(funcao)
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



/* Console
--> CD = 0.25

--> G = 9.81

--> v = 36

--> t = 4

--> fun = 'sqrt(G*x/CD).*tanh(sqrt(G*CD/x)*t) - v'

--> [raiz, i]=bissecao(fun, 100, 200)

Iter	Erro aprox.%	Raiz		xl		xu
1	33.333333	150.000000	100.000000	200.000000
2	20.000000	125.000000	100.000000	150.000000
3	9.090909	137.500000	125.000000	150.000000
4	4.347826	143.750000	137.500000	150.000000
5	2.222222	140.625000	137.500000	143.750000
6	1.098901	142.187500	140.625000	143.750000
7	0.546448	142.968750	142.187500	143.750000
8	0.273973	142.578125	142.187500	142.968750
9	0.136799	142.773438	142.578125	142.968750
10	0.068446	142.675781	142.578125	142.773438
11	0.034211	142.724609	142.675781	142.773438
12	0.017103	142.749023	142.724609	142.773438
13	0.008552	142.736816	142.724609	142.749023
14	0.004276	142.742920	142.736816	142.749023
15	0.002138	142.739868	142.736816	142.742920
16	0.001069	142.738342	142.736816	142.739868
17	0.000535	142.737579	142.736816	142.738342
18	0.000267	142.737961	142.737579	142.738342
19	0.000134	142.737770	142.737579	142.737961
20	0.000067	142.737675	142.737579	142.737770

 raiz  = 142.73767
 
 i  = 20.*/

```


## Aplicação

Usando a função do exemplo 2

--> exec('C:\Users\Aluno\efgrre.sce', -1)

--> CD = 0.25    


--> G = 9.81


--> v =36


--> t = 4


--> fum = 'sqrt(G*x/CD).*tanh(sqrt(G*CD/x)*t) - v'


--> [raiz, i]=bissecao(fun, 100, 200)
Iter	Erro aprox.%	Raiz		xl		xu
1	33.333333	150.000000	100.000000	200.000000
2	20.000000	125.000000	100.000000	150.000000
3	9.090909	137.500000	125.000000	150.000000
4	4.347826	143.750000	137.500000	150.000000
5	2.222222	140.625000	137.500000	143.750000
6	1.098901	142.187500	140.625000	143.750000
7	0.546448	142.968750	142.187500	143.750000
8	0.273973	142.578125	142.187500	142.968750
9	0.136799	142.773438	142.578125	142.968750
10	0.068446	142.675781	142.578125	142.773438
11	0.034211	142.724609	142.675781	142.773438
12	0.017103	142.749023	142.724609	142.773438
13	0.008552	142.736816	142.724609	142.749023
14	0.004276	142.742920	142.736816	142.749023
15	0.002138	142.739868	142.736816	142.742920
16	0.001069	142.738342	142.736816	142.739868
17	0.000535	142.737579	142.736816	142.738342
18	0.000267	142.737961	142.737579	142.738342
19	0.000134	142.737770	142.737579	142.737961
20	0.000067	142.737675	142.737579	142.737770

 i  = 20

 raiz  = 142.73767

