# Instrument Types and Performance Characteristics

## Active and passive instruments
| Passive Instruments     | Active Instruments     |
| ----------------------- | ---------------------- |
| Output produced **entirely by the quantity being measured** (eg. fluid pressure) | Quantity being measured **modulates the magnitude of an external power source** to produce the output (eg. changes in resistance of strain gauge modulates external voltage) |
| Do not require an external power source to generate output | Rely on external power for their operation (usually in electrical form) |
| **Passive pressure gauge** measures fluid pressure by converting it directly into mechanical movement of a pointer (energy moving pointer comes entirely from pressure change in fluid) | **Float-type petrol tank level indicator** has a float that moves with petrol level and linked to a potentiometer arm which devides an external voltage producing output signal proportional to fuel level (energy from external source & float modulates it) |
| <img src="https://github.com/JoshuaOhYQ/BEEE/blob/615567045375a32dd5e899abc2ca1ae7e798c1c1/docs/ETL1023%20Instrumentation/Gauge1.png?raw=true" alt="Pressure Gauge"> | <img src="https://github.com/JoshuaOhYQ/BEEE/blob/615567045375a32dd5e899abc2ca1ae7e798c1c1/docs/ETL1023%20Instrumentation/float1.png?raw=true" alt="Float Petrol"> |


## Null-Type and Deflection-Type
- **Deflection-Type Instruments**: The measured quantity causes a physical displacement (deflection) of a pointer or sensor which is directly proportional to the input.

- **Null-Type Instruments**: The measured quantity is balanced by a known reference force/input until equilibrium (*Null Point*) is achieved, hence no net deflection occurs at measurement.

- **Pressure gauge** is an example of **deflection-type** instrument (value being measured is displayed in terms of movement of pointer)

- **Dead-weight gauge** is an example of **null-type** instrument: <br>
<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/327c446596f526e53f016b9dd0efafdc842bf9a1/docs/ETL1023%20Instrumentation/Dead1.png?raw=true" alt="Control System">
</div>
<br>
Basically, the fluid pressure is applied to the base of the piston enclosed in a cylinder. Pressure then creates an upward force ```F = P x A, where P is pressure, A is piston Area``` . Calibrated weights are then added to the top of the piston until the donward force balances the upward fluid force. At equilibrium, the piston returns to the reference mark (null point). The formula of ```P = mg/A``` is then used to calculate the true output. 


- Below is a complete comaparison between both **Null-type** and **Deflection-type** Instrument:
| Null-Type               | Deflection-Type        |
| ----------------------- | ---------------------- |
| Relies on precisely calibrated weights or reference forces | Display measurements instanly via pointer deflection |
| No friction/hysteresis errors (equilibrium at null point) | User-friendly (no iterative adjustments needed) |
| Independent on linearlity issues (no need for sensor/output linearlity) | Fast measurements |
| Negligible error sources & very high accuracy | **Spring/Mechanical Non-Linearlity**: Requires precise calibration of springs and sensors |
| Slower and less convenient (requires manual weight adjustment) | **Friction/Wear** : Continuous movement introduces errors over time |

## Analogue and Digital Instruments
- **Digital Instruments**: Output signals are discrete numerical values (binary). For example, *digital multimeters & smart sensors with embedded processors*.

- Advantages of using a **Digital Instrument** are:
  * [x] Direct compatibility
  * [x] Faster processing
  * [x] Higher precision (data immediately readable by computers, so can eliminates conversion delays)
  * [x] No quantization error as no analogue to digital converter is used

- Resolution of **Digital Instrument** depends on the sensor itself.

- 
