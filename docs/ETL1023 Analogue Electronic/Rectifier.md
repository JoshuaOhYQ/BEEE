# Chapter 3: Rectifier

## AC to DC Conversion
<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/88f6455cd04a762483d9488db68318fa35be0577/docs/ETL1023%20Analogue%20Electronic/BlockDC.png?raw=true" alt="BlockDC">
</div>

**Output DC voltage** is used to power most electronic circuits, including consumer electronics, computers, industrial controllers, and laboratory instrumentation systems and equipment. **Rectifier** can be either a *half-wave rectifier* or *full-wave rectifier*. **Rectifier** converts *AC input voltage* to *pulsating DC voltage*. **Filter** then eliminates the fluctuations in the rectified voltage and *produces a relatively smooth dc voltage*. **Regulator** then *maintains a constant dc voltage* for variations in the input line voltage or in the load. 


## Half-wave Rectifier
<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/8d13c6e94ca493ecda8ae836e3557ae60e20227a/docs/ETL1023%20Analogue%20Electronic/RectifierPic/Halfwave1.png?raw=true" alt="HWRectifier">
</div> 

A *diode* is connected to an *ac source* and to a *load resistor*, $R_L$ forming a **half-wave rectifier**.

### Ideal Model 
If we use an *ideal model* for the **diode**, we basically ignore the *voltage drop of the diode*, as the the **diode** is a *short circuit* ```R = 0 Ω``` when *forward-biased* and *open circuit* ```R = ∞ Ω``` when *reversed-biased*. 

### Constant Voltage Drop Model
If we use a *constant voltage drop model* for the **diode**, we have to take into account the voltage drop , $V_D$ when *forward biased* of the **diode** as a constant value, typically around **0.7 V for silicon diode** and **0.3 V for germanium diode**. This can be shown in the graph below, where $V_D$ is the **constant voltage drop of diode**:

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/8d13c6e94ca493ecda8ae836e3557ae60e20227a/docs/ETL1023%20Analogue%20Electronic/RectifierPic/TransferConstantVoltageD.png?raw=true" alt="TCConstantVD">
</div>

!!! note "Barrier Potential"

    Basically, when using a diode, *input voltage* must overcome the **barrier potential or voltage drop of 0.7 V (silicon)** before diode can become forward-biased. This results in a **output**, $V_O$ with peak value that is **0.7 V less than peak value of input**, $V_S$ :
    $$
    V_{O} = V_{S} - 0.7 V
    $$  

### Operation 
- Using the **Constant Voltage Drop Model**, when the sinusoidal input voltage, $V_S$ goes *positive*, **diode** is *forward-biased* and *conducts current*. Current passes through load resistor and produces an output voltage across the load resistor, which is the $V_O$ or $V_S - V_D$ in the graph:  

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/8d13c6e94ca493ecda8ae836e3557ae60e20227a/docs/ETL1023%20Analogue%20Electronic/RectifierPic/Halfwave2.png?raw=true" alt="HWRectifierFB">
</div>

- Using the **Constant Voltage Drop Model**, when the sinusoidal input voltage, $V_S$ goes *negative* during the second half of its cycle, **diode** is *reversed-biased* and source voltage appears across the diode (Diode takes all the voltage). There is *no current*, so voltage across load resistor is 0 V, hence producing $V_O$ or $V_S - V_D$ of **0 V**. The net result is that only **positive half-cycles** of AC input voltage appear across the load:

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/a36e4653f1f2d635f14db6240efc684a3d73cfa9/docs/ETL1023%20Analogue%20Electronic/RectifierPic/Halfwave3.png?raw=true" alt="HWRectifierRB">
</div>

- Since, the $V_O$ does not change polarity, it is a pulsating dc voltage. 

- If we were using an **Ideal Diode Model**, the graph would look the same as the output *Constant Voltage Drop Model*, but the $V_O$ will not be considering the **voltage drop of diode**, hence during the *positive cycle*, the $V_O$ will be just the $V_S$ or same as the source voltage in the graph above, while for **Constant Voltage Drop Model**, it will be $V_S - V_D$. 

