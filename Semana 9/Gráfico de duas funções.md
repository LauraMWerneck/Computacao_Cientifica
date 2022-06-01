## Código

```c
function z=F1(x, y)
    z = exp(x)-y-1;
endfunction
function w=F2(x, y)
    w = x-log(x)-(y^2)/2;
endfunction
// Traça as linhas (x,y) resolvendo uma Função(x,y)=0
// Desenha no intervalo [-2,2] x [-3.3]]
plotimplicit(F1, -1:0.1:1, -2:0.1:2)           //  -> Eixo x de -1 a 1, e y de -2 a 2 
plotimplicit(F2, -1:0.1:1, -2:0.1:2,'r')       //  -> 'r' representa que quer vermelho o grafico da funcao 2 
// pos - posição da legenda
// boxed - com ou sem caixa
legend(['$\text e^x-y-1$';'$\text x-log(x)-(y^2)/2$'],pos=-5,boxed=%f);   // -> Imprime na forma de expressoes
gce().font_size = 4;                                                      // -> Função para aumentar a fonte(letra) do grafico 
xgrid

```

## Console
