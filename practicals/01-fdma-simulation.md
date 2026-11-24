# Practical 01 — FDMA Simulation

```matlab
clc;
clear all;
close all;

fs = 1000;
t = 0:1/fs:1-1/fs;

f1 = 50;
f2 = 100;
f3 = 150;

user1 = sin(2*pi*f1*t);
user2 = sin(2*pi*f2*t);
user3 = sin(2*pi*f3*t);

fdma_signal = user1 + user2 + user3;

figure;
subplot(4,1,1);
plot(t, user1);
grid on;
xlabel('Time (s)');
ylabel('Amplitude');
title('User 1 - 50 Hz');

subplot(4,1,2);
plot(t, user2);
grid on;
xlabel('Time (s)');
ylabel('Amplitude');
title('User 2 - 100 Hz');

subplot(4,1,3);
plot(t, user3);
grid on;
xlabel('Time (s)');
ylabel('Amplitude');
title('User 3 - 150 Hz');

subplot(4,1,4);
plot(t, fdma_signal);
grid on;
xlabel('Time (s)');
ylabel('Amplitude');
title('Combined FDMA Signal');
```