!!! Info 

    It is usually acceptable to use the **ideal diode model**, which neglects the effect of *barrier potential (voltage drop)*, when the peak value of *applied voltage* is **much greater** than the *barrier potential (voltage drop)* 

### Consideration for diode selection

#### Diode's current-handling capability
- Refers to the *maximum forward current* it can safely conduct without damage. 
- During the positive half-cycle of input AC Voltage, the diode conducts current to the load. This current *must not exceed the diode's rated* $I_F$.
- This is because excessive current raises the diode's internal temperature.

!!! example

    If the **input AC peak current**, $I_{peak} = 100 mA$, the diode's rated $I_F$ must be $> 100 mA$

#### Diode's peak inverse voltage (PIV)
- Refers to the *maximum reverse voltage* across the diode during the negative half-cycle.
- It is used to determine the *maximum reverse voltage (PIV rating)* the diode can withstand without breaking down.
- During the negative half-cycle, the diode is reverse-biased. The **diode takes the entire voltage from the source when it is reverse-biased** according to Kirchoff's Voltage Law, as voltage across resistor is zero. 
- The PIV rating of the diode *must be at least the peak input voltage*, $V_{peak}$.
- If the reverse voltage exceeds diode's PIV rating, breakdown of diode can occur, potentially damaging or destroying the diode. 

!!! Warning "Recommendation"

    It is recommeneded to have $V_{BR} > 1.5 PIV$, where $V_{BR}$ is the *diode's reverse breakdown voltage*. This is to provide a safety margin for voltage spikes or transients. 

#### Example consideration with graphs

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/9b75d240a3ad9d2f4b005ed934daec2b27e84aff/docs/ETL1023%20Analogue%20Electronic/RectifierPic/Halfwave4.png?raw=true" alt="HWRectifierPIVI">
</div>

To calculate the peak current through the diode during the positive half-cycle:
$$
I_{\text{forward}} = \frac{V_S - V_D}{R_{\text{load}}}
$$
Where, $V_S$ : Peak Source Voltage, $V_D$ : Diode's Forward Voltage Drop (≈ 0.7 V), $R_{load}$ : Load Resistance

**Hence, diode's current rating,** $I_F$ **must exceed the value of** $I_{\text{forward}}$ . 


!!! example

    If $I_{\text{forward}} = 93 mA$ , then we must select a diode with $I_F > 93 mA$ 

To find PIV for diode:
$$
PIV = V_{peak}
$$
Where, $V_{peak}$ is the peak input voltage, $V_S$

**Hence, diode's PIV rating or** $V_{BR}$ **must be more than** $1.5 PIV$ .

!!! example

    If \( V_S = 10\,\text{V} \), then the peak inverse voltage (PIV) is also \( 10\,\text{V} \).  
    We must choose a diode with a breakdown voltage \( V_{\text{BR}} \) greater than 1.5 times the PIV:

    $$
    V_{\text{BR}} > 1.5 \times 10\,\text{V} = 15\,\text{V}
    $$

## Full-wave Rectifier 
**Full-wave rectifier** allows unidirectional (one-way) current through the load during the *entire 360° of the input cycle*. Whereas, **half-wave rectifier** only allows current through the load only during *one-half of the cycle*. Thus, **full-wave rectification** will produce an output voltage with a frequency *twice the input frequency* and *pulsates every half-cycle of input*.

### Ideal Model 
If we use an *ideal model* for the **diode**, we basically ignore the *voltage drop of the diode*, as the the **diode** is a *short circuit* ```R = 0 Ω``` when *forward-biased* and *open circuit* ```R = ∞ Ω``` when *reversed-biased* same like what it is used for in *half-wave rectifier*. 

### Constant Voltage Drop Model
If we use a *constant voltage drop model* for the **diode** in **full-wave rectifier**, we have to take into account the voltage drop , $V_D$ when *forward biased* of the **diode** as a constant value, typically around **0.7 V for silicon diode** and **0.3 V for germanium diode**. 

Looking at the graph below, the slopes are ±1, as a **full-wave rectifier** inverts the negative half of the input sine wave so that *both positive and negative inputs produce a positive output* for the resistor:
$$
V_{out} = |V_{in}|
$$

