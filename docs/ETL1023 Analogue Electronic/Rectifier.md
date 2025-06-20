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

- On the other hand, if we were using a **constant voltage drop diode model**, the process will be the *same as the ideal diode model*, but we would have to consider the **constant forward voltage drop across the diode**, $V_D$ during **forward-biased**, which are around *0.7 V for silicon diode* and *0.3 V for germanium diode*. Hence, the output peak value will be $V_S - V_D$. 





