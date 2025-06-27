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
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/3c26dc604f5f2f2f0e529b2a353afb4504c6f1d4/docs/ENG2053%20Engineering%20Math%203/Even.png?raw=true" alt="Even&Odd">
</div>

- If we know what the function looks like over **one complete period**, we can sketch a graph of the function over a **wider interval of x** (many periods)

- Property of **repetition** defines the fundamental spatial frequency,  
  $k = \frac{2\pi}{L}$, that is used to give the first approximation to the periodic pattern $f(x)$:

  $$
  f(x) \approx C_1 \sin(kx + \alpha_1) = a_1 \cos(kx) + b_1 \sin(kx)
  $$

  where $a_1$, $b_1$, and $C_1$ are **constants** of amplitudes, and $\alpha_1$ is a **constant** of phase for the first approximation.

