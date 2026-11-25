# BP-RZ-AMI

```matlab
clc;
clear all;
close all;
n=floor(mod(randn(1,10),2));
s(1)=1;
h=-1;
for i=1:10
    if(n(i)==0)
        s=[s zeros(1,10)];
    else
        h=h*(-1);
        s=[s ones(1,5)*h zeros(1,5)];
    end
end
plot(s);
title('BP-RZ-AMI');
ylim([-1.2 1.2]);
for i=1:10
    text(i*10-5,1.1,num2str(n(i)));
end
```
