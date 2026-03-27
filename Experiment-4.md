# **Experiment 4: MOS Differential Amplifier Design and Analysis**

## **Aim**

Design and analyze a MOS differential amplifier circuit for the following specifications:

- **Supply Voltage (VDD):** +0.9 V  
- **Negative Supply (VSS):** −0.9 V
- **Tail node voltage (Vp):** -0.7 V 
- **Maximum Power (P):** ≤ 1.8 mW  
- **Channel Length (L):** 480 nm  
- **Input Common Mode Voltage (VinCM):** 0 V  
- **Output Common Mode Voltage (VoCM):** 0 V
## **Introduction**

A **Differential Amplifier** is a fundamental building block in analog electronics that amplifies the **difference between two input signals** while rejecting any signal common to both inputs.

It is widely used in:

- Operational Amplifiers (Op-Amps)
- Comparators
- Analog signal processing circuits
- Communication systems

The key advantage of a differential amplifier is its ability to **eliminate noise and interference**, since noise usually appears as a common signal on both inputs.



## **Theory of Differential Amplifier**

A differential amplifier operates on the principle of **difference amplification**:

- Two input signals: \( V_{in1} \) and \( V_{in2} \)
- Output depends on:

\[
V_{out} \propto (V_{in1} - V_{in2})
\]

### **Ideal Behavior**

- If \( V_{in1} = V_{in2} \) → Output = 0  
- If \( V_{in1} > V_{in2} \) → Positive output  
- If \( V_{in1} < V_{in2} \) → Negative output  



## **Working Principle**

A MOS differential amplifier consists of:

- Two NMOS transistors (M1, M2)
- A constant current source (tail current)
- Load elements (resistors or active loads)

### **Step-by-Step Working**

1. **Equal Inputs (Balanced Condition)**
   - \( V_{in1} = V_{in2} \)
   - Current splits equally:
     - \( I_1 = I_2 = I_{tail}/2 \)
   - Output voltages are equal → Differential output = 0

2. **Differential Input Applied**
   - When \( V_{in1} > V_{in2} \):
     - M1 conducts more current
     - M2 conducts less current
   - This creates a voltage difference at outputs

3. **Current Steering**
   - Tail current remains constant
   - Current is redistributed between M1 and M2

4. **Voltage Conversion**
   - Load resistors convert current difference into voltage difference



## **Types of Differential Amplifiers**

### **1. BJT Differential Amplifier**
- Uses bipolar junction transistors
- High gain but higher power consumption



### **2. MOS Differential Amplifier**
- Uses MOSFETs
- Low power consumption
- Widely used in IC design



### **3. Resistive Load Differential Amplifier**
- Uses resistors as load
- Simple design but lower gain



### **4. Active Load Differential Amplifier**
- Uses current mirror loads
- Provides higher gain



### **5. Single-Ended Output Differential Amplifier**
- Output taken from one side only



### **6. Double-Ended Output Differential Amplifier**
- Output taken as difference of two nodes
- Better noise immunity



## **Modes of Operation**

### **1. Differential Mode**
- Inputs are opposite signals
- Amplifies difference
- Desired mode



### **2. Common Mode**
- Inputs are equal
- Ideally no output
- Measures noise rejection capability
  
#  Circuit Design Calculations



##  Given Specifications

- $V_{DD} = 0.9\text{ V}$
- $V_{SS} = -0.9\text{ V}$
- $P \le 1.8\text{ mW}$
- $V_{p} = -0.7\text{ V}$
- $V_{inCM} = 0\text{ V}$
- $V_{oCM} = 0\text{ V}$



##  1. Calculation of Total Current

Since the circuit uses dual supply, total voltage is:

$$
V_{total} = V_{DD} - V_{SS}
$$

$$
V_{total} = 0.9 - (-0.9) = 1.8\text{ V}
$$



Using power relation:

$$
P = (V_{DD} - V_{SS}) \cdot I_{total}
$$

$$
I_{total} = \frac{P}{V_{DD} - V_{SS}}
$$

