# EXP 1 A : COMPUTATION OF DFT USING DIRECT AND FFT

# AIM: 

# To Obtain DFT and FFT of a given sequence in SCILAB. 

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 
// DISCRETE FOURIER TRANSFORM 

```
 clc;
 clear;
close;

x = [1 1 1 1 0 0 0 0];
N = 8;
X = zeros(1, N);

for k = 0:N-1
    s = 0;
    for n = 0:N-1
        s = s + x(n+1)*exp(-%i*2*%pi*k*n/N);
    end
    X(k+1) = s;
end

magX = abs(X);
k = 0:N-1;

subplot(2,1,1);
plot2d3(0:N-1, x);
xlabel("n");
ylabel("x(n)");
title("Input Sequence");

subplot(2,1,2);
plot2d3(k, magX);
xlabel("k");
ylabel("|X(k)|");
title("Magnitude Spectrum (Direct DFT)");
```
# FFT
```
clc;
clear;
close;

x = [1 1 1 1 0 0 0 0];
N = 8;
j = %i;

X = zeros(1, N);

for k = 0:3
    a = x(k+1) + x(k+5);
    b = x(k+1) - x(k+5);
    X(k+1) = a;
    X(k+5) = b;
end

for k = 0:1
    t = exp(-j*2*%pi*k/4);
    a = X(k+1) + t*X(k+3);
    b = X(k+1) - t*X(k+3);
    X(k+1) = a;
    X(k+3) = b;

    a = X(k+5) + t*X(k+7);
    b = X(k+5) - t*X(k+7);
    X(k+5) = a;
    X(k+7) = b;
end

for k = 0:3
    t = exp(-j*2*%pi*k/8);
    a = X(k+1) + t*X(k+5);
    b = X(k+1) - t*X(k+5);
    X(k+1) = a;
    X(k+5) = b;
end

magX = abs(X);
k = 0:N-1;

subplot(2,1,1);
plot2d3(0:N-1, x);
xlabel("n");
ylabel("x(n)");
title("Input Sequence");

subplot(2,1,2);
plot2d3(k, magX);
xlabel("k");
ylabel("|X(k)|");
title("Magnitude Spectrum (FFT – Radix 2)");
```


# OUTPUT: 
<img width="1919" height="936" alt="Screenshot 2026-02-03 133555" src="https://github.com/user-attachments/assets/31e9ee80-e1ea-4465-ac93-a4cb7775c3ae" />

<img width="1919" height="939" alt="Screenshot 2026-02-03 140447" src="https://github.com/user-attachments/assets/a4e5257c-03d7-4e3f-bc4a-50486e0a7a7c" />




# RESULT: 
Thus, the Discrete Fourier Transform and Fast Fourier Transform of the given sequence was obtained and its magnitude and phase spectrum were plotted.
