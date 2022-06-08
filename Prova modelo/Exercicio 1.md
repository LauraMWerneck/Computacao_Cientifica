## Console
 
 Usou - se o método da Secante Modificada.
 
```c
--> F = 60
 F  = 60.


--> R = 100
 R  = 100.


--> L = 0.1
 L  = 0.1


--> fi = atan(2*%pi*F*L/R)
 fi  = 0.3605152


--> f = 'sin(x - fi) + sin(fi)*exp(-x/tan(fi))'
 f  = sin(x - fi) + sin(fi)*exp(-x/tan(fi))


--> [raiz, iter]=sec_mod(f, 1d-6, 0.0001)

Entre com o limite inferior de x a = %pi

Entre com o limite superior de x b = 2*%pi

Entre com o valor inicial x0 = 3.2

Iter	Raiz		erro aprox. % 
1	3.5116602998	8.875013
2	3.5021401026	0.271839
3	3.5021404020	0.000009

f(3.502140) = 0.000000
 iter  = 

   3.

 raiz  = 

   3.5021404
```
