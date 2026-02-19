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

        The **Boolean Expression** is:
        
        $$
        \boxed{
        Y = \overline{(A+B)} + \Big[\overline{(A+B)} \cdot \overline{(C \cdot D)}\Big]
        }
        $$

        The Truth Table is:

        | A | B | C | D | $\overline{(A+B)}$ | $\overline{(C \cdot D)}$ | $\overline{(A+B)} \cdot \overline{(C \cdot D)}$ | $Y = \overline{(A+B)} + [\overline{(A+B)} \cdot \overline{(C \cdot D)}]$ |
        |:-:|:-:|:-:|:-:|:------------------:|:------------------------:|:-----------------------------------------------:|:-----------------------------------------------------------------------:|
        | 0 | 0 | 0 | 0 | 1 | 1 | 1 | 1 + 1 = **1** |
        | 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1 + 1 = **1** |
        | 0 | 0 | 1 | 0 | 1 | 1 | 1 | 1 + 1 = **1** |
        | 0 | 0 | 1 | 1 | 1 | 0 | 0 | 1 + 0 = **1** |
        | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 + 0 = **0** |
        | 0 | 1 | 0 | 1 | 0 | 1 | 0 | 0 + 0 = **0** |
        | 0 | 1 | 1 | 0 | 0 | 1 | 0 | 0 + 0 = **0** |
        | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 + 0 = **0** |
        | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 0 + 0 = **0** |
        | 1 | 0 | 0 | 1 | 0 | 1 | 0 | 0 + 0 = **0** |
        | 1 | 0 | 1 | 0 | 0 | 1 | 0 | 0 + 0 = **0** |
        | 1 | 0 | 1 | 1 | 0 | 0 | 0 | 0 + 0 = **0** |
        | 1 | 1 | 0 | 0 | 0 | 1 | 0 | 0 + 0 = **0** |
        | 1 | 1 | 0 | 1 | 0 | 1 | 0 | 0 + 0 = **0** |
        | 1 | 1 | 1 | 0 | 0 | 1 | 0 | 0 + 0 = **0** |
        | 1 | 1 | 1 | 1 | 0 | 0 | 0 | 0 + 0 = **0** |


        

    