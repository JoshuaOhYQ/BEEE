# Fourier Series: Part 1

## Introduction
With the knowledge of **even and odd functions**, work required to find Fourier Series can be reduced, as some **Fourier coefficients** $a_0$ , $a_n$ or $b_n$ become **zero** after integration.

## Fourier Series for Even Functions

$y = f(t)$ is **even** if $f(-t) = f(t)$ for all values of $t$ . Graph is always symmetrical about the **y-axis** (miror image):

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/2278648141d5a50c01aa59928e2e8842bbc482ac/docs/ENG2053%20Engineering%20Math%203/evengraph.png?raw=true" alt="evengraph">
</div>

For **even** function $f(t)$ with range $-L$ to $L$ (**period** $= 2L$ ), this will produce value **0**:

$$
b_n = \frac{1}{L} \int_{-L}^{L} f(t) \sin(\frac{n\pi t}{L}) \, dt = 0
$$
 
<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/2278648141d5a50c01aa59928e2e8842bbc482ac/docs/ENG2053%20Engineering%20Math%203/0area1.png?raw=true" alt="0area1">
</div>

!!! note "Flashback"

    - Product of an **even function** and an **odd function** will produce an **odd function**. 

    - Product of **two even functions** will produce **even** and product of **two odd functions** will produce **even**.

Since for an **even function**, **coefficient** $b_n$ has zero value ( $b_n = 0$ ), we only have to calculate $a_0$ and $a_n$ for **Fourier Series expansion**:

$$
a_0 = \frac{1}{L} \int_{-L}^{L} f(t) \, dt
$$

$$
a_n = \frac{1}{L} \int_{-L}^{L} f(t) \cos\left( \frac{n\pi t}{L} \right) \, dt
$$


**Final Fourier expansion** for an **even** function has **cosine** terms only: 

$$
f(t) = \frac{a_0}{2} + \sum_{n=1}^{\infty} \left[ a_n \cos(\frac{n\pi t}{L}) \right]
$$



## Fourier Series for Odd Functions

$y = f(t)$ is **odd** if $f(-t) = -f(t)$ for all values of $t$ . Graph is always symmetrical about the **origin**:

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/2278648141d5a50c01aa59928e2e8842bbc482ac/docs/ENG2053%20Engineering%20Math%203/evengraph.png?raw=true" alt="oddgraph">
</div>

For **odd** function $f(t)$ with range $-L$ to $L$ (**period** $= 2L$ ), this will produce value **0**:

$$
a_n = \frac{1}{L} \int_{-L}^{L} f(t) \cos(\frac{n\pi t}{L}) \, dt = 0
$$

Since for an **odd function**, **coefficient** $a_n$ and $a_0$ has zero value ( $a_0 = 0$ & $a_n = 0$ ), we only have to calculate $b_n$ for **Fourier Series expansion**:

$$
b_n = \frac{1}{L} \int_{-L}^{L} f(t) \sin\left( \frac{n\pi t}{L} \right) \, dt
$$


**Final Fourier expansion** for an **odd** function has **sine** terms only: 

$$
f(t) = \sum_{n=1}^{\infty} \left[ b_n \sin(\frac{n\pi t}{L}) \right]
$$



