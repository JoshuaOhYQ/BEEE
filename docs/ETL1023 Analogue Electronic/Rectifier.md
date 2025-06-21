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
- The PIV rating of the diode *must be at least the peak input voltage*, $I_{peak}$.
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

- This **pulsating nature** can be resolved with a **filter capacitor**:
  (i) **Capacitor** is in parallel with the load to smooth the output voltage.
  (ii) The capacitor *charges during peaks* and *discharges during valleys*.
  (iii) This help *reduce the ripple voltage (remaining small fluctuations)* significantly.
  (iv) As a result, the capacitor filter **smooths the output voltage to a near-constant DC**.

### Operation (Ideal diode & capacitor)
- **Ideal diode**: Zero voltage drop when forward-biased, infinite resistance when reverse-biased

- **Ideal capacitor**: No leakage, infinite resistance when fully charged (i.e., holds charge forever unless discharged through a load)

- At $t = 0$, the capacitor voltage $v_C = 0 V$ (**Uncharged**). As the AC input voltage $V_S$ starts increasing from 0 toward its positive peak, the diode becomes **forward-biased** when $V_S > V_C$ (which is initially 0). The diode conducts and **charges the capacitor**:

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/c1fd3856f9ab8005b07ad805c7c44408273a1cd6/docs/ETL1023%20Analogue%20Electronic/RectifierPic/CapIdeal1.png?raw=true" alt="CapIdeal1">
</div>

- The capacitor continues charging as long as $V_S$ is increasing and greater than $V_C$. Once the **input voltage reaches its peak**, say $V_{peak}$, the capacitor **charges up to this value**:
$$
V_C = V_S = V_{peak}
$$

- After the input voltage begins to drop below the peak, $V_S < V_C$, hence diode becomes **off** and **no current flows** anymore. Because the capacitor is **ideal**, it does not discharge (**no leakage**), so it holds its voltage at $V_{peak}$ indefinetly:

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

- During the next cycles of the AC waveform, diode will only turn on again if $V_S$ rises above the stored $V_C$. But since $V_S$ **never exceeds the peak again** (or only does so momentarily), the diode remains mostly **off** due to **ideal capacitor characteristics**. Thus, output voltage remains at $V_S$ or $V_{peak}$:

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/c1fd3856f9ab8005b07ad805c7c44408273a1cd6/docs/ETL1023%20Analogue%20Electronic/RectifierPic/CapIdeal4.png?raw=true" alt="CapIdeal4">
</div>

!!! Question "Why so"

    Now, when the ideal capacitor gets **fully charged**, the circuit is effectively an **open circuit**. Hence, there is no way for current to flow. 

!!! info "Unless...."

    Unless there's a load, in which case the capacitor might discharge slightly and get "topped up" when $V_S > V_C$

- Since the $V_O$ is a DC voltage equal to the **peak of the input wave**, the circuit is known as **peak rectifier** or **peak detector**:

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/c1fd3856f9ab8005b07ad805c7c44408273a1cd6/docs/ETL1023%20Analogue%20Electronic/RectifierPic/CapIdeal5.png?raw=true" alt="CapIdeal5">
</div>

!!! Abstract "For your information"

    Peak rectifier or peak detector is commonly used in **signal processing, power supply smoothening and precision rectifier circuits**.





