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

### Consideration for diode selection

#### Diode's current-handling capability
- Refers to the *maximum forward current* it can safely conduct without damage 
- During the positive half-cycle of input AC Voltage, the diode conducts current to the load. This current *must not exceed the diode's rated* $I_F$.
- This is because excessive current raises the diode's internal temperature.

!!! example

    If the **input AC peak current**, $I_peak = 100 mA$, the diode's rated $I_F$ must be $> 100 mA$!



