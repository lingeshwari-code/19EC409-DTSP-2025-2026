# EXP 1 A : COMPUTATION OF DFT USING DIRECT AND FFT

# AIM: 
To Obtain DFT and FFT of a given sequence in SCILAB. 
# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 
```
// DISCRETE FOURIER TRANSFORM 
clc;
clear;

// Input sequence
xn = [1 2 3 4 4 3 2 1];
n1 = 0:length(xn)-1;

// Plot input sequence
subplot(3,1,1);
plot2d3(n1, xn);
xlabel('Time n');
ylabel('Amplitude xn');
title('Input Sequence');

// DFT computation
j = sqrt(-1); // imaginary unit
N = length(xn);
Xk = zeros(1, N);

for k = 0:N-1
    for n = 0:N-1
        Xk(k+1) = Xk(k+1) + xn(n+1) * exp(-j*2*%pi*k*n/N);
    end
end

disp(Xk);

// Frequency axis
K1=0:1:length(Xk)-1; 

// Magnitude spectrum
magnitude = abs(Xk);
subplot(3,1,2);
plot2d3(K1, magnitude);
xlabel('Frequency (Hz)');
ylabel('Magnitude');
title('Magnitude Spectrum');

// Phase spectrum
// Phase spectrum
angle = atan(imag(Xk), real(Xk));

subplot(3,1,3);
plot2d3(K1, angle);
xlabel('Frequency (Hz)');
ylabel('Phase');
title('Phase Spectrum');
// FAST FOURIER TRANSFORM 
clear; clc; close all;

// Input sequence
xn = [1 2 3 4 4 3 2 1];
n1 = 0:length(xn)-1;

// Plot input sequence
subplot(2,2,1);
plot2d3(n1, xn);
xlabel('Time n');
ylabel('Amplitude');
title('Input Sequence');

// FFT computation
Xk = fft(xn);
K1 = 0:length(Xk)-1;

// Magnitude spectrum
magnitude = abs(Xk);
subplot(2,2,2);
plot2d3(K1, magnitude);
xlabel('Frequency (Hz)');
ylabel('Magnitude');
title('Magnitude Spectrum');

// Phase spectrum
angle = atan(imag(Xk), real(Xk));
subplot(2,2,3);
plot2d3(K1, angle);
xlabel('Frequency (Hz)');
ylabel('Phase (radians)');
title('Phase Spectrum');

// Inverse FFT
y = ifft(Xk);
n2 = 0:length(y)-1;
subplot(2,2,4);
plot2d3(n2, y);
xlabel('Time n');
ylabel('Amplitude');
title('Inverse FFT of X(k)');
```
# OUTPUT: 
<img width="1045" height="800" alt="image" src="https://github.com/user-attachments/assets/39e0535c-417b-470d-a6de-f28e7267824c" />
<img width="959" height="820" alt="image" src="https://github.com/user-attachments/assets/e1b7b458-ae28-4bd0-a0c7-05a2e2c95802" />

# RESULT: 
Thus the computational of DFT using Direct and FFT is verified successfully..