Hence, 

$$
V_{out} = 
\begin{cases}
V_{in} & \text{if } V_{in} > 0 \quad (\text{Slope} = +1) \\
-V_{in} & \text{if } V_{in} < 0 \quad (\text{Slope} = -1)
\end{cases}
$$

Graphically, this forms a **V-shaped curve**, where the output mirrors the input during the positive half and flips it during the negative half. The curve near the origin is slightly **flatenned**, meaning *no output until* $|V_{in}|$ *exceeds the diode drops*, $V_D$. This can be shown in the graph below, where $V_D$ is the **constant voltage drop of diode**:

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/6c39dde28b20996bc91c08ef7813201fb6df2b83/docs/ETL1023%20Analogue%20Electronic/RectifierPic/TransferFWR.png?raw=true" alt="TCConstantVFW">
</div>

### Center-Tapped Full-Wave Rectifier Operation
- **Center-tapped rectifier** is a type of *full-wave rectifier* that uses *two diodes connected to the secondary of a center-tapped transformer*:

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/6fdf8e581b8fdf6e4904b4d415cd7ae2ca995bf1/docs/ETL1023%20Analogue%20Electronic/RectifierPic/CTFW1.png?raw=true" alt="CTFW1">
</div>

!!! Info "Why Center-Tapped"

    **Half of the total secondary voltage** appears between the center tap and each end of the secondary winding (*Each side have same number of turns*, producing 2 equal halves)


- Using a **ideal diode model**, during the *positive half-cycle of input voltage*, diode $D_1$ is *forward-biased* and diode $D_2$ is *reverse-biased*. Since, it is **ideal diode**, there will be *no voltage drop* across the diode. The current path is through $D_1$ and load resistor $R_L$. Basically, the output waveform will be $V_S$ same as the *postiive half-cycle of input voltage*. 

- Using a **ideal diode model**, during the *negative half-cycle of input voltage*, diode $D_1$ is *reverse-biased* and diode $D_2$ is *forward-biased*. Since, it is **ideal diode**, there will be *no voltage drop* across the diode. The current path is through $D_2$ and load resistor $R_L$. Basically, the output waveform will be $V_S$ same as the *postive half-cycle of input voltage*. 

- As a result, the output current during **both positive and negative** portions of the input cycle through the load will be in the **same direction**, hence output voltage across load resistor is a **full-wave rectified dc voltage**.

- On the other hand, if we were using a **constant voltage drop diode model**, the process will be the *same as the ideal diode model*, but we would have to consider the **constant forward voltage drop across the diode**, $V_D$ during **forward-biased**, which are around *0.7 V for silicon diode* and *0.3 V for germanium diode*. Hence, the output peak value will be $V_S - V_D$ for the complete cycle just like in the graph below. 

- Graph during the **positive half-cycle of input voltage**:
<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/51873780389343678e181a2f87dc3bf7418c9140/docs/ETL1023%20Analogue%20Electronic/RectifierPic/FullwaveCT1.png?raw=true" alt="FullwaveCT1">
</div>

- Graph during the **negative half-cycle of input voltage**:
<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/51873780389343678e181a2f87dc3bf7418c9140/docs/ETL1023%20Analogue%20Electronic/RectifierPic/FullwaveCT2.png?raw=true" alt="FullwaveCT2">
</div>

- Graph of **full complete waveform**:
<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/51873780389343678e181a2f87dc3bf7418c9140/docs/ETL1023%20Analogue%20Electronic/RectifierPic/FullwaveCT3.png?raw=true" alt="FullwaveCT3">
</div>

!!! Warning "Ideal diode model"

    For **Ideal diode model**, instead of $V_S - V_D$ , it will be just $V_S$ , same value as the input voltage for both cycles.  


### Center-Tapped Full-Wave Rectifier PIV
In a center-tapped rectifier, during the positive half-cycle, one diode $D_1$ conducts and in forward-biased, while the other diode $D_2$ is in reverse-biased. Meanwhile, during the negative half-cycle, the vice versa happens. 

