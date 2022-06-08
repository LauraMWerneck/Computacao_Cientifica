## Console 
```c
--> fun = '[sin(%pi*x(1))+log(x(2))-2; 2*x(1)^3+sqrt(2*x(2))-3]'
 fun  = 

 [sin(%pi*x(1))+log(x(2))-2; 2*x(1)^3+sqrt(2*x(2))-3]


--> jac = '[%pi*cos(%pi*x(1)) 1/x(2); 6*x(1)^2 1/sqrt(2*x(2))]'
 jac  = 

 [%pi*cos(%pi*x(1)) 1/x(2); 6*x(1)^2 1/sqrt(2*x(2))]


--> [x, iter]=newraph_n(fun, jac)
Entre com as aprox. inicial x0 = [1;2]

 iter  = 

   5.

 x  = 

   0.6473061
   3.0197778

--> [x, iter]=newraph_n(fun, jac)
Entre com as aprox. inicial x0 = [0;1]

 iter  = 

   5.

 x  = 

   0.1674742
   4.4718606
```
