# Fourier Series: Part 1

## Introduction

- **Fourier series** is a mathematical tool to *breakdown complex pattern into simpler parts*.

- By using **Fourier series**, we can represent any periodic function as a *sum of sine and cosine functions with different frequencies*.

!!! example
    
    Using **Fourier series**, a song can be represented by adding up different "notes", each with their own frequency. 

!!! info "Extra Info"

    **Fourier series** is used in many fields:

    - **Signal Processing** :  Used to analyze and clean up signals (eg. In MP3 audio files, it helps remove unnecessary data but keeps the sound quality). 
    - **Engineering** : Helps design and analyze circuits with AC (alternating current) and useful in image processing to break down image details by frequency.
    - **Physics**: Explains wave behavior, vibrations, and oscillations (sound (acoustics), light (optics), and even quantum mechanics).

- In simple words, **Fourier series** helps **simplify complex patterns into simpler components**, which makes the signals **easier to analyze and manipulate**.


## Basic Theory of Fourier Series

- Periodic function $f(X)$ with period $L$ show the same pattern every $L$ units along the *x-axis*, hence $f(x+L) = f(x)$ for every value of $x$ . 

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/c6cb3e127e004aead24f2c929391b604a0c80d85/docs/ENG2053%20Engineering%20Math%203/Four1.png?raw=true" alt="Four1">
</div>

- If we know what the function looks like over **one complete period**, we can sketch a graph of the function over a **wider interval of x** (many periods).

- Property of **repetition** defines the fundamental spatial frequency,  

  $k = \frac{2\pi}{L}$, that is used to give the first approximation to the periodic pattern $f(x)$:

  $$
  f(x) \approx C_1 \sin(kx + \alpha_1) = a_1 \cos(kx) + b_1 \sin(kx)
  $$

  where $a_1$, $b_1$, and $C_1$ are **constants** of amplitudes, and $\alpha_1$ is a **constant** of phase for the first approximation.

- A much better approximation can be built by adding an appropriate combination of harmonics to the fundamental pattern:
    
  $$
  C_2 \sin(2kx + \alpha_2) = a_2 \cos(2kx) + b_2 \sin(2kx) \quad \text{(2nd harmonic)}
  $$

  $$
  C_3 \sin(3kx + \alpha_3) = a_3 \cos(3kx) + b_3 \sin(3kx) \quad \text{(3rd harmonic)}
  $$


To build a non-smooth shape (square wave) with sharp edges and sudden jumps using **Fourier Series**, we can **add sine waves together**:

1. Start with the **fundamental sine wave** (**lowest frequency**)
2. Then add **harmonics** (**3x, 5x, 7x the frequency** etc)
3. More harmonics you add, **the closer the sum looks like a square wave**.

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/299a21871a72a521410910663bcc37dad0bdaeda/docs/ENG2053%20Engineering%20Math%203/Four2.png?raw=true" alt="Four2">
</div>

## General representation 

The **Fourier Series** for function $f(x)$ with period $L = 2\pi$ , fundamental frequency $k = \frac{2\pi}{L} = 1$ and involve terms:

$$
a_1 \cos x, \quad b_1 \sin x
$$

$$
a_2 \cos x, \quad b_2 \sin x
$$

$$
a_3 \cos x, \quad b_3 \sin x
$$

We also include a **constant term** $\frac{a_0}{2}$ to represent a functions entirely above the *x-axis* and with **sufficient number of harmonics**, approximate series can exactly represent a give function $f(X)$ :

$$
f(x) = \frac{a_0}{2} + a_1 \cos x + a_2 \cos x + a_3 \cos x + ... + b_1 \sin x + b_2 \sin x + b_3 \sin x + ...
$$

Basically, the **Fourier Series** of function $f(x)$ with **period** $2\pi$ , where **n = 1, 2, 3, ...** is:

$$
f(x) = \frac{a_0}{2} + \sum_{n=1}^{\infty} \left[ a_n \cos(nx) + b_n \sin(nx) \right]
$$

To find the **Fourier coefficients** ($a_0$ , $a_n$ , $b_n$) for function $f(x)$ , where integrations are over a **single interval** in $x$ of $L = 2\pi$ : 

**Step 1 -**
$$
a_0 = \frac{1}{\pi} \int_{2\pi} f(x) \, dx
$$

**Step 2 -**
$$
a_n = \frac{1}{\pi} \int_{2\pi} f(x) \cos(nx) \, dx
$$


**Step 3 -**
$$
b_n = \frac{1}{\pi} \int_{2\pi} f(x) \sin(nx) \, dx
$$

!!! abstract "Note that"

    If we specify a particular value of $x$ in **Fourier Series**, it will give you a series of constants equal to $f(x)$. 