To derive the **Peak Inverse Voltage (PIV)** for diodes in a **center-tapped full-wave rectifier**: 

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/3a26a68cfb3c35e75079b8e27be6578a948e6e8b/docs/ETL1023%20Analogue%20Electronic/RectifierPic/PIVCTFWR.png?raw=true" alt="FullwaveCT3">
</div>

When diode \( D_2 \) is in reverse bias, the voltage across \( D_2 \) is:

\[
V_{D2} = V_O - (-V_S)
\]

The waveform reaches its peak/maximum value when \( V_O = V_S - V_D \).  

Since \( D_2 \) is reverse-biased, \( V_{D2} = \text{PIV} \):

\[
\begin{align*}
\text{PIV} &= V_O - (-V_S) \\
           &= V_O + V_S
\end{align*}
\]

Substituting \( V_O = V_S - V_D \):

\[
\begin{align*}
\text{PIV} &= (V_S - V_D) + V_S \\
           &= 2V_S - V_D
\end{align*}
\]

!!! Success "Final Equation for Center-Tapped Full Wave Rectifier"

    **PIV (Peak Inverse Voltage)** is the *maximum reverse voltage of the diode* when reverse-biased. Hence in this case, for **center-tapped full wave rectifier**, it is \( \text{PIV} = 2V_S - V_D \) .  

### Bridge Full-Wave Rectifier Operation 
- **Bridge Full-Wave Rectifier** is a *full-wave rectifier* **without** the need of a **center-tapped transformer**. It uses **4 diodes**, with arrangements similar to *Wheatstone bridge*:

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/6d5226ee13d06353193f7445549ec4b90667d957/docs/ETL1023%20Analogue%20Electronic/RectifierPic/Bridge1.png?raw=true" alt="Bridge1">
</div>

- Using an **ideal-diode model**, when the input cycle is positive, diodes $D_1$ and $D_2$ are **forward-biased** and conduct current. A voltage is developed across the resistor and same like the *positive half of the input cycle* since we *do not have to consider the voltage drop across the diode*. During this time, diodes $D_3$ and $D_4$ are **reverse-biased**. 

- Using an **ideal-diode model**, when the input cycle is negative, diodes $D_3$ and $D_4$ are **forward-biased** and conduct current in the **same direction as positive half-cycle through the resistor**. A voltage is developed across the resistor and same like the *positive half of the input cycle* (*because same current direction*) since we *do not have to consider the voltage drop across the diode*. During this time, diodes $D_1$ and $D_2$ are **reverse-biased**. As a result, a **full-wave rectified output voltage** appears across the resistor. 

- Using a **constant voltage drop diode model**, the *process of the rectification will be the same* as the ideal-diode model, but we have to consider the *constant voltage drop across the diodes*. Looking at the process illustration below, **2 diodes are always in series with the load resistor**, whether it is positive or negative half-cycles. So, if we take into account the diode drops, the output voltage is:
$$
V_O = V_S - 2V_D
$$

- Graph during the **positive half-cycle of input voltage**:
<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/8e7c7aa0742b47cc1e14ca82a9a5c8a202b1575f/docs/ETL1023%20Analogue%20Electronic/RectifierPic/Bridge2.png?raw=true" alt="Bridge2">
</div>

- Graph during the **negative half-cycle of input voltage**:
<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/8e7c7aa0742b47cc1e14ca82a9a5c8a202b1575f/docs/ETL1023%20Analogue%20Electronic/RectifierPic/Bridge3.png?raw=true" alt="Bridge3">
</div>

- Graph of **full complete waveform**:
<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/8e7c7aa0742b47cc1e14ca82a9a5c8a202b1575f/docs/ETL1023%20Analogue%20Electronic/RectifierPic/Bridge4.png?raw=true" alt="Bridge4">
</div>

!!! Warning "Ideal diode model"

    For **Ideal diode model**, instead of $V_S - 2V_D$ , it will be just $V_S$ , same value as the input voltage for both cycles.   


### Bridge Full-Wave Rectifier PIV
To derive the PIV for **Bridge Full-Wave Rectifier**, we look at the circuit during positive input cycle, when diodes $D_1$ and $D_2$ are **forward-biased** and diodes $D_3$ and $D_4$ are **reverse-biased**:

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/dc41f80ea40bf403faf4b50f191c0a04e09968c8/docs/ETL1023%20Analogue%20Electronic/RectifierPic/PIVBridge.png?raw=true" alt="PIVBridge">
</div>