$$
I_{total} = \frac{1.8\text{ mW}}{1.8\text{ V}} = 1\text{ mA}
$$



**Final:**

$$
I_{total} = I_{tail} = 1\text{ mA}
$$



##  2. Current in Each Branch

$$
I_D = \frac{I_{tail}}{2}
$$

$$
I_D = \frac{1\text{ mA}}{2} = 0.5\text{ mA}
$$

##  3. Calculation of Load Resistance $R_D$

Using output common-mode condition:

$$
V_{oCM} = V_{DD} - I_D \cdot R_D
$$

Given:

$$
V_{oCM} = 0\text{ V}
$$



Substituting values:

$$
0 = 0.9 - (0.5\text{ mA} \cdot R_D)
$$



Solving:

$$
0.5\text{ mA} \cdot R_D = 0.9
$$

$$
R_D = \frac{0.9}{0.5 \times 10^{-3}}
$$

$$
R_D = 1800\ \Omega
$$



**Final:**

$$
R_D = 1.8\text{ k}\Omega
$$

##  Technology Parameters (TSMC 0.18µm)

Technology parameters are taken from `tsmc018.lib`.



###  Extracted Parameters

- Threshold Voltage (NMOS):

$$
V_{THn} = 0.366\ \text{V}
$$



- Oxide Thickness:

$$
t_{ox} = 4.1 \times 10^{-9}\ \text{m}
$$



- Oxide Permittivity:

$$
\varepsilon_{ox} = 3.9 \times 8.854 \times 10^{-12}\ \text{F/m}
$$

$$
\varepsilon_{ox} = 3.453 \times 10^{-11}\ \text{F/m}
$$



- Electron Mobility:

$$
\mu_n = 115.689\ \text{cm}^2/\text{V·s}
$$

$$
\mu_n = 115.689 \times 10^{-4}\ \text{m}^2/\text{V·s}
$$

$$
\mu_n = 0.0115689\ \text{m}^2/\text{V·s}
$$



##  Derived Parameter: Oxide Capacitance ($C_{ox}$)

Using:

$$
C_{ox} = \frac{\varepsilon_{ox}}{t_{ox}}
$$

Substitute values:

$$
C_{ox} = \frac{3.453 \times 10^{-11}}{4.1 \times 10^{-9}}
$$

$$
C_{ox} = 8.42 \times 10^{-3}\ \text{F/m}^2
$$




##  4. Gate-Source Voltage ($V_{GS}$)

$$
V_{inCM} = V_{GS} + V_p
$$

Rearranging:

$$
V_{GS} = V_{inCM} - V_p
$$

$$
V_{GS} = 0 - (-0.7)
$$

$$
V_{GS} = 0.7\ \text{V}
$$



##  5. Overdrive Voltage ($V_{OV}$)

$$
V_{OV} = V_{GS} - V_{THn}
$$

$$
V_{OV} = 0.7 - 0.366 = 0.334\ \text{V}
$$



##  6. Calculation of Width ($W$)

Using saturation current equation:

$$
I_D = \frac{1}{2} \mu_n C_{ox} \frac{W}{L} V_{OV}^2
$$



Rearranging for $W$:

$$
W = \frac{2 I_D L}{\mu_n C_{ox} V_{OV}^2}
$$



### Substitute values:

$$
W = \frac{2 \times 0.0005 \times (480 \times 10^{-9})}{0.0115689 \times (8.42 \times 10^{-3}) \times (0.334)^2}
$$

$$
W \approx 4.4160 \times 10^{-5}\ \text{m}
$$



### Final Width:

$$
W \approx 44.160\ \mu\text{m}
$$



##  Saturation Condition Check

Condition for MOSFET to remain in saturation:

$$
V_{DS} > V_{OV}
$$



### From circuit:

- $V_D = V_{out} = 0\ \text{V}$
- $V_S = V_p \approx -0.7\ \text{V}$ (approx)

$$
V_{DS} = V_D - V_S
$$

