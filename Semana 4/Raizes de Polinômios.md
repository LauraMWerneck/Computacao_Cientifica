## Código
```c
Raizes de polinômios no Scilab
• Quando se busca por todas as raízes de um polinômio, o Scilab oferece a função roots.
• Polinômio definido pelos seus coeficientes:
-->p1 = poly([-6 1 1],'x','c')
p1 = - 6 + x + x^2
-->roots(p1)
ans =
    - 3.
      2.
• Outra forma de definir o mesmo polinômio:
-->x = poly(0,'x')
    x = x
-->p1 = x^2 + x - 6
p1 = - 6 + x + x^2
-->roots(p1)
ans =
    - 3.
      2. 
• Valor numérico de um polinômio:
-->p1 = poly([-6 1 1],'x','c')
p1 = - 6 + x + x^2
-->horner(p1,1) // valor de p1 em x = 1
ans = - 4.

• Um polinômio pode também ser definido pelas suas raízes:
-->p1 = poly([-3 2],'x','r')
p1 = - 6 + x + x^2
```