Voltage after $D_2$ is

$$
0 - V_{D2} = -V_{D2}
$$

This is also the voltage on the **left side of** $D_3$ . 

Voltage on the right side of $D_3$ is $V_O$, **due to the ground** being on the other side of the resistor. 

When $D_3$ is in reverse-biased, reverse voltage across $D_3$ is

$$
V_{D3} = V_O - (-V_{D2})
$$

The waveform reaches its peak/maximum value when

$$
V_{O} = V_S - 2V_{D}
$$

Since \( D_3 \) is reverse-biased, we can use \( V_{D3} = \text{PIV} \):

\[
\begin{align*}
\text{PIV} &= V_O - (-V_{D2}) \\
           &= V_O + V_{D2}
\end{align*}
\]

Substituting \( V_O = V_S - 2V_D \) and assuming that all diodes are the same:

\[
\begin{align*}
\text{PIV} &= (V_S - 2V_D) + V_D \\
           &= V_S - V_D
\end{align*}
\]

!!! Success "Final Equation for Bridge Full Wave Rectifier"

    **PIV (Peak Inverse Voltage)** is the *maximum reverse voltage of the diode* when reverse-biased. Hence in this case, for **bridge full wave rectifier**, it is \( \text{PIV} = V_S - V_D \) .  


## Peak Rectifier
### Introduction
- Rectified waveform *removes the segments of negative input waveform* and produces a **pulsating DC output**. 

- This **pulsating DC output** is still **unsuitable** as a dc power supply, as the *voltage constantly varies between peak voltage and zero* due to its *pulsating nature*. 

This **pulsating nature** can be resolved with a **filter capacitor**:

1. The **capacitor** is placed in parallel with the load to smooth the output voltage.
2. The capacitor **charges during voltage peaks** and **discharges during voltage valleys**.
3. This helps to **reduce the ripple voltage** (i.e., the remaining small fluctuations).
4. As a result, the capacitor filter **smooths the output voltage to a near-constant DC**.


### Operation (Ideal diode & capacitor)
- **Ideal diode**: Zero voltage drop when forward-biased, infinite resistance when reverse-biased

- **Ideal capacitor**: No leakage, infinite resistance when fully charged (i.e., holds charge forever unless discharged through a load)

- At $t = 0$, the capacitor voltage $v_C = 0 V$ (**Uncharged**). As the AC input voltage $v_s$ starts increasing from 0 toward its positive peak, the diode becomes **forward-biased** when $v_s > V_C$ (which is initially 0). The diode conducts and **charges the capacitor**:

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/c1fd3856f9ab8005b07ad805c7c44408273a1cd6/docs/ETL1023%20Analogue%20Electronic/RectifierPic/CapIdeal1.png?raw=true" alt="CapIdeal1">
</div>

- The capacitor continues charging as long as $v_s$ is increasing and greater than $V_C$. Once the **input voltage reaches its peak**, say $V_{peak}$, the capacitor **charges up to this value**:
$$
V_C = V_S = V_{peak}
$$

- After the input voltage begins to drop below the peak, $v_s < V_C$, hence diode becomes **off** and **no current flows** anymore. Because the capacitor is **ideal**, it does not discharge (**no leakage**), so it holds its voltage at $V_{peak}$ indefinetly:

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/c1fd3856f9ab8005b07ad805c7c44408273a1cd6/docs/ETL1023%20Analogue%20Electronic/RectifierPic/CapIdeal2.png?raw=true" alt="CapIdeal2">
</div>

- Since the diode is **off** and in **reverse-biased**, the capacitor is isolated and maintain its voltage:
$$
V_O = V_C = V_S 
$$

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/c1fd3856f9ab8005b07ad805c7c44408273a1cd6/docs/ETL1023%20Analogue%20Electronic/RectifierPic/CapIdeal3.png?raw=true" alt="CapIdeal3">
</div>

