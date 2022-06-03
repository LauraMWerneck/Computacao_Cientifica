## Código
```c
i = 1; c = 0.25; g= 9.80665; m = 60;
vex(1)=0; // solução exata
vnum(1)=0; // solução numérica
t(1)=0; dt = 0.5;
while t(i)<12 do
t(i+1)=t(i)+dt
vex(i+1)= sqrt(g*m/c)*tanh(sqrt(g*c/m)*t(i+1));
vnum(i+1)=vnum(i)+(g - (c/m)*(vnum(i)^2))*dt
i=i+1;
end
printf("A soluçao exata de v(%d)= %f\n",t(i),vex(i));
printf("A soluçao numerica de v(%d)= %f\n",t(i),vnum(i));
e = abs((vex(i)-vnum(i))/vex(i))*100;
printf("O erro percentual relativo é %f %%",e);
plot2d(t,vex,style=[color('blue4')]);
plot2d(t,vnum,style=[color('red4')]);
xgrid
```
