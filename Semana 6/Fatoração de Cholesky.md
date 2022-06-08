## Código
```c
function x=cholesky(A, b)
    // Fatoração de Cholesky
    // function x = cholesly(A, b)
    // onde x vetor solução
    // A é a matriz de coeficientes
    // b é vetor de termos independentes
    soma = 0;
    [m,n] = size(A);
    if m~=n then
        error('A deve ser uma matriz quadrada');
    end
    m = max(size(b))    //length(b)
    if m~=n then
        error('Vetor b com número incorreto de linhas.');
    end
    //Obtenção da Matriz U Fatoração de Cholesky
    for i = 1:n
        for j = i:n
            if i == j then
                for k=1:(i-1)
                    soma = soma + A(k,i)^2;
                end
                A(i,i)= sqrt(A(i,i)- soma);
                soma = 0;
            else
                for k=1:(i-1)
                    soma = soma + A(k,i)*A(k,j);
                end
                A(i,j)= (A(i,j)-soma)/A(i,i);
                soma = 0;
            end
        end
    end
    disp('U',A);
    // substituição progressiva
    for i = 1:n
        for k=1:(i-1)
            soma = soma + A(k,i)*x(k);
        end
        x(i)= (b(i)-soma)/A(i,i);
        soma = 0;
    end
    disp('d',x);
    // substituição regressiva
    x(n)= x(n)/A(n,n);
    for i=n-1:-1:1
        x(i)=(x(i)-A(i,(i+1):n)*x((i+1):n))/A(i,i);
    end
endfunction

/*         Console

--> A = [1.5 -0.7 2; -0.7 1 -1; 2 -1 3]
 A  = 

   1.5  -0.7   2.
  -0.7   1.   -1.
   2.   -1.    3.

-->  b = [0.5;-1;0.5]
 b  = 

   0.5
  -1.
   0.5
   
--> x=cholesky(A, b)

  "U"

   1.2247449  -0.5715476   1.6329932
  -0.7         0.8205689  -0.0812444
   2.         -1.          0.5716053

  "d"

   0.4082483
  -0.9343111
  -0.4243737
 x  = 

   0.7575758
  -1.2121212
  -0.7424242*/

```