- During the next cycles of the AC waveform, diode will only turn on again if $v_s$ rises above the stored $V_C$. But since $v_s$ **never exceeds the peak again** (or only does so momentarily), the diode remains mostly **off** due to **ideal capacitor characteristics**. Thus, output voltage remains at $V_S$ or $V_{peak}$:

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/c1fd3856f9ab8005b07ad805c7c44408273a1cd6/docs/ETL1023%20Analogue%20Electronic/RectifierPic/CapIdeal4.png?raw=true" alt="CapIdeal4">
</div>

!!! Question "Why so"

    Now, when the ideal capacitor gets **fully charged**, the circuit is effectively an **open circuit**. Hence, there is no way for current to flow. 

!!! info "Unless...."

    Unless there's a load, in which case the capacitor might discharge slightly and get "topped up" when $v_s > V_C$

- Since the $V_O$ is a DC voltage equal to the **peak of the input wave**, the circuit is known as **peak rectifier** or **peak detector**:

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/c1fd3856f9ab8005b07ad805c7c44408273a1cd6/docs/ETL1023%20Analogue%20Electronic/RectifierPic/CapIdeal5.png?raw=true" alt="CapIdeal5">
</div>

!!! Abstract "For your information"

    Peak rectifier or peak detector is commonly used in **signal processing, power supply smoothening and precision rectifier circuits**.


### Operation (Ideal diode, but normal capacitor)
- A more practical implementation includes **a load resistance R** connected across **a normal capacitor C**. 

- **Ideal Diode**: No voltage drop when forward-biased and infinite resistance when reverse-biased.

- **Capacitor**: Stores charges, but can now discharge through load resistor R.

- **Resistor R**: Represents the load across which output is taken. 

- Output Voltage, $V_O = V_C$ which is the *voltage of the capacitor*. 

- At $t = 0$ , $V_C = 0$ , **capacitor is initially uncharged**. The diode becomes **forward-biased** as soon as $v_s > 0$ , conducts current and the **capacitor charges up** as long as $v_s > V_C$ :

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/7b2ffb11d91270ef19d8c7dd82d544423a7ebd58/docs/ETL1023%20Analogue%20Electronic/RectifierPic/CapN1.png?raw=true" alt="CapN1">
</div>

- The capacitor tracks the input voltage while it's rising. When the input voltage **reaches its peak**, the capacitor **charges fully**:
$$
V_C = V_S = V_{peak} 
$$

- After the input voltage passes the peak and starts to fall, $v_s < V_C$ , so diode becomes **reverse-biased**. At this point, the capacitor begins to **discharge through resistor R**. The voltage across the capacitor drops exponentially: $V_{C}(t) = V_{\text{peak}} e^{-\frac{t}{RC}}$
, until the diode turns on again in the next cycle:

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/7b2ffb11d91270ef19d8c7dd82d544423a7ebd58/docs/ETL1023%20Analogue%20Electronic/RectifierPic/CapN2.png?raw=true" alt="CapN2">
</div>


- Capacitor continue to **discharge**, as the diode is still off and in **reverse-biased**. At this point, there is no current flow from the source, but the capacitor **continues to power the load R** and the output voltage (capacitor voltage) gradually **drops even more** during this time:

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/7b2ffb11d91270ef19d8c7dd82d544423a7ebd58/docs/ETL1023%20Analogue%20Electronic/RectifierPic/CapN3.png?raw=true" alt="CapN3">
</div>

- In the next cycle, when the *input voltage again excceds the decayed capacitor voltage*, $v_s > V_{C}(t)$ , the diode becomes **forward-biased** again and the capacitor is **topped up and charged** back to the new peak value of $V_S$ :

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/7b2ffb11d91270ef19d8c7dd82d544423a7ebd58/docs/ETL1023%20Analogue%20Electronic/RectifierPic/CapN4.png?raw=true" alt="CapN4">
</div>

- The cycle repeats itself:

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/7b2ffb11d91270ef19d8c7dd82d544423a7ebd58/docs/ETL1023%20Analogue%20Electronic/RectifierPic/CapN5.png?raw=true" alt="CapN5">
</div>