$$
V_{DS} = 0 - (-0.7) = 0.7\ \text{V}
$$



### Compare:

$$
V_{DS} = 0.7\ \text{V}, \quad V_{OV} = 0.334\ \text{V}
$$



### Result:

$$
V_{DS} \geq V_{OV}
$$

✔ Transistor operates in **saturation region**

### CIRCUIT DIAGRAM :
![WhatsApp Image 2026-03-27 at 3 08 09 AM](https://github.com/user-attachments/assets/a31bfa15-a81a-4a22-a9f4-0856acd09761)

### DC ANALYSIS ( OPERATING POINT ) :

***BEFORE TUNNING*** :

$$
W = 44.160um
$$

![WhatsApp Image 2026-03-26 at 10 46 33 PM](https://github.com/user-attachments/assets/1def6dd8-e9f0-4441-b62d-4f0f4eb6a23c)

***AFTER TUNNING*** :

$$
W = 29.475um
$$

![WhatsApp Image 2026-03-26 at 10 47 47 PM](https://github.com/user-attachments/assets/117bf80f-4b5c-4e8f-9e49-dad9002ff232)



### Results Before and After Tuning

| Parameter | Before Tuning | After Tuning |
|----------|--------------|-------------|
| Width ($W$) | 44.160 µm | 29.475 µm |
| Drain Current ($I_D$) | 0.5 mA (M1, M2) | 0.5 mA (M1, M2) |
| Tail Node Voltage ($V_p$) | -0.652104 V | -0.7 V |
| Output Voltage ($V_{out}$) | $8.859 \times 10^{-17}$ V (≈ 0) | $7.02456 \times 10^{-17}$ V (≈ 0) |


##  Common Mode Analysis

#  1. Input Common Mode Range (ICMR)

##  Minimum Input Common Mode Voltage

Condition: Tail current source must remain in saturation

$$
V_{inCM(min)} = V_{T} + V_{p}
$$

Substitute:

$$
V_{inCM(min)} = 0.366 - 0.7
$$

$$
V_{inCM(min)} = -0.334\text{ V}
$$

![WhatsApp Image 2026-03-27 at 12 25 46 AM](https://github.com/user-attachments/assets/e9c693b0-d0c5-4192-8355-0c6d0ac58069)





##  Maximum Input Common Mode Voltage

Condition: M1, M2 must remain in saturation

$$
V_{DS} \geq V_{OV}
$$

Drain voltage:

$$
V_D = V_{DD} - I_D R_D
$$

$$
V_D = 0.9 - (0.5\text{ mA} \times 1.8\text{ k}\Omega)
$$

$$
V_D = 0.9 - 0.9 = 0\text{ V}
$$



Now:

$$
V_{inCM(max)} = V_D + V_{TH}
$$

$$
V_{inCM(max)} = 0 + 0.366
$$

$$
V_{inCM(max)} = 0.366\text{ V}
$$

![WhatsApp Image 2026-03-27 at 12 34 46 AM](https://github.com/user-attachments/assets/44af00cd-a649-478b-bbf0-595a893530f9)



#  2. Output Common Mode Range



##  Maximum Output Voltage

When transistor is just in saturation:

$$
V_{oCM(max)} = V_{DD}
$$

$$
V_{oCM(max)} = 0.9\text{ V}
$$



##  Minimum Output Voltage

Condition:

$$
V_{DS} \geq V_{OV}
$$

$$
V_{oCM(min)} = V_S + V_{OV}
$$

Source voltage:

$$
V_S = - 0.7 = -0.7\text{ V}
$$



Now:

$$
V_{oCM(min)} = -0.7 + 0.334
$$

$$
V_{oCM(min)} = -0.366\text{ V}
$$



#  Final Results

| Parameter | Value |
|----------|------|
| $V_{inCM(min)}$ | -0.334 V |
| $V_{inCM(max)}$ | 0.366 V |
| $V_{oCM(min)}$ | -0.366 V |
| $V_{oCM(max)}$ | 0.9 V |





































 
