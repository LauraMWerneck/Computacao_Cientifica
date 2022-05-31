## Código

```c
function [fx, term] = series(fun, x, n_sig)
    //
    // Cálculo de funções com serie de potências
    // function [fx,term]=series(funcao, x, n_sig)
    // onde fx é o valor da função e x
    // term é o número de termos usados para o erro
    //especificado
    // fun é a função de entrada literal em x e n
    // x é o número no qual se deseja obter o valor da função
    // n é o numero do termo (começando em 0)
    // n_sig é o numero de alg. significativos da resposta -
    // opcional
    // Exemplo de chamada:
    // exec('path\series.sci',-1)
    // fun ='(-1)^(n)*x^(2*n)/factorial(2*n)'
    // [fx,term]=series(fun, %pi/3, 3)
    if argn(2) < 3 then
        n_sig = 3;
    end
    //
    // argn fornece os números de parâmetros de entrada (argn(2)) e
    // saída (argn(1)) passados à função quando esta é chamada. Aqui
    // está sendo usada para lidar com parâmetros opcionais.
    //
    es = 0.5*10^(2-n_sig); // condição de parada relativa %
    fx_old = 0; fx = 0;n = 0; vreal=cos(x);
    printf("Termo fx et %% erro %%\n");
    while 1 do 
        fx = fx + evstr(fun);
        erro = abs((fx - fx_old)/fx)*100;
        errot = abs((vreal - fx)/vreal)*100;
        printf("%-8d %10.6f %10.6f %10.6f\n", n+1, fx, errot, erro);
        if(erro<= es) then
            break;
        end
        fx_old = fx;
        n = n +1;
    end
    term = n+1;
endfunction

```

## Console
--> f = 'cos(x)'
 f  =  "cos(x)"

--> series(f, 0, 4)

Termo fx et % erro %

1           1.000000   0.000000 100.000000

2           2.000000 100.000000  50.000000

3           3.000000 200.000000  33.333333

4           4.000000 300.000000  25.000000

5           5.000000 400.000000  20.000000

6           6.000000 500.000000  16.666667

7           7.000000 600.000000  14.285714

8           8.000000 700.000000  12.500000

9           9.000000 800.000000  11.111111

10         10.000000 900.000000  10.000000

11         11.000000 1000.000000   9.090909

12         12.000000 1100.000000   8.333333

13         13.000000 1200.000000   7.692308

14         14.000000 1300.000000   7.142857

15         15.000000 1400.000000   6.666667

16         16.000000 1500.000000   6.250000

17         17.000000 1600.000000   5.882353