- As a result, the output voltage, $V_O = V_C$ is not perfectly flat, but a rippled DC: 

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/7b2ffb11d91270ef19d8c7dd82d544423a7ebd58/docs/ETL1023%20Analogue%20Electronic/RectifierPic/CapN6.png?raw=true" alt="CapN6">
</div>

!!! note 

    Basically, the capacitor:

    - quickly **charges** to the peak when the diode **conducts** 
    - **discharges** slowly through R **until the next peak** 

    Which results in **small ripples** around the peak voltage and the amount of ripple depends on **R & C**: 

    $$
    V_{\text{ripple}} \propto \frac{1}{RC}
    $$

    - **Larger C**: Slower discharge & less ripple
    - **Larger R**: smaller load current & less ripple

### Derivation of filter circuit (Half-wave)
In an RC filter circuit, $v_c$ **decays exponentiatlly** over time with time constant $τ = CR$ , where *C is the capacitance* and *R is the resistance*. Voltage for capacitor at any time t is given by:

$$
v_c = V_C \cdot e^{-\frac{t}{\tau}}
$$

where, $V_C$ is the initial peak voltage across the capacitor.

!!! note "Flashback"

    When t = τ = RC, $v_c$ drops to ≈ **36.8%** of peak voltage $V_C$ :

    $$
    e^{-\frac{RC}{RC}} = e^{-1} \approx 0.368
    $$

    In basic terms, the time constant, τ determines **how quickly the capacitor discharges**. After **one time constant (1τ)**, the voltage of capacitor **reduces to about 36.8% of its initial value**.   

Time constant, τ is important in an RC filter circuit for **maintaining a stable and reliable DC output voltage**. In an RC circuit, the capacitor **charges and discharges** through the capacitor. A larger τ (achieved by **increasing C or R**) results in **slower voltage changes** across capacitor. If $CR >> T$ , where T is the period of the input waveform, it ensures that the capacitor **does not discharge significantly during T**, hence *minimizing ripple*:

\begin{align*}
e^{-\frac{T}{\tau}} &= e^{-\frac{T}{RC}} \\
\text{If } RC &\gg T, \text{ then } \frac{T}{RC} \to 0 \Rightarrow e^{-\frac{T}{RC}} \to 1
\end{align*}

So, *the larger the τ, the smaller the change in* $V_C$ : 

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/7950e83135c62e7e239c7e2773d210cceefb3003/docs/ETL1023%20Analogue%20Electronic/RectifierPic/Dev1.png?raw=true" alt="Dev1">
</div>

!!! info "For your information"

    While larger R or C improves filtering, it may also **slow the circuit's response to load changes**. Besides, **larger C** *increases cost or size* and **larger R** *lowers output current capability*.  

When a capacitor discharges through a resistor in an RC filter circuit, the *output voltage decays slightly between input pulses*. This decay causes a **small fluctuation** called the **ripple voltage**, $V_r$. To **minimize ripple** and keep $V_r$ **small**, **CR must be large** to ensure the capacitor **discharges very slowly**: 

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/dc7b42857ec5950bf99380b55e2d2e64bbf559a8/docs/ETL1023%20Analogue%20Electronic/RectifierPic/Dev2.png?raw=true" alt="Dev2">
</div>

Approximation for calculating **DC output voltage** ($V_O$) in an RC filter circuit, accounting for *ripple voltage* $V_r$ :

- The capacitor **discharges between input pulses**, causing the output to **drop** from $V_S$ to $V_S - V_r$ . 
- The **average** of these extremes ($V_S$ and $V_S - V_r$) gives the DC output:
$$ 
V_O = \frac{V_S + (V_S - V_r)}{2} = V_S - \frac{1}{2} V_r
$$
Where:  
\( V_S \): Peak voltage (maximum value of the unfiltered input, e.g., rectified AC)  
\( V_r \): Peak-to-peak ripple voltage (fluctuation due to capacitor discharge)  
\( V_O \): Average DC output voltage after filtering

In the formula above, $V_O$ is basically the **midpoint of the ripple extremes**.

!!! Warning 

    **This formula works by assuming that:**

    - Linear discharge (valid if $CR >> T$ , only **small ripple**)
    - **Symmetric ripple waveform** (sawtooth or triangular approximation)