If $f(x)$ is discontinuous at $x$ , the series **converges to a value half-way between the two possible function values**:

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/03e34f84a025c3b9a00f7c304ccf450870d12be7/docs/ENG2053%20Engineering%20Math%203/Four3.png?raw=true" alt="Four3">
</div>

## Alternative representation 1

For waveform $f(x)$ with period $L = \frac{2\pi}{k}$ :

$$
f(x) = \frac{a_0}{2} + \sum_{n=1}^{\infty} \left[ a_n \cos(nkx) + b_n \sin(nkx) \right]
$$

To find the **Fourier coeffiecients** where integrations are over a **single interval** in $x$ of $L$ :  

**Step 1 -**
$$
a_0 = \frac{2}{L} \int_{L} f(x) \, dx
$$

**Step 2 -**
$$
a_n = \frac{2}{L} \int_{L} f(x) \cos(nkx) \, dx
$$


**Step 3 -**
$$
b_n = \frac{2}{L} \int_{L} f(x) \sin(nkx) \, dx
$$


## Alternative representation 2

For waveform $f(x)$ with period $2L = \frac{2\pi}{k}$ , $k = \frac{\pi}{L}$ and $nkx = \frac{n\pi x}{L}$ :

$$
f(x) = \frac{a_0}{2} + \sum_{n=1}^{\infty} \left[ a_n \cos(\frac{n\pi x}{L}) + b_n \sin(\frac{n\pi x}{L}) \right]
$$

To find the **Fourier coeffiecients** where integrations are over a **single interval** in $x$ of $2L$ :  

**Step 1 -**
$$
a_0 = \frac{1}{L} \int_{2L} f(x) \, dx
$$

**Step 2 -**
$$
a_n = \frac{1}{L} \int_{2L} f(x) \cos(\frac{n\pi x}{L}) \, dx
$$


**Step 3 -**
$$
b_n = \frac{1}{L} \int_{2L} f(x) \sin(\frac{n\pi x}{L}) \, dx
$$


## Alternative representation 3

For waveform $f(t)$ with period $T = \frac{2\pi}{\omega}$ :

$$
f(t) = \frac{a_0}{2} + \sum_{n=1}^{\infty} \left[ a_n \cos(n\omega t) + b_n \sin(n\omega t) \right]
$$

To find the **Fourier coeffiecients** where integrations are over a **single interval** in $t$ of $T$ :  

**Step 1 -**
$$
a_0 = \frac{2}{T} \int_{T} f(t) \, dt
$$

**Step 2 -**
$$
a_n = \frac{2}{T} \int_{T} f(t) \cos(n\omega t) \, dt
$$


**Step 3 -**
$$
b_n = \frac{2}{T} \int_{T} f(t) \sin(n\omega t) \, dt
$$

## Useful Trigonometry results

When calculating the **Fourier coefficients** $a_n$ and $b_n$ , the following trigonometry results deduced from the graph of $\sin x$ and $\cos x$ are useful:

$$
\sin (n\pi) = 0
$$

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/63d79cd0274818309f38e7b63e6df945931a6b2e/docs/ENG2053%20Engineering%20Math%203/sin%20%3D%200.png?raw=true" alt="sin=0">
</div>

$$
\cos (n\pi) = (-1)^n
$$

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/63d79cd0274818309f38e7b63e6df945931a6b2e/docs/ENG2053%20Engineering%20Math%203/cos%20%3D%20-1.png?raw=true" alt="cos=-1">
</div>

$$
\sin\left(\frac{n\pi}{2}\right) =
\begin{cases}
0, & \text{if } n \text{ is even} \\
1, & \text{if } n = 1, 5, 9, \ldots \\
-1, & \text{if } n = 3, 7, 11, \ldots
\end{cases}
$$

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/63d79cd0274818309f38e7b63e6df945931a6b2e/docs/ENG2053%20Engineering%20Math%203/sin.2.png?raw=true" alt="sin/2">
</div>

$$
\cos\left(\frac{n\pi}{2}\right) =
\begin{cases}
0, & \text{if } n \text{ is odd} \\
1, & \text{if } n = 0, 4, 8, \ldots \\
-1, & \text{if } n = 2, 6, 10, \ldots
\end{cases}
$$

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/63d79cd0274818309f38e7b63e6df945931a6b2e/docs/ENG2053%20Engineering%20Math%203/cos.2.png?raw=true" alt="cos/2">
</div>

If we integrate over whole periods, areas cancel out:
$$
\int_{2\pi} \sin(nx) \, dx = 0
$$

$$
\int_{2\pi} \cos(nx) \, dx = 0
$$

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/03e34f84a025c3b9a00f7c304ccf450870d12be7/docs/ENG2053%20Engineering%20Math%203/Four3.png?raw=true" alt="0areas">
</div>