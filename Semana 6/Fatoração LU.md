## Código

```c
function x=fatoralu(A, b)
    // Fatoração LU
    // function x = fatorlu(A, b)
    // onde x vetor solução
    // A é a matriz de coeficientes
    // b é o vetor de termos constantes
    //
    [m,n] = size(A);
    if m~=n then
        error('A deve ser uma matriz quadrada');
    end
    P = eye(n,n);       // Cria a matriz p -> matriz identidade quadrad n x n
    // eliminação progressiva
    for i = 1:n-1
        [maior, k]= max(abs(A(i:n,i)));
        l = i + k - 1;
        if l~=i then
            A([l,i],:)=A([i,l],:);
            P([l,i],:)=P([i,l],:);
        end
        for j = i+1:n
            A(j,i) = A(j,i)/A(i,i)        // Guarda os multiplicadores
            A(j,i+1:n)= A(j,i+1:n)-A(j,i)*A(i,i+1:n);    // For de maneira implicita
        end
    end
    //Mostra A
    disp('L/U', A)
    disp('P', P)
    // substituição progressiva
    b = P*b;          // Mantem b permutado
    d = zeros(n,1);   // Cria o vetor coluna d zerado
    d(1)=b(1);
    for i = 2:n
        for j = 1:i-1
            d(i)= d(i) + A(i,j)*d(j);
        end
        //d(i)= b(i)-(A(i,1:(i-1))*d(1:(i-1)));  // For implicito -> substitui as linhas 31,32,33,35
        d(i) = b(i) - d(i);
    end
    // substituição regressiva
    x = zeros(n,1);
    x(n)= d(n)/A(n,n);
    for i=n-1:-1:1
        x(i)=(d(i)-A(i,(i+1):n)*x((i+1):n))/A(i,i);
    end
endfunction


/*         Console
--> A=[2 -2 3; 1 2 3; -5 7 3] 
 A  = 

   2.  -2.   3.
   1.   2.   3.
  -5.   7.   3.

--> b=[1;-2;4] 
 b  = 

   1.
  -2.
   4.

--> x=A\b                          //Modo alternativo de achar x
 x  = 

  -2.0526316
  -1.2631579
   0.8596491

--> [L, U, P] = lu(A)              //Função do proprio scilab para achar as matrizes
 L  = 

   1.    0.          0.
  -0.2   1.          0.
  -0.4   0.2352941   1.
 U  = 

  -5.   7.    3.       
   0.   3.4   3.6      
   0.   0.    3.3529412
 P  = 

   0.   0.   1.
   0.   1.   0.
   1.   0.   0.

-->  x=fatoralu(A, b)              //Comando da nossa função criada no scinotes

  "L/U"

  -5.    7.          3.       
  -0.2   3.4         3.6      
  -0.4   0.2352941   3.3529412

  "P"

   0.   0.   1.
   0.   1.   0.
   1.   0.   0.
 x  = 

  -2.0526316
  -1.2631579
   0.8596491
*/

```
