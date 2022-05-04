## Exercício
Use a eliminação de Gauss com pivotamento para resolver manualmente o sistema:

3 𝑥1 + 𝑥2 + 2 𝑥3 = 2

6 𝑥1 + 3 𝑥2 − 𝑥3 = −2

2 𝑥1 + 3 𝑥2 + 𝑥3 = 1

• Com o auxílio da Função Scilab, confira o resultado obtido.


## Resposta no Scilab 
--> A=[3 1 2; 6 3 -1; 2 3 1]
 A  = 

   3.   1.   2.
   6.   3.  -1.
   2.   3.   1.


--> b= [2;-2;1]
 b  = 

   2.
  -2.
   1.


--> x=gaussp(A, b)

   6.    3.   -1.   -2.
   0.5  -0.5   2.5   3.
   2.    3.    1.    1.

   6.          3.   -1.         -2.       
   0.5        -0.5   2.5         3.       
   0.3333333   2.    1.3333333   1.6666667

   6.          3.    -1.         -2.       
   0.3333333   2.     1.3333333   1.6666667
   0.5        -0.25   2.8333333   3.4166667
 x  = 

  -0.1470588
   0.0294118
   1.2058824
