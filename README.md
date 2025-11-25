# EXP 1 : Linear and Circular Convolution

## AIM: 

 To perform Linear and Circular Convolution for two given sequence using SCILAB. 

## APPARATUS REQUIRED: 
PC installed with SCILAB. 

## PROGRAM (Linear Convolution): 
```
clear;

// Input signals
x = [1 1 1 1];
h = [1 2 3 4];

m = length(x);
n = length(h);

// Time indices for x and h
a = 0:m-1;
b = 0:n-1;

// Plot input signal x[n]
subplot(3,1,1);
plot2d3(a, x);
xlabel('Time n');
ylabel('Amplitude');
title('Graphical Representation of Input Signal x[n]');

// Plot impulse response h[n]
subplot(3,1,2);
plot2d3(b, h);
xlabel('Time n');
ylabel('Amplitude');
title('Graphical Representation of Impulse Signal h[n]');

// Initialize convolution result
y = zeros(1, m+n-1);

// Manual convolution calculation
for i = 1:m+n-1
    conv_sum = 0;
    for j = 1:m
        if ( (i-j+1) > 0 & (i-j+1) <= n )
            conv_sum = conv_sum + x(j) * h(i-j+1);
        end
    end
    y(i) = conv_sum;
end

// Display convolution result
disp(y, 'Convolution Output y[n] = ');

// Time index for output
t = 0:m+n-2;

// Plot convolution result y[n]
subplot(3,1,3);
plot2d3(t, y);
xlabel('Time n');
ylabel('Amplitude');
title('Graphical Representation of Output Signal y[n]');
```

## PROGRAM (Circular Convolution): 

```

// Sequences
x = [1 1 1 1];
h = [1 2 3];

// Plot input & impulse
subplot(3,1,1); plot2d3(0:length(x)-1, x); title('Input sequence');
subplot(3,1,2); plot2d3(0:length(h)-1, h); title('Impulse sequence');

// Zero padding
N = max(length(x), length(h));
x = [x, zeros(1, N-length(x))];
h = [h, zeros(1, N-length(h))];

// Circular convolution
y = zeros(1,N);
for n=1:N
  for k=1:N
    j = n-k+1; if j<=0 then j=N+j; end
    y(n) = y(n) + x(k)*h(j);
  end
end

// Plot result
subplot(3,1,3); plot2d3(0:N-1, y); title('Circular convolution');
disp(y)
```

## OUTPUT (Linear Convolution): 
<img width="1918" height="1011" alt="image" src="https://github.com/user-attachments/assets/1c8fd185-34e2-466b-b20e-e7513f83d68d" />


## OUTPUT (Circular Convolution): 
<img width="1904" height="1012" alt="image" src="https://github.com/user-attachments/assets/94fc45c3-df7c-410e-84fc-95f84d5e9a89" />


## RESULT: 
Linear and Circular Convolution are successfully executed in scilab
