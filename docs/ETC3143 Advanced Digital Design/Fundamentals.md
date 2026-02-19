# Chapter 0: Recap from Digital Fundamentals

## Basic Logic Gates 

<div align="center">
  <img src="https://github.com/JoshuaOhYQ/BEEE/blob/c010fd3b0dfd8eb599e84ba85f3a94e1f4173385/docs/ETC3143%20Advanced%20Digital%20Design/Fundamentals/LogicGates.png?raw=true" alt="LogicGates">
</div>

!!! note 

    We can determine the **Boolean expression** that represents a logic circuit with multiple gates connected and from the Boolean expression given to us we can produce the **truth table**. For example, if there are **4 inputs** in the Boolean expression, there are **16 possible combinations of inputs**. 

!!! question "Try Solving this !!!"
    
    === "Question"
        Determine the Boolean expression that represents the entire logic circuit below, in addition construct the truth table based on that Boolean expression:

        <div align="center">
            <img src="https://github.com/JoshuaOhYQ/BEEE/blob/c42a169109795617a81924a0f1124dc8d7fd8648/docs/ETC3143%20Advanced%20Digital%20Design/Fundamentals/Question1.png?raw=true" alt="Logic Circuit Diagram" width="600">
        </div>

    === "Answer"
        ### Boolean Expression Analysis

        Let's analyze the logic circuit step by step:

        1. **First NOR Gate**: Takes inputs A and B
           - Output = $\overline{A + B}$

        2. **AND Gate**: Takes inputs C and D
           - Output = $C \cdot D$

        3. **Second NOR Gate**: Takes the output from AND gate
           - Output = $\overline{C \cdot D}$

        4. **Final AND Gate**: Takes outputs from first NOR gate and second NOR gate
           - Output Y = $\overline{A+B} \cdot \overline{C \cdot D}$

        Therefore, the **Boolean Expression** is:
        
        $$\boxed{Y = \overline{A+B} \cdot \overline{C \cdot D}}$$

        ### Truth Table

        | A | B | C | D | $\overline{A+B}$ | $C \cdot D$ | $\overline{C \cdot D}$ | $Y = \overline{A+B} \cdot \overline{C \cdot D}$ |
        |:-:|:-:|:-:|:-:|:-----------------:|:-----------:|:----------------------:|:-----------------------------------------------:|
        | 0 | 0 | 0 | 0 | 1 | 0 | 1 | 1 |
        | 0 | 0 | 0 | 1 | 1 | 0 | 1 | 1 |
        | 0 | 0 | 1 | 0 | 1 | 0 | 1 | 1 |
        | 0 | 0 | 1 | 1 | 1 | 1 | 0 | 0 |
        | 0 | 1 | 0 | 0 | 0 | 0 | 1 | 0 |
        | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 0 |
        | 0 | 1 | 1 | 0 | 0 | 0 | 1 | 0 |
        | 0 | 1 | 1 | 1 | 0 | 1 | 0 | 0 |
        | 1 | 0 | 0 | 0 | 0 | 0 | 1 | 0 |
        | 1 | 0 | 0 | 1 | 0 | 0 | 1 | 0 |
        | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 0 |
        | 1 | 0 | 1 | 1 | 0 | 1 | 0 | 0 |
        | 1 | 1 | 0 | 0 | 0 | 0 | 1 | 0 |
        | 1 | 1 | 0 | 1 | 0 | 0 | 1 | 0 |
        | 1 | 1 | 1 | 0 | 0 | 0 | 1 | 0 |
        | 1 | 1 | 1 | 1 | 0 | 1 | 0 | 0 |

        ### Simplified Result

        The output Y is **HIGH (1)** only when:
        - A = 0 AND B = 0 (so $\overline{A+B} = 1$), AND
        - NOT (C = 1 AND D = 1) (so $\overline{C \cdot D} = 1$)

        In all other cases, Y = 0.

        $$\boxed{Y = \overline{A+B} \cdot \overline{CD}}$$
        

    