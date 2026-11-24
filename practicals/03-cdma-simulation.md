# Practical 03 — CDMA Simulation

```matlab
clc;
clear all;
close all;

data1 = [1 0 1 1];
data2 = [1 1 0 1];

data1(data1 == 0) = -1;
data2(data2 == 0) = -1;

code1 = [1 1 1 1];
code2 = [1 -1 1 -1];

spread1 = kron(data1, code1);
spread2 = kron(data2, code2);

cdma_signal = spread1 + spread2;

figure;
subplot(3,1,1);
stem(cdma_signal, 'filled');
grid on;
title('CDMA Combined Signal');
xlabel('Chip');
ylabel('Amplitude');

received1 = [];
for i = 1:length(data1)
    chips = cdma_signal((i-1)*4+1:i*4);
    value = sum(chips .* code1);
    if value > 0
        received1(i) = 1;
    else
        received1(i) = 0;
    end
end

received2 = [];
for i = 1:length(data2)
    chips = cdma_signal((i-1)*4+1:i*4);
    value = sum(chips .* code2);
    if value > 0
        received2(i) = 1;
    else
        received2(i) = 0;
    end
end

subplot(3,1,2);
stem(received1, 'filled');
grid on;
title('Recovered Data - User 1');
xlabel('Bit');
ylabel('Data');

subplot(3,1,3);
stem(received2, 'filled');
grid on;
title('Recovered Data - User 2');
xlabel('Bit');
ylabel('Data');

disp('Original Data of User 1:');
disp([1 0 1 1]);
disp('Recovered Data of User 1:');
disp(received1);
disp('Original Data of User 2:');
disp([1 1 0 1]);
disp('Recovered Data of User 2:');
disp(received2);
```
