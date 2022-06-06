## Código

```c
/*Use a eliminação de Gauss ingênua para resolver o sistema:

6 x1 + x2 + 2 x3 = 12

4 x1 + 3 x2 − x3 = −12

x1 + 2 x2 + x3 = 8*/

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

/*      Cosole

--> A=[6 1 2; 4 3 -1; 1 2 1]
 A  = 

   6.   1.   2.
   4.   3.  -1.
   1.   2.   1.

--> b=[12;-12;8]
 b  = 

   12.
  -12.
   8.

--> x=A\b
 x  = 

  -0.9142857
   0.1142857
   8.6857143

--> x=gaussi(A, b)

   6.          1.          2.          12.
   0.6666667   2.3333333  -2.3333333  -20.
   1.          2.          1.          8. 

   6.          1.          2.          12.
   0.6666667   2.3333333  -2.3333333  -20.
   0.1666667   1.8333333   0.6666667   6. 

   6.          1.          2.          12.      
   0.6666667   2.3333333  -2.3333333  -20.      
   0.1666667   0.7857143   2.5         21.714286
 x  = 

  -0.9142857
   0.1142857
   8.6857143
*/
```
