## Código
```c
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
```

## Aplicação

--> A=[1 2 3; 3 3 1; 2 3 1]
 A  = 

   1   2   3
   
   3   3   1
   
   2   3   1


--> b=[1;2;1]
 b  = 

   1
   
   2
   
   1


--> x=gaussp(A, b)

   3.          3.   1.          2.       
   0.3333333   1.   2.6666667   0.3333333
   2.          3.   1.          1.       

   3.          3.   1.          2.       
   0.3333333   1.   2.6666667   0.3333333
   0.6666667   1.   0.3333333  -0.3333333

   3.          3.   1.          2.       
   0.3333333   1.   2.6666667   0.3333333
   0.6666667   1.  -2.3333333  -0.6666667
 x  = 

   1.
  -0.4285714
  
   0.2857143
