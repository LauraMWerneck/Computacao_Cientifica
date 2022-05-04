## Exemplo 
Use a eliminação de Gauss ingênua para resolver o sistema:

6 x1 + x2 + 2 x3 = 12

4 x1 + 3 x2 − x3 = −12

x1 + 2 x2 + x3 = 8

## Código

```c
function x=gaussi(A, b)
    // Eliminação de Gauss Ingênua
    // onde x vetor solução
    // A é a matriz de coeficientes, A é uma matriz quadrada
    // b é o vetor de termos constantes, b é um vetor coluna 
    // exec('path\gaussi.sci',-1)
    // x=gaussi(A, b)
    [m,n] = size(A); // Vê se a matriz é quadrada e se m=~n enão a matriz não é quadrada e não roda 
    if m~=n then
        error('A deve ser uma matriz quadrada.');
    end
    n=length(b)
    if m~=n then
        error('Dimensão incorreta de b');
    end
    nb = n + 1; // Número de colunas da matriz aumentada 
    A = [A b]; // obtendo a matriz aumentada A
    // eliminação progressiva
    for i = 1:n-1
        for j = i+1:n
            A(j,i) = A(j,i)/A(i,i);
            // for k = i+1:nb
            // A(j,k)= A(j,k)-A(j,i)*A(i,k);
            // end
            A(j,i+1:nb)= A(j,i+1:nb)-A(j,i)*A(i,i+1:nb); // For implícito do scilab (k vai de i+1 até nb)
            disp(A) // Imprime a matriz A
        end
    end
    // substituição regressiva
    x = zeros(n,1);  // Cria o vetor de 1 coluna com n linhas, porque o x tem que ser um vetor coluna
    x(n)= A(n,nb)/A(n,n);
    for i=n-1:-1:1
        // for j=i+1:n
        // x(i) = x(i) + A(i,j) * x(j);
        // end
        // x(i) = (A(i,nb)-x(i)) /A(i,i);
        // para resolver a equação em uma única linha
        // usa-se um for implícito para o somatório
        x(i) = (A(i,nb) - A(i,(i+1):n) * x((i+1):n)) /A(i,i);
    end
endfunction

```

## Aplicação (OBS: Não está usando os valores do exemplo)

--> A=[1 2 3; 3 3 1; 2 3 1]
 A  = 

   1.   2.   3.
   3.   3.   1.
   2.   3.   1.


--> b=[1;2;1]
 b  = 

   1.
   2.
   1.


--> x=A\b
 x  = 

   1.
  -0.4285714
   0.2857143


--> x=gaussi(A, b)

   1.   2.   3.   1.
   3.  -3.  -8.  -1.
   2.   3.   1.   1.

   1.   2.   3.   1.
   3.  -3.  -8.  -1.
   2.  -1.  -5.  -1.

   1.   2.          3.          1.       
   3.  -3.         -8.         -1.       
   2.   0.3333333  -2.3333333  -0.6666667
 x  = 

   1.
  -0.4285714
   0.2857143