Relationship between ripple voltage $V_r$ , time constant $\tau$ and input period $T$: 

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/2d01e0836611c6a8874acaf7f3589f00cde351a8/docs/ETL1023%20Analogue%20Electronic/RectifierPic/Dev3.png?raw=true" alt="Dev3">
</div>

- During the **discharge phase** of an RC filter circuit, where **diode is cut-off and not conducting**, output voltage *decays exponentially*: 

$$
v_o = V_S \cdot e^{-\frac{t}{CR}}
$$

where, $V_S$ is the *peak voltage*.

- At the **end of discharging** (after time T), **output reaches its minimum**:

$$
V_S - V_r \approx V_S e^{\frac{-T}{CR}}
$$

where, $V_r$ is the *voltage drop during discharge* / *ripple voltage*.

- As $CR >> T$ , $\frac{T}{CR}$ is **very small**, hence we can use the approximation of:
$$
e^{\frac{-T}{CR}} \approx 1 - \frac{T}{CR}
$$

- *Substituting* into the discharge equation we get:
$$
V_S - V_r \approx V_S \left(1 - \frac{T}{CR} \right)
$$

$$
V_r \approx V_S \cdot \frac{T}{CR}
$$

!!! Abstract "Interpretation"

    Final equation to find ripple voltage:

    $$
    V_r \approx V_S \cdot \frac{T}{CR}
    $$

    Looking at this equation, **ripple voltage** $V_r$ **decreases** if:

    - C or R **increases** (larger time constant)
    - T **decreases**

- As frequency $f$ is the reciprocal of cycle period $T$ , $f = \frac{1}{T}$ , we *substitute* this into the formula to find $V_r$ :
$$
V_r \approx V_S \cdot \frac{T}{CR} = \frac{V_S}{fCR}
$$

- With $V_r << V_S$ (**small ripple**), we can assume that **capacitor discharges with a constant current**:
$$
I_L = \frac{V_S}{R}
$$

- If we *subsitute* this **constant current** $I_L$ into the formula for $V_r$ : 
$$
V_r = \frac{I_LT}{C} = \frac{I_L}{fC}
$$

!!! Abstract "Interpretation"

    Alternative equation to find ripple voltage:

    $$
    V_r = \frac{I_L}{fC}
    $$

    Looking at this equation, **ripple voltage** $V_r$ **decreases** if:

    - frequency, $f$ or capacitance, $C$ **increases** 
    - load current, $I_L$ **decreases**

!!! Warning 

    The constant-current assumption holds only if $V_r << V_S$ , if **larger ripple**, you need to use **exponential decay equations**. 

### Derivation of filter circuit (Full-wave)
The key differences between half-wave and full-wave peak rectifiers with capacitor filtering is that:

- **Half-Wave**: Uses only **one half** of the AC cycle, resulting in a **ripple frequency** ($f$) **equal** to the **input AC frequency** (e.g., *50 Hz*)

- **Full-Wave**: Uses **both halves** of the AC cycle, **doubling the ripple frequency** (e.g., *100 Hz for 50 Hz input*)

!!! note 

    - **Half-Wave Output**: Larger gaps between recharge pulses, deeper ripple.
    - **Full-Wave Output**: More frequent recharging, smaller ripple amplitude.

With **full-wave peak rectifier**, decaying **period** is approximately **reduced by half**, so **discharge time** is $\frac{T}{2}$:
$$
V_r = \frac{V_ST}{2CR} = \frac{V_S}{2fCR} 
$$
where, $f$ is the **original AC frequency** from the **source**. But the **effective ripple frequency** is $2f$ . 

The discharge period ($T$) is **halved**, since the capacitor is **recharged twice** as often:

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/385fa90f6477a5f1490916610eec558e2fd0a6fb/docs/ETL1023%20Analogue%20Electronic/RectifierPic/Dev4.png?raw=true" alt="Dev4">
</div>

!!! info "Extra Info"

    Full-wave rectifiers require **more diodes** but offer **better performance**, as full-wave rectifier inherently produce **less ripple voltage** for the same $C$ , $R$ and input frequency because the **capacitor discharges for a shorter time**. 
