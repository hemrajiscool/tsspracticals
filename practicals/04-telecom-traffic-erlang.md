# Practical 04 — Telecommunication Traffic (Erlang)

```matlab
clc;
clear all;
close all;

N = 160;
T = 1;
H_min = 3;
carrier_capacity = 5;

H = H_min / 60;
lambda = N / T;
A = lambda * H;

fprintf('========================================\n');
fprintf(' TELECOMMUNICATION TRAFFIC CALCULATION\n');
fprintf('========================================\n');
fprintf('Number of Calls          = %d\n', N);
fprintf('Observation Time         = %.2f hour\n', T);
fprintf('Average Call Duration    = %.2f minutes\n', H_min);
fprintf('Call Arrival Rate        = %.2f calls/hour\n', lambda);
fprintf('Traffic Intensity        = %.2f Erlangs\n', A);
fprintf('Carrier Capacity         = %.2f Erlangs\n', carrier_capacity);

if A > carrier_capacity
    fprintf('\nStatus: SYSTEM IS OVERLOADED\n');
else
    fprintf('\nStatus: SYSTEM IS NOT OVERLOADED\n');
end

figure;
values = [carrier_capacity A];
bar(values);
grid on;
xlabel('System Condition');
ylabel('Traffic / Capacity (Erlangs)');
title('Telecommunication Traffic and Carrier Capacity');
xticks(1:2);
xticklabels({'Carrier Signal', 'Offered Traffic'});
ylim([0 max(values)+2]);

text(1, carrier_capacity + 0.2, ...
    sprintf('%.2f Erlangs', carrier_capacity), ...
    'HorizontalAlignment', 'center');
text(2, A + 0.2, ...
    sprintf('%.2f Erlangs', A), ...
    'HorizontalAlignment', 'center');

if A > carrier_capacity
    text(1.5, max(values)+1, ...
        'OVERLOADED SIGNAL PRESENT', ...
        'HorizontalAlignment', 'center', ...
        'FontSize', 12);
end
```
