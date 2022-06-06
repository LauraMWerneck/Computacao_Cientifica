## Código
```c
/*Use a eliminação de Gauss com pivotamento para resolver o sistema:
3 𝑥1 + 𝑥2 + 2 𝑥3 = 2
6 𝑥1 + 3 𝑥2 − 𝑥3 = −2
2 𝑥1 + 3 𝑥2 + 𝑥3 = 1
*/

function x=gaussp(A, b)
    // Eliminação de Gauss com pivotamento
    // onde x vetor solução
    // A é a matriz de coeficientes
    // b é o vetor de termos constantes
    // exec('path\gaussp.sci',-1)
    // x=gausp(A, b)
    [m,n] = size(A);
    if m~=n then
        error('A deve ser uma matriz quadrada.');
    end
    n=length(b)
    if m~=n then
        error('Dimensão incorreta de b');
    end
    nb = n + 1;
    A = [A b]; // pbtendo a matriz aumentada
    // eliminação progressiva
    for i=1:n-1
        // pivotamento parcial
        // encontrar o maior coef. da coluna abaixo do pivo
        [maior,k]=max(abs(A(i:n,i)));
        l = i + k - 1;
        if l~=i then
            A([l,i],:)=A([i,l],:);
        end
        for j=i+1:n
            A(j,i) = A(j,i)/A(i,i);
            A(j,i+1:nb)=A(j,i+1:nb)-A(j,i)*A(i,i+1:nb);
            disp(A);
        end
    end
    // substituição regressiva
    x = zeros(n,1);
    x(n)= A(n,nb)/A(n,n);
    for i=n-1:-1:1
        x(i) = (A(i,nb) - A(i,(i+1):n) * x((i+1):n)) /A(i,i);
    end
endfunction


/*     Console
--> A = [3 1 2; 6 3 -1; 2 3 1]
 A  = 

   3.   1.   2.
   6.   3.  -1.
   2.   3.   1.

--> b = [2;-2;1]
 b  = 

   2.
  -2.
   1.

--> x=gaussp(A, b)

   6.    3.   -1.   -2.
   0.5  -0.5   2.5   3.
   2.    3.    1.    1.

         column 1 to 3
   6.          3.   -1.       
   0.5        -0.5   2.5      
   0.3333333   2.    1.3333333
         column 4
  -2.       
   3.       
   1.6666667

         column 1 to 3
   6.          3.    -1.       
   0.3333333   2.     1.3333333
   0.5        -0.25   2.8333333
         column 4
  -2.       
   1.6666667
   3.4166667
 x  = 

  -0.1470588
   0.0294118
   1.2058824
*/
```
