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

        1. **First NOR Gate** (Top): Takes inputs A and B
           - Output X = $\overline{A + B}$

        2. **AND Gate** (Middle): Takes inputs C and D
           - Output Z = $C \cdot D$

        3. **Second NOR Gate** (Bottom): Takes X and Z as inputs
           - The expression $\overline{(A + B)(C \cdot D)}$ is incorrect notation
           - Actually, this NOR gate takes the outputs from previous gates:
           - Inputs to this NOR gate are: $\overline{A+B}$ and $C \cdot D$
           - Therefore, output = $\overline{(\overline{A+B}) + (C \cdot D)}$

        4. **OR Gate** (Final): Takes X and the output from the second NOR gate
           - First input = $\overline{A+B}$
           - Second input = $\overline{(\overline{A+B}) + (C \cdot D)}$
           - Output Y = $\overline{A+B} + \overline{(\overline{A+B}) + (C \cdot D)}$

        Therefore, the **Boolean Expression** is:
        
        $$\boxed{Y = \overline{A+B} \;+\; \overline{(\overline{A+B}) + (C \cdot D)}}$$

        This matches: $Y = \overline{A + B} + [\overline{(A + B)(C \cdot D)}]$ ✓

        ### Truth Table

        | A | B | C | D | $\overline{A+B}$ | $C \cdot D$ | $\overline{(\overline{A+B}) + (C \cdot D)}$ | $Y = \overline{A+B} + \overline{(\overline{A+B}) + (C \cdot D)}$ |
        |:-:|:-:|:-:|:-:|:-----------------:|:-----------:|:------------------------------------------:|:---------------------------------------------------------------:|
        | 0 | 0 | 0 | 0 | 1 | 0 | $\overline{1 + 0} = \overline{1} = 0$ | 1 + 0 = **1** |
        | 0 | 0 | 0 | 1 | 1 | 0 | $\overline{1 + 0} = \overline{1} = 0$ | 1 + 0 = **1** |
        | 0 | 0 | 1 | 0 | 1 | 0 | $\overline{1 + 0} = \overline{1} = 0$ | 1 + 0 = **1** |
        | 0 | 0 | 1 | 1 | 1 | 1 | $\overline{1 + 1} = \overline{1} = 0$ | 1 + 0 = **1** |
        | 0 | 1 | 0 | 0 | 0 | 0 | $\overline{0 + 0} = \overline{0} = 1$ | 0 + 1 = **1** |
        | 0 | 1 | 0 | 1 | 0 | 0 | $\overline{0 + 0} = \overline{0} = 1$ | 0 + 1 = **1** |
        | 0 | 1 | 1 | 0 | 0 | 0 | $\overline{0 + 0} = \overline{0} = 1$ | 0 + 1 = **1** |
        | 0 | 1 | 1 | 1 | 0 | 1 | $\overline{0 + 1} = \overline{1} = 0$ | 0 + 0 = **0** |
        | 1 | 0 | 0 | 0 | 0 | 0 | $\overline{0 + 0} = \overline{0} = 1$ | 0 + 1 = **1** |
        | 1 | 0 | 0 | 1 | 0 | 0 | $\overline{0 + 0} = \overline{0} = 1$ | 0 + 1 = **1** |
        | 1 | 0 | 1 | 0 | 0 | 0 | $\overline{0 + 0} = \overline{0} = 1$ | 0 + 1 = **1** |
        | 1 | 0 | 1 | 1 | 0 | 1 | $\overline{0 + 1} = \overline{1} = 0$ | 0 + 0 = **0** |
        | 1 | 1 | 0 | 0 | 0 | 0 | $\overline{0 + 0} = \overline{0} = 1$ | 0 + 1 = **1** |
        | 1 | 1 | 0 | 1 | 0 | 0 | $\overline{0 + 0} = \overline{0} = 1$ | 0 + 1 = **1** |
        | 1 | 1 | 1 | 0 | 0 | 0 | $\overline{0 + 0} = \overline{0} = 1$ | 0 + 1 = **1** |
        | 1 | 1 | 1 | 1 | 0 | 1 | $\overline{0 + 1} = \overline{1} = 0$ | 0 + 0 = **0** |

        ### Simplified Result

        The output Y = **0** only when:
        - A = 0, B = 1, C = 1, D = 1 OR
        - A = 1, B = 0, C = 1, D = 1 OR
        - A = 1, B = 1, C = 1, D = 1

        In all other 13 combinations, Y = **1**.

        $$\boxed{Y = \overline{A+B} + \overline{(\overline{A+B}) + CD}}$$
        

    