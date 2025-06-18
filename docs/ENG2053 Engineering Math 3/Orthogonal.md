# Integral of Periodic Function – Orthogonal / Non- Orthogonal

## Even & Odd Functions
- If function is **even**: $f(-x) = f(x)$

!!! Example

    $f(x) = x^2$  and  $g(x) = cos(x)$ 
    

- If function is **odd**: $f(-x) = -f(x)$

!!! Example

    $f(x) = x^3$  and  $g(x) = sin(x)$ 

- Sketching of even and odd functions: <br>

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/3c26dc604f5f2f2f0e529b2a353afb4504c6f1d4/docs/ENG2053%20Engineering%20Math%203/Even.png?raw=true" alt="Even&Odd">
</div>

<br>

!!! Tip "Facts about intregrals of even/odd functions"

    **These facts are only valid on "symmetric interval" (Example: [-L,L]) and these facts may not be true if we are not integrating on a "symmetric interval":** 

    - $f(x)$ is even, then
      $$
      \int_{-L}^{L} f(x) dx = 2 \int_0^L f(x) dx
      $$

    - $f(x)$ is odd, then
      $$
      \int_{-L}^{L} f(x) dx = 0
      $$

!!! Abstract "Product of even and odd"

    - Odd x Odd = Even
    - Even x Even = Even
    - Odd x Even = Odd


## Orthogonality in Fourier Series
- In Fourier series, **sine and cosine** functions are examined for their orthogonality, as it shows how these functions interact over one period.

- In Fourier series, we represent periodic function as a sum of sines and cosines. 

- Orthogonality ensures each term in this sum corresponds to an independent frequency component, therefore the coefficients of $a_n$, $a_0$ and $b_n$ can be computed seperately without interference. 

## Non-Orthogonal Functions 
- Two functions are **non-orthogonal** if the intergral of their inner product over the interval is *nonzero*: 
  $$
  \int_{a}^{b} f(x)g(x) dx \neq 0
  $$

!!! example

    === "1"

        **Given functions** $f(x) = x$ **and** $g(x) = 2x$**:**
        $$
        \int_{0}^{1} f(x)g(x) dx = \int_{0}^{1} x(2x) dx = 2 \int_{0}^{1} x^2 dx = \left. \frac{2x^3}{3} \right|_{0}^{1} = \frac{2}{3}
        $$

        ```markdown
        Hence, since the product of these functions is not zero, they are non-orthogonal.
        ```

    === "2"

        **Given functions** \( f(x) = \cos(x) \) **and** \( g(x) = \cos(x) + \cos(3x) \)**:**

        $$
        \begin{align*}
        \int_{-\pi}^{\pi} f(x)g(x) \, dx &= \int_{-\pi}^{\pi} \cos(x) \left[ \cos(x) + \cos(3x) \right] \, dx \\
        &= \int_{-\pi}^{\pi} \cos^2(x) \, dx + \int_{-\pi}^{\pi} \cos(x) \cos(3x) \, dx
        \end{align*}
        $$

        **First integral:**
        $$
        \int_{-\pi}^{\pi} \cos^2(x) \, dx > 0
        $$

        **Second integral:**
        $$
        \int_{-\pi}^{\pi} \cos(x) \cos(3x) \, dx = 0
        $$

        **Overall result:**
        $$
        \int_{-\pi}^{\pi} f(x)g(x) \, dx = \text{non-zero}
        $$

        ```markdown
        Hence, since the product of these functions contains a non-zero component, there are non-orthogonal.
        ```

!!! Danger "For your information"

    In Fourier series, if two functions are not orthogonal, they will *interfere with each other when decomposing a function*, as they do  not exhibit the same **clean speration** as orthogonal functions making analysis more complex!


## Orthogonal Functions
- Two non-zero functions are **orthogonal** if the integral of their inner product over the interval is *zero*:

  $$
  \int_{a}^{b} f(x)g(x) \, dx = 0
  $$

- A set of non-zero functions is said to be **mutually orthogonal** on \( a \leq x \leq b \), if \( f_i(x) \) and \( f_j(x) \) are orthogonal for every \( i \neq j \). So:

$$
\int_{a}^{b} f_i(x)\, f_j(x)\, dx =
\begin{cases}
  0       & \text{if } i \ne j \\
  c > 0   & \text{if } i = j
\end{cases}
$$


!!! Tip "Extra info!"

    === "Case i ≠ j"

        -  Even though the product $f_1(x)f_2(x)$ isn't zero at all points, the positive contributions in some regions are canceled out by negative contributions in others, particularly around where the sine and cosine functions interact.

        - Basically, when you integrate the product $f_1(x)f_2(x)$ over a full period, the total positive and negative areas balance out, resulting in a net integral of zero, confirming that the functions are orthogonal


    === "Case i = j"

        - For this case we will get a positive value from the integral, as:

          $$
          \int_{\a}^{\b} \f_i(x)f_i(x)  \, dx = \int_{\a}^{\b} \[f_i(x)]^2  \, dx > 0
          $$















