# 1.Experimental verification of Signal sampling using various types
# Aim
Write a simple Python program for the experimental verification of Signal sampling using various types.
# Tools required
```
Google Colab
Python
NumPy Library
Matplotlib Library
Internet Connection
Computer / Laptop
```
# Program
```
import numpy as np
import matplotlib.pyplot as plt
# Continuous signal parameters
fm = 5                      # Message frequency 5hz
fs = 50                     # Sampling frequency 50hz
t = np.linspace(0, 1, 1000) # Continuous time axis
ts = np.arange(0, 1, 1/fs)  # Sampled time axis

# Original analog signal
x = np.sin(2 * np.pi * fm * t)#x=sin(2pifmt)

# Sampled values
xs = np.sin(2 * np.pi * fm * ts)

# Flat-top sampling generation
flat_top = np.zeros_like(t)

for i in range(len(ts)-1):
    idx = np.where((t >= ts[i]) & (t < ts[i+1]))
    flat_top[idx] = xs[i]

# Plotting
plt.figure(figsize=(12,8))

# Original signal
plt.subplot(4,1,1)
plt.plot(t, x)
plt.title("Original Analog Signal")
plt.grid()

# Ideal Sampling
plt.subplot(4,1,2)
plt.stem(ts, xs, basefmt=" ")
plt.title("Ideal Sampling")
plt.grid()

# Natural Sampling (approximated)
plt.subplot(4,1,3)
plt.plot(t, x)
plt.stem(ts, xs, linefmt='r', markerfmt='ro', basefmt=" ")
plt.title("Natural Sampling")
plt.grid()

# Flat-top Sampling
plt.subplot(4,1,4)
plt.plot(t, flat_top)
plt.title("Flat-top Sampling")
plt.grid()

plt.tight_layout()
plt.show()
```
# Output Waveform

<img width="1624" height="973" alt="Screenshot 2026-04-21 092013" src="https://github.com/user-attachments/assets/2a1a4783-02aa-4a16-8296-0adf10ed54b2" />


# Results

<img width="1624" height="973" alt="Screenshot 2026-04-21 092013" src="https://github.com/user-attachments/assets/14734dbc-f80c-4f5a-a7e6-54306407640c" />


# Hardware experiment output waveform.

<img width="1624" height="973" alt="Screenshot 2026-04-21 092013" src="https://github.com/user-attachments/assets/76fa4276-41a6-45c1-a692-7a625473c404" />

