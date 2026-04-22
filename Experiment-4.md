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

  ---
  
#  1) Circuit Design Calculations



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

Transistor operates in **saturation region**

---

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


---


## TRANSIENT ANALYSIS :

##  Common Mode Analysis

#  1. Input Common Mode Range (ICMR)

##  Minimum Input Common Mode Voltage 

It is the minimum input common-mode voltage at which the differential amplifier just starts to operate properly.

 At this Condition:
 1. * Tail current source just remains active
    
    * The tail transistor (or current source) is just in saturation
    
    * It is at the edge of operation
    
    * Any further decrease → it goes to triode region

2. Input transistors (M1, M2):

  * Still in saturation
But operating at minimum allowed gate voltage

3. Source node voltage (Vp):

 * Becomes very low (more negative)
This reduces: VGS

 4. If VinCM goes BELOW this:

* Tail current source enters triode region

* Current becomes unstable

* Differential pair loses proper operation

* Amplifier stops working correctly

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

just below the VinCM (min)

![WhatsApp Image 2026-03-27 at 12 56 36 AM](https://github.com/user-attachments/assets/181cb522-4b7c-4726-a8d1-31897d811ac9)

At V_{inCM(min)} :
Output waveform → just starts distorting

Below this:
Output becomes flat / incorrect ,
No proper amplification



##  Maximum Input Common Mode Voltage

It is the maximum input common-mode voltage at which the differential amplifier still operates properly (in the saturation region).

At this Condition:

###  1. Input Transistors (M1, M2)

- Are just at the **edge of saturation**  
- Drain voltage is just enough to satisfy:

$$
V_{DS} \geq V_{OV}
$$

- Any further increase in $V_{inCM}$ → transistors enter **triode region**



###  2. Drain Voltage ($V_{out}$)

- Becomes **very low**

Because:

- Higher $V_{inCM}$ → higher drain current ($I_D$)  
- Larger voltage drop across $R_D$  

$$
V_{out} = V_{DD} - I_D R_D
$$

 So, $V_{out}$ decreases



###  3. If $V_{inCM}$ Goes ABOVE This

- Input transistors (M1, M2) enter **triode region**  
- They stop behaving like amplifiers 
- Gain drops drastically  


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

just above the V_{inCM(max)}

![WhatsApp Image 2026-03-27 at 12 58 55 AM](https://github.com/user-attachments/assets/ffce14f9-cab7-4922-8b4a-717b92b4bf49)



###  At $V_{inCM(max)}$

- Output waveform **just starts clipping (top side)**  



###  Above $V_{inCM(max)}$

The output becomes:

- Distorted   
- Flattened   
- Non-linear  



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



## Final Conclusion – Input Common Mode Limits

The proper operation of a differential amplifier is strictly limited by the input common-mode voltage range defined by $V_{inCM(min)}$ and $V_{inCM(max)}$.

- At $V_{inCM(min)}$, the tail current source is at the edge of saturation. Any further decrease causes it to enter the triode region, resulting in loss of constant current and improper circuit operation.

- At $V_{inCM(max)}$, the input transistors (M1, M2) are at the boundary of saturation. Any further increase drives them into the triode region, leading to reduced gain and output distortion.

 Therefore, the differential amplifier operates correctly only within this input common-mode range, where:

- All transistors remain in saturation  
- Proper current distribution is maintained  
- Linear amplification is achieved  



##  Final Statement:

The range

$$
V_{inCM(min)} \le V_{inCM} \le V_{inCM(max)}
$$

defines the safe and linear operating region of the differential amplifier. Outside this range, the circuit loses its amplification capability and becomes non-linear.

---

##  Differential Input Range ($v_{id}$) for Linear Operation


The differential input voltage is:

$$
v_{id} = v_{in1} - v_{in2}
$$

The circuit behaves as a **linear amplifier** only when both transistors (M1, M2) remain in saturation and share current smoothly.



##  Condition for Linear Operation

For a MOS differential pair:

$$
|v_{id}| \le 2 V_{OV}
$$



###  Given

- $V_{OV} = 0.334\ \text{V}$



##  Calculate $v_{id}$ Range

$$
|v_{id}| \le 2 \times 0.334
$$

$$
|v_{id}| \le 0.668\ \text{V}
$$



##  Final Range

$$
-0.668\ \text{V} \le v_{id} \le 0.668\ \text{V}
$$



##  Practical Linear Region 

 For **strictly linear behavior** (no distortion):

$$
|v_{id}| \ll 2 V_{OV}
$$

Typically:

$$
|v_{id}| \le 0.1\text{ to }0.2\ \text{V}
$$





 $V_{id} = 100\ \text{mV}$
 ![WhatsApp Image 2026-03-27 at 1 50 16 AM](https://github.com/user-attachments/assets/29f5fb8a-d81e-4d6f-b60f-95a4a32ff568)

 
 $V_{id} = 600\ \text{mV}$
 ![WhatsApp Image 2026-03-27 at 1 52 27 AM](https://github.com/user-attachments/assets/4245036c-82e9-481c-b1a8-f012219093eb)



##  What Happens Outside This Range

- One transistor carries almost all current  
- Other transistor turns OFF  
- Circuit behaves like a **switch**, not amplifier   
- Output becomes non-linear and distorted
 
 $V_{id} = 1400\ \text{mV}$
 ![WhatsApp Image 2026-03-27 at 1 56 08 AM](https://github.com/user-attachments/assets/4aa41fb0-f594-4c0b-94a6-1d7e6175bf8a)

 

  
##  Conclusion

- Theoretical range: $\pm 0.668\ \text{V}$  
- Practical linear range: **much smaller (~±0.1–0.2 V)**  
- Within this range:
  - Both transistors remain in saturation  
  - Current splits smoothly  
  - Amplification is linear  
---
## Transient Gain Calculation :

Input Signal:
Vin1 = SINE(0 50m 1k)
Vin2 = SINE(0 -50m 1k)

<img width="1919" height="891" alt="image" src="https://github.com/user-attachments/assets/93d3da09-b8b8-464c-8931-d03bbfceaf21" />

Measured Values:

Vin (peak-to-peak)  = 100mV

Vout (peak-to-peak) = 608.2mV

Practical Gain:

Av = Vout / Vin

Av = 608.2mv/ 100mv

Av = 6.082 V/V

Gain in dB:

Av(dB) = 20 log10( 6.082 )

Av(dB) ≈ 15.680 dB

##  Gain Calculation Using Small-Signal Analysis



##  1. Small-Signal Model

For a MOS differential pair:

- Each transistor contributes transconductance $g_m$  
- Output is taken as differential:

$$
v_{out} = v_{out1} - v_{out2}
$$



## 2. Differential Gain Formula

$$
A_d = g_m \cdot R_D
$$


##  3. Calculate Transconductance ($g_m$)

Using:

$$
g_m = \frac{2 I_D}{V_{OV}}
$$



###  Given

- $I_D = 0.5\ \text{mA} = 0.0005\ \text{A}$  
- $V_{OV} = 0.334\ \text{V}$  



###  Calculation

$$
g_m = \frac{2 \times 0.0005}{0.334}
$$

$$
g_m = \frac{0.001}{0.334}
$$

$$
g_m \approx 2.99 \times 10^{-3}\ \text{S}
$$

$$
g_m \approx 2.99\ \text{mS}
$$



##  4. Calculate Gain ($A_d$)

Given:

- $R_D = 1.8\ \text{k}\Omega = 1800\ \Omega$



$$
A_d = g_m \cdot R_D
$$

$$
A_d = 2.99 \times 10^{-3} \times 1800
$$

$$
A_d \approx 5.382
$$



##  Final Gain

$$
A_d \approx 5.382\ \text{V/V}
$$



##  Gain in dB

$$
A_d(dB) = 20 \log_{10}(A_d)
$$

$$
A_d(dB) = 20 \log_{10}(5.382)
$$

$$
A_d(dB) \approx 14.618\ \text{dB}
$$


- Differential gain = **5.382 V/V**  
- Gain = **14.618 dB**

  ## Transient Analysis – Linear vs Non-Linear Behavior

##  Circuit Setup

- Load Capacitor:

$$
C_L = 10\text{ pF} \quad (\text{connected from each output to ground})
$$

- Differential input:

Vin1 = SINE(0 A 1k)  
Vin2 = SINE(0 -A 1k)

$$
V_{id} = 2A
$$

![WhatsApp Image 2026-03-27 at 2 08 48 AM](https://github.com/user-attachments/assets/69d27f3b-0823-4f2d-8fc6-e49d58768a6f)


##  1. Case 1: $V_{id} < \sqrt{2} V_{OV}$ (Linear Region)

###  Condition:

$$
\sqrt{2} V_{OV} = 0.472\text{ V}
$$

Choose:

$$
V_{id} = 0.2\text{ V} \Rightarrow A = 0.1\text{ V}
$$



###  Input:

Vin1 = SINE(0 0.1 1k)  
Vin2 = SINE(0 -0.1 1k)

![WhatsApp Image 2026-03-27 at 2 09 47 AM](https://github.com/user-attachments/assets/600d22a3-fcb9-427e-8f65-b6d1d6b2b25f)


###  Observation:

- Output waveform is clean sinusoidal  
- No distortion  
- Both transistors conduct  

##  2. Case 2: $V_{id} > \sqrt{2} V_{OV}$ (Non-Linear Region)

Choose:

$$
V_{id} = 0.8\text{ V} \Rightarrow A = 0.4\text{ V}
$$



###  Input:

Vin1 = SINE(0 0.4 1k)  
Vin2 = SINE(0 -0.4 1k)

![WhatsApp Image 2026-03-27 at 2 13 16 AM](https://github.com/user-attachments/assets/ddca22e2-a8c4-4f1e-895f-59b991c3d186)


###  Observation:

- Output waveform is distorted  
- Peaks are flattened (clipping)  
 



##  3. Comparison

| Parameter | Linear Region | Non-Linear Region |
|----------|--------------|------------------|
| Condition | $V_{id} < \sqrt{2} V_{OV}$ | $V_{id} > \sqrt{2} V_{OV}$ |
| Output | Clean sine wave | Distorted waveform |
| Transistor Operation | Both ON | One OFF |
| Current Distribution | Shared | Fully steered |
| Gain | Constant | Reduced / non-linear |

## Final Conclusion 

The transient analysis of the MOS differential amplifier clearly distinguishes between linear and non-linear regions of operation based on the differential input voltage $v_{id}$.

- In the **linear region** ($v_{id} < \sqrt{2} V_{OV}$), both transistors (M1 and M2) operate in saturation and share the tail current smoothly. As a result, the output is a clean sinusoidal waveform with constant gain, and the circuit behaves as a **linear amplifier**.

- In the **non-linear region** ($v_{id} > \sqrt{2} V_{OV}$), one transistor carries almost the entire tail current while the other turns OFF. This leads to current steering, causing distortion, clipping, and non-linear output behavior. The circuit no longer acts as an amplifier but behaves like a **switching circuit**.



##  Key Insight

- Linearity is maintained only when both transistors conduct simultaneously and remain in saturation.

- Once the input exceeds the limit, the differential pair loses its linear relationship between input and output.



## Final Statement

The condition

$$
v_{id} < \sqrt{2} V_{OV}
$$

defines the **linear operating region** of the differential amplifier. Beyond this range, the circuit enters the non-linear region, resulting in distortion and loss of amplification capability.

---
##  AC Analysis
AC analysis determines frequency response.

##  Circuit Setup
   Set AC amplitude: = 1  
 
  <img width="1919" height="920" alt="image" src="https://github.com/user-attachments/assets/f1cfe936-6e5a-4dc2-a2a1-604f4b2d376f" />
  
  Midband Gain = 15.892 dB
  
 -3 dB Cutoff Frequency:

  ![WhatsApp Image 2026-03-27 at 2 36 37 AM](https://github.com/user-attachments/assets/8d9ff4b4-d81e-47ca-b877-e85a0b05fbf1)
  
Upper Cutoff Frequency fH  = 9.606 MHz 

Lower Cutoff Frequency fL = 0 Hz

**Bandwidth :**

BW = fH − fL

BW =  9.606 MHz 

**Gain :** 
- Therotical Gain = **14.618 dB**
- Practical Gain = **15.892 dB**

##  Unity Gain Bandwidth (UGB)


Unity Gain Bandwidth (UGB) is the frequency at which the gain of the amplifier becomes:

$$
A_v = 1 \quad (0\text{ dB})
$$

<img width="1919" height="901" alt="Screenshot 2026-03-27 224857" src="https://github.com/user-attachments/assets/4586a773-4a1c-4ff6-8ce5-442f86503609" />


###  From AC Analysis Graph

- The gain curve crosses **0 dB** at approximately:

$$
UGB \approx 58.3\ \text{MHz}
$$

---

###  Interpretation

- Below UGB → amplifier provides gain (>1)  
- At UGB → gain becomes unity  
- Above UGB → gain < 1 (attenuation region)  

---

###  Key Insight

- UGB represents the **maximum useful frequency** of the amplifier.

- It indicates the **speed of the amplifier**:

- Higher UGB → faster amplifier  
- Lower UGB → slower response
  
## Gain Bandwidth Product (GBP)

Gain Bandwidth Product (GBP) is defined as:

$$
GBP = A_v \times BW
$$

It represents the product of the midband gain and the bandwidth of the amplifier.



###  Given (From AC Analysis)

- Gain:

$$
A_v \approx 6.232\ \text{V/V}
$$

- Bandwidth:

$$
BW \approx 9.606\ \text{MHz}
$$



###  Calculation
$$
GBP \approx 59.86\ \text{MHz}
$$




###  Interpretation

- GBP remains approximately **constant** for a given amplifier  
- If gain increases → bandwidth decreases  
- If bandwidth increases → gain decreases  


###  Key Insight

- GBP defines the **performance limit** of the amplifier.

 It shows the trade-off between:
- Gain  
- Bandwidth

  ---
  ## Final Results and Inference



##  Final Results

###  DC Design Results

| Parameter | Value |
|----------|------|
| Tail Current ($I_{tail}$) | 1 mA |
| Drain Current ($I_D$) | 0.5 mA |
| Load Resistance ($R_D$) | 1.8 k$\Omega$ |
| Overdrive Voltage ($V_{OV}$) | 0.334 V |
| Final Width ($W$) | 29.475 µm |

---

###  Common Mode Range

| Parameter | Value |
|----------|------|
| $V_{inCM(min)}$ | -0.334 V |
| $V_{inCM(max)}$ | 0.366 V |
| $V_{oCM(min)}$ | -0.366 V |
| $V_{oCM(max)}$ | 0.9 V |

---

###  Differential Input Range

$$
-0.668\text{ V} \le v_{id} \le 0.668\text{ V}
$$

- Practical linear range: **±0.1 to 0.2 V**

---

###  Gain Results

| Type | Value |
|------|------|
| Theoretical Gain | 5.382 V/V (14.618 dB) |
| Practical Gain (Transient) | 6.082 V/V (15.68 dB) |
| AC Gain | 15.892 dB |

---

###  Frequency Response

| Parameter | Value |
|----------|------|
| Bandwidth (BW) | 9.606 MHz |
| Unity Gain Bandwidth (UGB) | 58.3 MHz |
| Gain Bandwidth Product (GBP) | 59.86 MHz |

---

##  Inference

---

###  1. Design Verification

- The circuit satisfies all given specifications:
  - Low power operation (≤ 1.8 mW)  
  - Symmetrical output ($V_{out} \approx 0$)  
  - Proper biasing ($V_p = -0.7$ V)  

 All MOSFETs operate in **saturation region**

---

###  2. Linearity Behavior

- For small differential input:
  - Both transistors conduct  
  - Current is shared  
  - Output is linear  

- For large input:
  - One transistor turns OFF  
  - Current steering occurs  
  - Output becomes distorted  

- Confirms that the differential pair behaves as:
  - **Amplifier (linear region)**
  - **Switch (non-linear region)**

---

###  3. Common Mode Analysis Insight

- Proper operation is restricted to:

$$
V_{inCM(min)} \le V_{inCM} \le V_{inCM(max)}
$$

- Outside this range:
  - Tail current source fails (low side)  
  - Input transistors leave saturation (high side)  

 This defines the **safe operating region**

---

###  4. Gain Analysis Insight

- Practical gain is slightly higher than theoretical:
  - Due to device non-idealities  
  - Model accuracy in LTspice  

 Confirms correctness of:
- Small-signal model  
- gm-based analysis  

---

###  5. Frequency Response Insight

- Gain remains constant in midband  
- Drops after cutoff frequency due to:
  - Load capacitance ($C_L$)  
  - Parasitic capacitances  

- UGB ≈ GBP → validates amplifier behavior  

 Shows **gain-bandwidth trade-off**

---

###  6. Overall Performance

- Moderate gain (~15 dB)  
- Good bandwidth (~10 MHz)  
- High UGB (~58 MHz)  

 Suitable for:
- Low-voltage analog applications  
- High-speed signal processing  

---

##  Final Conclusion

The MOS differential amplifier is successfully designed and analyzed. The circuit operates correctly within the defined input common-mode and differential input ranges, maintaining all transistors in saturation. 

The results from DC, transient, and AC analyses confirm that the amplifier provides linear amplification for small inputs and exhibits non-linear behavior for large inputs due to current steering. The frequency response validates the expected gain-bandwidth trade-off.

---

##  Final Statement

The design meets all specifications and demonstrates the fundamental operation of a MOS differential amplifier as both a **linear amplifier** and a **non-linear switching device**, depending on the input conditions.

---
# CIRCUIT 2 
**CIRCUIT DIAGRAM**
<img width="1182" height="877" alt="Screenshot 2026-03-29 001109" src="https://github.com/user-attachments/assets/9011a0dd-df8e-4954-b8f0-1223d60cce69" />


# Circuit Design Calculations

## Given Specifications
- VDD = 0.9 V  
- VSS = −0.9 V  
- Maximum Power P ≤ 1.8 mW  
- Tail node voltage Vp = −0.7 V  
- Input common mode voltage VinCM = 0 V  
- Channel length L = 480 nm  

### Technology Parameters (TSMC 0.18 µm)

**NMOS**
- Threshold voltage VTHn = 0.366 V  
- Electron mobility μn = 0.0115689 m²/V·s  

**PMOS**
- Threshold voltage |VTHp| ≈ 0.39 V  
- Hole mobility μp = 0.02738 m²/V·s  

**Oxide Capacitance**
- εox = 3.453 × 10⁻¹¹ F/m  
- tox = 4.1 × 10⁻⁹ m  
- Cox = 8.42 × 10⁻³ F/m²  



## 1. Total Current Calculation
P = (VDD − VSS) × Itotal  

1.8 mW = 1.8 × Itotal  

**Itotal = 1 mA**



## 2. Current Distribution
- Tail current (M3): 1 mA  
- Branch current:  
  Ibranch = 0.5 mA  

So:
- ID1 = ID2 = 0.5 mA  
- ID3 = 1 mA  
- ID4 = ID5 = 0.5 mA  



## 3. Gate-Source Voltage (M1, M2)
VGS = Vin − Vs  

VGS = 0 − (−0.7)  

**VGS = 0.7 V**

---

## 4. Overdrive Voltage
Choose:

**VOV = 0.2 V**



## 5. Bias Voltage (VB)
VGS3 = VTH + VOV  

VGS3 = 0.366 + 0.2 = 0.566 V  

VB = VGS3 + VS  

VB = 0.566 − 0.9 = −0.334 V  

**Choose: VB ≈ −0.35 V**



## 6. Width Calculation (NMOS)

ID = (1/2) μn Cox (W/L) VOV²  

W/L = 2ID / (μn Cox VOV²)

### For M1, M2:
- ID = 0.5 mA  
- W/L ≈ 256  
- W ≈ 122.9 µm  

### For M3:
- ID = 1 mA  
- W/L ≈ 513.29  
- W ≈ 246.37 µm  



## 7. Width Calculation (PMOS)
W/L ≈ 108  

W ≈ 51.8 µm  



## 8. Output Common Mode Voltage
VoCM = 0 V  



## 9. Saturation Condition Check

**NMOS (M1, M2):**  
VDS = 0.7 V > 0.2 → Saturation  

**M3:**  
VDS3 = 0.2 V ≥ 0.2 → Edge saturation  

**PMOS (M4, M5):**  
VSD = 0.9 V > 0.2 → Saturation  



## Final Results
- Total current = 1 mA  
- Branch current = 0.5 mA  
- VOV = 0.2 V  
- VB = −0.35 V  
- NMOS width ≈ 122.9 µm  
- PMOS width ≈ 51.8 µm  
- All transistors operate in saturation  

---
# DC Analysis (Operating Point) :

## Before Tuning

### Transistor Dimensions

- Wn ≈ 122.9 µm (M1, M2)  
- Wn ≈ 246.37 µm (M3)  
- Wp ≈ 51.8 µm (M4, M5)  

### Simulation Result

<img width="1693" height="883" alt="Screenshot 2026-03-28 215656" src="https://github.com/user-attachments/assets/c212f904-1706-4e47-9c84-a8d34300b9a4" />


## After Tuning

### Simulation Result

<img width="1700" height="891" alt="Screenshot 2026-03-28 220901" src="https://github.com/user-attachments/assets/3d23b712-529f-4113-a65e-084effc5ede4" />

---
# Input & Output Common Mode Range Analysis

## Given

- VDD = 0.9 V  
- VSS = −0.9 V  
- VTHn = 0.366 V  
- |VTHp| = 0.39 V  
- VOVn = 0.2 V  
- VOVp = 0.2 V  
- Tail node voltage Vp ≈ −0.7 V  



# 1. Input Common Mode Range (VinCM)

## Condition for Proper Operation

All transistors must remain in saturation:

- M1, M2 → NMOS input pair  
- M3 → Tail current source  
- M4, M5 → PMOS load  



## (A) VinCM(min)

Lower limit is determined by M1, M2 staying ON:

VGS ≥ VTH  

VGS = VinCM − Vp  

So,

VinCM − Vp ≥ VTH  

VinCM ≥ VTH + Vp  

Substitute:

VinCM ≥ 0.366 + (−0.7)  

**VinCM(min) ≥ −0.334 V**



## (B) VinCM(max)

Upper limit is determined by M1 remaining in saturation:

VDS ≥ VOV  

For M1:

VDS = Vout − Vp  

Also:

VGS = VinCM − Vp  

Saturation condition:

VDS ≥ VGS − VTH  

Vout − Vp ≥ VinCM − Vp − VTH  

Cancel Vp:

Vout ≥ VinCM − VTH  

So:

VinCM ≤ Vout + VTH  



### PMOS Constraint (M4 Saturation)

VSD ≥ VOV  

VDD − Vout ≥ VOV  

Vout ≤ VDD − VOV  

Vout ≤ 0.9 − 0.2  

Vout ≤ 0.7 V  



### Substitute into VinCM(max)

VinCM ≤ 0.7 + 0.366  

**VinCM(max) ≤ 1.066 V**



## Final Input Common Mode Range

- VinCM(min) ≈ −0.334 V  
- VinCM(max) ≈ 1.066 V  



# 2. Output Common Mode Range (VoCM)

## (A) VoCM(max)

Limited by PMOS saturation (M4, M5):

VSD ≥ VOV  

VDD − VoCM ≥ VOV  

VoCM ≤ VDD − VOV  

VoCM ≤ 0.9 − 0.2  

**VoCM(max) ≤ 0.7 V**



## (B) VoCM(min)

Limited by NMOS saturation (M1, M2):

VDS ≥ VOV  

VoCM − Vp ≥ VOV  

VoCM ≥ VOV + Vp  

VoCM ≥ 0.2 + (−0.7)  

**VoCM(min) ≥ −0.5 V**



## Final Output Common Mode Range

- VoCM(min) ≈ −0.5 V  
- VoCM(max) ≈ 0.7 V  



# Summary

## Input Common Mode Range
- VinCM(min) = −0.334 V  
- VinCM(max) = 1.066 V  

## Output Common Mode Range
- VoCM(min) = −0.5 V  
- VoCM(max) = 0.7 V  



# Key Observations

- Lower VinCM is limited by NMOS input transistors turning OFF  
- Upper VinCM is limited by PMOS load saturation  
- VoCM range ensures both NMOS and PMOS remain in saturation  
- Proper operation requires all MOSFETs to operate in saturation region  

---
# Differential Input Voltage Range (Linear Region)

The differential amplifier operates in the linear region as long as both input transistors (M1 and M2):

- Remain ON  
- Operate in saturation  
- Share the tail current  



## Differential Input Definition

vid = vin1 − vin2  

For symmetric inputs:

- vin1 = VinCM + vid/2  
- vin2 = VinCM − vid/2  



## Condition for Linear Operation

For proper linear amplification:

- Both M1 and M2 must conduct current  
- Neither transistor should turn OFF  

Boundary condition occurs when one transistor (M2) is about to turn OFF:

VGS2 = VTH  



## Derivation

VGS2 = vin2 − Vp  

Substitute:

VinCM − vid/2 − Vp = VTH  

Rearranging:

vid/2 = VinCM − Vp − VTH  

vid = 2 (VinCM − Vp − VTH)  



## Substituting Circuit Values

- VinCM = 0 V  
- Vp = −0.7 V  
- VTH = 0.366 V  

vid = 2 (0 − (−0.7) − 0.366)  

vid = 2 (0.334)  

**vid ≈ 0.668 V**



## Theoretical Maximum Range

−0.668 V ≤ vid ≤ +0.668 V  



## Practical Linear Range (Small-Signal Condition)

For good linearity:

|vid| ≤ 2 × VOV  

Given:

VOV = 0.2 V  

**|vid| ≤ 0.4 V**



## Final Answer

- Theoretical limit:  
  −0.668 V ≤ vid ≤ +0.668 V  

- Practical linear region:  
  −0.4 V ≤ vid ≤ +0.4 V  



## Key Insight

- At |vid| > 0.668 V → one transistor turns OFF → nonlinear region  
- For accurate amplification → operate within ±0.4 V  
- Linear range depends strongly on overdrive voltage (VOV)  

---

# Transient Analysis – Linear vs Non-Linear Behavior

## Theory

The CMOS differential amplifier operates linearly when both input transistors (M1 and M2):

- Remain in saturation  
- Conduct simultaneously  
- Share the tail current  

The boundary between linear and nonlinear operation is given by:

|vid| < √2 VOV  

If:

|vid| > √2 VOV  

→ One transistor turns OFF  
→ Current is steered to one branch  
→ Output becomes nonlinear  



## Simulation Setup

### Case 1: Linear Region (vid < √2 VOV)
V1 Vin1 0 SINE(0 0.05 1k)
V2 Vin2 0 SINE(0 -0.05 1k)

- Differential input:  
  vid = 0.05 V < 0.283 V  

### Case 2: Nonlinear Region (vid > √2 VOV)
V1 Vin1 0 SINE(0 0.7 1k)
V2 Vin2 0 SINE(0 -0.7 1k)


- Differential input: vid = 0.7 V > 0.283 V  

## Observations

### Case 1: Linear Region (vid < √2 VOV)


<img width="1919" height="885" alt="Screenshot 2026-03-28 223320" src="https://github.com/user-attachments/assets/7b5acb37-1d28-463b-b1ae-9e167da885c2" />

Output voltages Vout1 and Vout2 are:
- Clean sinusoidal signals
- Equal in magnitude and opposite in phase
- No clipping or distortion observed
- Output is centered around 0 V
 



### Case 2: Nonlinear Region (vid > √2 VOV)


<img width="1919" height="882" alt="Screenshot 2026-03-28 223754" src="https://github.com/user-attachments/assets/4b8b19e1-d131-4c91-b0b3-dc1622961b76" />

Output waveforms are:

- Strongly distorted
- Flattened at peaks (clipping) 
-  No longer sinusoidal

Output swings close to supply limits
Upper limit ≈ 0.8–0.9 V
Lower limit ≈ -0.5 V  

# Comparison and Interpretation

## Comparison of Linear and Nonlinear Operation

| Parameter | Linear Region (vid < √2 VOV) | Nonlinear Region (vid > √2 VOV) |
|----------|-----------------------------|--------------------------------|
| Input amplitude | Small (±0.05 V) | Large (±0.7 V) |
| Differential input (vid) | 0.1 V | 1.4 V |
| Output waveform | Pure sinusoidal | Distorted / clipped |
| Symmetry | Perfectly symmetric | Distorted and asymmetric |
| Phase relation | 180° out of phase | Still opposite, but distorted |
| Output swing | Within linear limits | Hits supply limits |
| Transistor operation | Both ON | One OFF at a time |
| Current distribution | Shared equally | Fully steered to one branch |
| Gain | Constant | Nonlinear / varying |
| Behavior | Linear amplifier | Switching behavior |



# Interpretation of Results

## Linear Region (vid < √2 VOV)

In this region, the applied differential input is small enough that:

- Both input transistors (M1 and M2) remain in saturation  
- Tail current is continuously shared between both branches  

Output signals (Vout1 and Vout2) are:

- Smooth sinusoidal waves  
- Equal in magnitude and opposite in phase  

This indicates that:

- The relationship between input and output is linear  
- The amplifier operates with constant gain  
- No distortion is introduced  

Hence, the circuit behaves as an ideal differential amplifier.



## Nonlinear Region (vid > √2 VOV)

When the input signal exceeds the limit:

- One transistor enters cutoff during part of the cycle  
- The other transistor carries nearly the entire tail current  
- The circuit no longer shares current symmetrically  

As observed in the waveform:

- Output becomes distorted and clipped  
- Peaks are flattened due to saturation limits  
- Output swings approach supply boundaries  

This indicates that:

- The input-output relationship is no longer linear  
- Gain varies with time  
- The circuit behaves like a current steering switch  



# Key Insight

The boundary:

|vid| = √2 VOV  

defines the transition from linear to nonlinear operation.

- Below this limit → Linear amplification  
- Above this limit → Nonlinear distortion  



# Final Conclusion

The transient analysis clearly demonstrates that:

- Proper linear amplification occurs only for small differential inputs  
- Large input signals force the circuit into nonlinear operation  

Maintaining:

- Small signal input  
- Proper DC biasing  
- Saturation of all transistors  

is essential for accurate amplifier performance  

Thus, the CMOS differential amplifier transitions from a **linear amplifier** to a **nonlinear switching circuit** as vid increases beyond √2 VOV.

---

# Transient Gain Calculation

## Input Signal

Vin1 = SINE(0 50m 1k)  
Vin2 = SINE(0 -50m 1k)  


<img width="1918" height="892" alt="Screenshot 2026-03-28 225413" src="https://github.com/user-attachments/assets/bba42fd5-d8d6-4528-8cdf-7d4c4e823c26" />




## Measured Values

- Vin (peak-to-peak) = 100 mV  
- Vout (peak-to-peak) = 191.58 mV  



## Practical Gain

Av = Vout / Vin  

Av = 191.58 mV / 100 mV  

**Av = 1.9158 V/V**



## Gain in dB

Av(dB) = 20 log10(1.9158)  

**Av(dB) ≈ 5.647 dB**



# Small-Signal Gain Calculation (Differential Amplifier)

## Given Data

### Supply Voltages
- VDD = 0.9 V  
- VSS = −0.9 V  

### Drain Current
- ID1 = ID2 = 0.5 mA  

### Overdrive Voltage
- VOV = 0.2 V  



## 1. Transconductance (gm)

For a MOSFET:

gm = 2ID / VOV  

Substituting values:

gm = (2 × 0.5 × 10⁻³) / 0.2  

gm = (1 × 10⁻³) / 0.2  

**gm = 5 × 10⁻³ S = 5 mS**



## 2. Small-Signal Gain Expression

Av = gm × (ro2 || ro4)  

where:

- ro2 = output resistance of NMOS (M2)  
- ro4 = output resistance of PMOS (M4)  



## 3. Equivalent Output Resistance

From transient simulation:

- Vin (peak-to-peak) = 100 mV  
- Vout (peak-to-peak) = 191.58 mV  

Gain:

Av = Vout / Vin  

Av = 1.9158 V/V  

Now:

ro_eq = Av / gm  

ro_eq = 1.9158 / (5 × 10⁻³)  

**ro_eq ≈ 383 Ω**

So:

(ro2 || ro4) ≈ 383 Ω  



## 4. Individual Output Resistance

Assuming:

ro2 ≈ ro4  

Then:

ro = 2 × ro_eq  

ro ≈ 2 × 383  

**ro ≈ 766 Ω**



## 5. Final Gain Verification

Av = gm × ro_eq  

Av = (5 × 10⁻³) × 383  

**Av ≈ 1.915 ≈ 1.92 V/V**



## 6. Gain in dB

Av(dB) = 20 log10(Av)  

Av(dB) = 20 log10(1.9158)  

**Av(dB) ≈ 5.65 dB**



## 7. Final Results

- gm = 5 mS  
- ro ≈ 766 Ω  
- (ro2 || ro4) ≈ 383 Ω  
- Gain Av ≈ 1.92 V/V  
- Gain ≈ 5.65 dB  

<img width="1919" height="915" alt="Screenshot 2026-03-28 232329" src="https://github.com/user-attachments/assets/4b6ff6d1-32b2-4707-be92-468e9dc325b2" />




## 8. Observations

The practical gain is higher due to:

- Finite output resistance (ro)  
- Channel length modulation  

Low gain is due to:

- Small ro (short channel length)  
- High drain current  



## 9. Conclusion

The small-signal gain calculated using gm and ro matches closely with the simulated gain.

Hence, the differential amplifier operates correctly in the small-signal region with a gain of approximately:

**Av ≈ 1.92 V/V**

This validates both theoretical analysis and simulation results.

---

# AC Analysis

AC analysis determines frequency response.



## Circuit Setup

- Set AC amplitude = 1  



## Midband Gain

- Midband Gain = 5.683 dB  
- Frequency = 31.622 kHz  


<img width="1919" height="915" alt="Screenshot 2026-03-28 232329" src="https://github.com/user-attachments/assets/9bb92f33-e239-4761-847d-2225eea34c8c" />


## -3 dB Cutoff Frequency


<img width="1916" height="920" alt="Screenshot 2026-03-28 233016" src="https://github.com/user-attachments/assets/1c20fc0b-15f8-4fca-a244-8fedd088ebde" />


- Upper Cutoff Frequency:  
  fH = 3.0644 GHz  

- Lower Cutoff Frequency:  
  fL = 0 Hz  



## Bandwidth

BW = fH − fL  

BW = 3.0644 GHz  



## Midband Gain (Verification)

From AC plot:

Gain (dB) = 5.6837 dB  

Convert to linear:

Av = 10^(5.6837 / 20)  

**Av ≈ 1.92 V/V**



## Unity Gain Bandwidth (UGB)

UGB is the frequency where gain = 0 dB.

<img width="1919" height="884" alt="Screenshot 2026-03-29 000658" src="https://github.com/user-attachments/assets/94a1f54a-691d-4fa2-b335-23642422db61" />


Since the curve crosses 0 dB slightly after BW:

UGB ≈ Av × BW  

UGB ≈ 1.92 × 3.064 GHz  

**UGB ≈ 5.88 GHz**



## Gain Bandwidth Product (GBP)

For a single-pole system:

GBP = UGB  

**GBP ≈ 5.88 GHz**



## Final Results

| Parameter | Value |
|----------|------|
| Gain (Av) | 1.92 V/V |
| Gain (dB) | 5.68 dB |
| Bandwidth (BW) | 3.064 GHz |
| UGB | 5.88 GHz |
| GBP | 5.88 GHz |



## Observations

- Gain is relatively low (~2 V/V)  
- Bandwidth is very high (~GHz range)  
- Indicates a low-gain, high-speed amplifier  



## Interpretation

- Circuit behaves as a wideband amplifier  
- Low gain due to small output resistance (ro)  

High bandwidth is due to:

- Low parasitic capacitance  
- Strong bias current  



## Conclusion

The AC analysis confirms:

- The amplifier has low gain but very high bandwidth  
- Gain-Bandwidth Product is approximately constant (~5.88 GHz)  
- Suitable for high-speed analog applications  

---

# Overall Results, Inference and Interpretation



# 1. Overall Results

## DC Performance

- Total current = 1 mA  
- Branch current = 0.5 mA  
- Overdrive voltage (VOV) = 0.2 V  
- Bias voltage VB ≈ −0.35 V  
- All MOSFETs operate in saturation region  



## Transistor Dimensions

- NMOS (M1, M2): W ≈ 122.9 µm  
- NMOS (M3): W ≈ 246.37 µm  
- PMOS (M4, M5): W ≈ 51.8 µm  



## Common Mode Ranges

### Input Common Mode Range
- VinCM(min) ≈ −0.334 V  
- VinCM(max) ≈ 1.066 V  

### Output Common Mode Range
- VoCM(min) ≈ −0.5 V  
- VoCM(max) ≈ 0.7 V  



## Differential Input Range

- Theoretical: ±0.668 V  
- Practical linear range: ±0.4 V  



## Transient Analysis

- Linear operation for small signals (vid < √2 VOV)  
- Nonlinear distortion for large signals (vid > √2 VOV)  



## Gain Performance

- Practical gain Av ≈ 1.92 V/V  
- Gain ≈ 5.65 dB  
- Transconductance gm = 5 mS  
- Output resistance ro ≈ 766 Ω  



## AC Performance

- Gain ≈ 1.92 V/V (5.68 dB)  
- Bandwidth ≈ 3.064 GHz  
- Unity Gain Bandwidth ≈ 5.88 GHz  
- Gain Bandwidth Product ≈ 5.88 GHz  



# 2. Inference

- The amplifier successfully operates under **low-voltage (±0.9 V)** conditions.  
- All transistors are biased correctly in saturation, ensuring proper analog operation.  
- The circuit demonstrates **stable DC operating point** and reliable biasing.  
- The gain is relatively low due to:
  - Small output resistance (ro)  
  - Short channel length effects  
- High bandwidth is achieved due to:
  - Low parasitic capacitances  
  - Strong bias current  
- The circuit exhibits a **trade-off between gain and bandwidth**:
  - Low gain → High speed  
  - High bandwidth → Wide frequency operation  



# 3. Interpretation

## Linear vs Nonlinear Behavior

- For small input signals:
  - Both transistors conduct  
  - Current is shared  
  - Output is linear and sinusoidal  

- For large input signals:
  - One transistor turns OFF  
  - Current is steered  
  - Output becomes nonlinear  



## Circuit Behavior

- Acts as a **linear differential amplifier** for small signals  
- Acts as a **current-steering switch** for large signals  



## Performance Nature

- The circuit behaves as a **low-gain, high-speed amplifier**  
- Suitable for:
  - High-frequency analog circuits  
  - Wideband applications  
  - Front-end signal processing  



## Design Insight

- Gain can be improved by increasing output resistance (ro)  
- Bandwidth can be controlled by adjusting bias current and capacitances  
- Proper biasing is critical to maintain saturation and linearity  



# Final Conclusion

The designed CMOS differential amplifier demonstrates:

- Correct DC biasing and saturation operation  
- Accurate small-signal gain matching theoretical and simulation results  
- High bandwidth (~GHz range) with low gain (~2 V/V)  
- Clear transition between linear and nonlinear regions  

Thus, the circuit is best suited for **high-speed, wideband analog applications**, where bandwidth is prioritized over gain.

---

# Circuit 3 
**CIRCUIT DIAGRAM :**
<img width="1265" height="834" alt="image" src="https://github.com/user-attachments/assets/cd5e3b3c-1507-423c-8aab-6aad42ba263f" />

# Circuit Design Calculations:

## 1. Given

VDD = 0.9 V  
VSS = −0.9 V  
VinCM = 0 V  
L = 480 nm  
Vp = −0.7 V 
ID (tail current) = 1 mA  



## 2. Current Distribution

For differential pair:

I1 = I2 = ID / 2  

I1 = I2 = 0.5 mA  



## 3. From Simulation

 
Vout = −0.0324 V  



## 4. Gate-Source Voltage

### NMOS (M1, M2)

VGS = Vin − Vp  

VGS = 0 − (−0.7)  

VGS = 0.7 V  



## 5. Overdrive Voltage

Vov = VGS − VTHn  

Vov = 0.7 − 0.366  

Vov = 0.334 V  



## 6. Saturation Check

### NMOS (M1, M2)

VDS = Vout − Vp  

VDS = −0.0324 − (−0.7)  

VDS = 0.6676 V  

Check:

VDS ≥ Vov  

0.6676 ≥ 0.334 



### Tail NMOS (M3)

VDS3 = Vp − VSS  

VDS3 = −0.7 − (−0.9)  

VDS3 = 0.2 V  

VGS3 = Vb1 − VSS  

VGS3 = −0.34 − (−0.9) = 0.56 V  

Vov3 = 0.56 − 0.366 = 0.194 V  

Check:

0.2 ≥ 0.194  



### PMOS (M4, M5)

VSD = VDD − Vout  

VSD = 0.9 − (−0.0324)  

VSD = 0.9324 V  

VSG = VDD − Vb2  

VSG = 0.9 − (−0.36) = 1.26 V  

Vovp = 1.26 − 0.39 = 0.87 V  

Check:

0.9324 ≥ 0.87  



## 7. Width Calculation

Drain current equation:

ID = (1/2) μ Cox (W/L) Vov²  



### NMOS (M1, M2)

ID = 0.5 mA  

(W/L)n = (2 × 0.5×10⁻³) / (μn × Cox × Vov²)

(W/L)n ≈ 92  

Wn = 92 × 480 nm  

Wn ≈ 44 µm  



### Tail NMOS (M3)

ID = 1 mA  

(W/L)3 ≈ 184  

W3 ≈ 88 µm  



### PMOS (M4, M5)

(W/L)p ≈ 39  

Wp ≈ 18.7 µm  

      

## 8. Final Summary

| Transistor | Current | Width |
|-----------|--------|------|
| M1, M2 | 0.5 mA | 44 µm |
| M3 | 1 mA | 88 µm |
| M4, M5 | 0.5 mA | 18.7 µm |



### DC ANALYSIS ( OPERATING POINT ) :
<img width="1763" height="896" alt="Screenshot 2026-03-29 025029" src="https://github.com/user-attachments/assets/00662cef-6931-4810-97c5-24ddbb49ef9e" />

# Common Mode Analysis — CMOS Differential Amplifier

## Given

VDD = 0.9 V  
VSS = −0.9 V  

VTHn = 0.366 V  
|VTHp| = 0.39 V  

Vp ≈ −0.7 V  
Vov ≈ 0.334 V  



# 1. Input Common Mode Range (VinCM)


## VinCM (min)

Condition:

NMOS (M1, M2) must remain ON:

VGS ≥ VTHn  

VGS = VinCM − Vp  

So:

VinCM − Vp ≥ VTHn  

VinCM ≥ VTHn + Vp  

Substitute:

VinCM ≥ 0.366 + (−0.7)  

VinCM ≥ −0.334 V  



## VinCM (max)

Condition:

Tail transistor (M3) must remain in saturation:

VDS3 ≥ Vov  

Also:

Vp = VinCM − VGS  

But:

VGS = VTH + Vov  

So:

Vp = VinCM − (VTHn + Vov)  

Now apply saturation:

Vp − VSS ≥ Vov  

Substitute:

VinCM − (VTHn + Vov) − VSS ≥ Vov  

VinCM ≥ VTHn + 2Vov + VSS  

But for max limit, we consider upper headroom:

VinCM ≤ VDD − |VTHp| − Vov  

Substitute:

VinCM ≤ 0.9 − 0.39 − 0.334  

VinCM ≤ 0.176 V  



## Final VinCM Range

| Parameter | Value |
|----------|------|
| VinCM(min) | −0.334 V |
| VinCM(max) | 0.176 V |



# 2. Output Common Mode Range (VoCM)



## VoCM (min)

Condition:

NMOS must remain in saturation:

VDS ≥ Vov  

Vout − Vp ≥ Vov  

Vout ≥ Vp + Vov  

Substitute:

Vout ≥ −0.7 + 0.334  

Vout ≥ −0.366 V  



## VoCM (max)

Condition:

PMOS must remain in saturation:

VSD ≥ Vov  

VDD − Vout ≥ Vov  

Vout ≤ VDD − Vov  

Substitute:

Vout ≤ 0.9 − 0.334  

Vout ≤ 0.566 V  



## Final VoCM Range

| Parameter | Value |
|----------|------|
| VoCM(min) | −0.366 V |
| VoCM(max) | 0.566 V |



# 3. Final Answer

## Input Common Mode Range

VinCM(min) = −0.334 V  
VinCM(max) = 0.176 V  



## Output Common Mode Range

VoCM(min) = −0.366 V  
VoCM(max) = 0.566 V  



# 4. Conclusion

- Input range is limited by NMOS turn-on and PMOS saturation  
- Output range is limited by NMOS and PMOS saturation conditions  
- Circuit operates linearly only within these ranges
- 
# Differential Input Range (vid) for Linear Operation

## Definition

vid = Vin1 − Vin2  

For linear operation:

- Both transistors M1 and M2 must remain ON  
- Tail current must be shared (no current steering to one side)  



## Condition for Linear Region

For a differential pair:

|vid| << 2 × Vov  



## Step 1: Calculate Overdrive Voltage

From previous:

VGS = 0.7 V  
VTHn = 0.366 V  

Vov = VGS − VTH  

Vov = 0.7 − 0.366  

Vov = 0.334 V  



## Step 2: Compute vid Range

vid(max) = 2 × Vov  

vid(max) = 2 × 0.334  

vid(max) ≈ 0.668 V  



## Final Range

|vid| ≤ 0.668 V  

So:

-0.668 V ≤ vid ≤ 0.668 V  



## Interpretation

- For |vid| < 0.668 V → Linear amplification region  
- For |vid| > 0.668 V → One transistor turns OFF  
  → circuit enters nonlinear / switching region  



## Conclusion

The differential amplifier behaves as a linear amplifier only when the input differential voltage is within ±0.668 V.

# Transient Analysis — Linear vs Nonlinear Behavior

The linear range of a differential amplifier is given by:

|vid| ≤ √2 × Vov  

Where:

Vov = VGS − VTH  

From design:

Vov = 0.334 V  

So:

vid(max) = √2 × 0.334 ≈ 0.472 V  



# Case 1: vid < √2 Vov  (Linear Region)

## Input Applied

Vin1 = SINE(0, 5 mV, 1 kHz)  
Vin2 = SINE(0, −5 mV, 1 kHz)  

vid = 10 mV <  0.472V  

<img width="1919" height="894" alt="image" src="https://github.com/user-attachments/assets/6ab34493-bf10-484b-84e8-1892e232f4bf" />


## Observation

- Output signals (Vout1, Vout2) are:
  - Sinusoidal  
  - Symmetrical  
  - Undistorted  

- Both NMOS transistors (M1, M2):
  - Remain ON  
  - Share current equally  



## Result

- Circuit behaves as a **linear amplifier**  
-  Output is proportional to input  



# Case 2: vid > √2 Vov  (Nonlinear Region)

## Input Applied

Vin1 = SINE(0, 300 mV, 1 kHz)  
Vin2 = SINE(0, −300 mV, 1 kHz)  

vid = 600 mV > 472 mV  

<img width="1919" height="893" alt="image" src="https://github.com/user-attachments/assets/e4469419-9b44-4c39-a879-e846a0bccd8c" />




## Observation

- Output waveform:
  - Distorted  
  - Clipped / flattened   

- One transistor:
  - Turns OFF  

- Other transistor:
  - Carries almost full tail current  



## Result

- Circuit behaves as a **nonlinear amplifier**  
-Current steering occurs  


# Comparison and Interpretation — Linear vs Nonlinear Operation

## Basis of Comparison

The behavior of the CMOS differential amplifier is analyzed for two cases:

1. |vid| < √2Vov  → Linear Region  
2. |vid| > √2Vov  → Nonlinear Region  

Where:

√2Vov ≈ 0.472 V  



## Comparison Table

| Parameter | Linear Region | Nonlinear Region |
|----------|--------------|------------------|
| Input Condition | |vid| < √2Vov | |vid| > √2Vov |
| Output Waveform | Sinusoidal | Distorted sinusoidal |
| Gain | Constant | Varies (compressed) |
| Linearity | High | Reduced |
| Current Distribution | Shared equally | One-sided (current steering) |
| Transistor Operation | Both ON | One ON, one OFF |
| Signal Behavior | Amplification | Switching tendency |



## Interpretation

- In the **linear region**, both transistors (M1 and M2) operate in saturation and share the tail current equally. This results in a proportional and undistorted output signal, confirming proper amplifier behavior.

- In the **nonlinear region**, as the differential input voltage exceeds √2Vov, one transistor gradually turns OFF while the other carries most of the current. This causes current steering, leading to distortion and reduction in gain.

- The transition from linear to nonlinear operation is **gradual**, not abrupt. Hence, even in the nonlinear region, the output may still appear sinusoidal but shows amplitude compression and reduced symmetry.



## Conclusion

The transient analysis clearly demonstrates that the CMOS differential amplifier behaves as a linear amplifier only within the input range |vid| ≤ √2Vov. Beyond this range, the circuit enters nonlinear operation due to current steering, resulting in distortion and deviation from ideal amplification.

# Small Signal Analysis — Differential Gain


## 1. Small Signal Model

For differential operation:

- Input: vid = Vin1 − Vin2  
- Each NMOS carries current variation = gm × (vid / 2)  

Output is taken at one side (single-ended):



## 2. Transconductance (gm)

gm = 2ID / Vov  

From design:

ID (per transistor) = 0.5 mA  
Vov = 0.334 V  

gm = (2 × 0.5×10⁻³) / 0.334  

gm ≈ 2.99 mS  



## 3. Output Resistance

Output node consists of:

- NMOS output resistance → ro_n  
- PMOS output resistance → ro_p  

Effective resistance:

Rout = ro_n || ro_p  



## 4. Differential Gain (Single-Ended)

Voltage gain:

Av = gm × (ro_n || ro_p)  



## 5. Approximation (Using Symmetry)

If:

ro_n ≈ ro_p = ro  

Then:

Rout ≈ ro / 2  

So:

Av ≈ gm × (ro / 2)  



## 6. Final Expression

Single-ended gain:

Av = gm × (ro_n || ro_p)  

Differential gain:

Ad = 2 × Av  



## 7. Numerical Insight

Since gm ≈ 2.99 mS:

Av depends on ro  

Typical:

If ro ≈ 50 kΩ  

Av ≈ 2.99×10⁻³ × 25×10³  

Av ≈ 74.75 V/V  

Av (dB) = 20log(74.75)

Av = 37.47dB



## 8. Key Observations

- Gain increases with:
  - Higher gm (higher current or lower Vov)  
  - Higher ro (long channel length)  

- Gain decreases if:
  - Devices leave saturation  
  - Channel length modulation increases  



## 9. Conclusion

The voltage gain of the CMOS differential amplifier is given by:

Av = gm × (ro_n || ro_p)

The gain is directly proportional to transconductance and output resistance, confirming that proper biasing and saturation operation are essential for achieving high gain.

##  AC Analysis
AC analysis determines frequency response.

##  Circuit Setup
   Set AC amplitude: = 1  
 <img width="1919" height="895" alt="image" src="https://github.com/user-attachments/assets/0a8ffc22-1764-407b-93b2-5e7ae3a2666f" />

 
  
  Midband Gain =  32.377dB
  
 -3 dB Cutoff Frequency:
 <img width="1915" height="865" alt="image" src="https://github.com/user-attachments/assets/b59e8f64-6bf4-4437-a00c-108031749f10" />


 
Upper Cutoff Frequency fH  = 446.21 MHz 

Lower Cutoff Frequency fL = 0 Hz

**Bandwidth :**

BW = fH − fL

BW = 446.21 MHz 



##  Unity Gain Bandwidth (UGB)

UGB is the frequency where gain = 1 (0 dB)

For single dominant pole system:

UGB ≈ Av × BW  

UGB = 41.6 × 446.21 MHz  

UGB ≈ 18.56 GHz  



##  Gain Bandwidth Product (GBP)

GBP = Gain × Bandwidth  

GBP = 41.6 × 446.21 MHz  

GBP ≈ 18.56 GHz  



##  Final Results

| Parameter | Value |
|----------|------|
| Gain (dB) | 32.377 dB |
| Gain (linear) | 41.6 V/V |
| Bandwidth (BW) | 446.21 MHz |
| Unity Gain Bandwidth (UGB) | 18.56 GHz |
| Gain Bandwidth Product (GBP) | 18.56 GHz |



##  Observations

- High bandwidth indicates fast response  
- Gain is moderate and stable in midband  
- GBP is large → suitable for high-frequency applications  



##  Conclusion

The AC analysis shows that the CMOS differential amplifier provides a midband gain of 32.377 dB with a bandwidth of 446.21 MHz. The high unity gain bandwidth and gain-bandwidth product indicate good high-frequency performance.


# Results, Inference and Interpretation




# 1. Final Results

## DC Analysis

- Tail current (ID) ≈ 1 mA  
- Branch currents (M1, M2) ≈ 0.5 mA each  
- Output voltage (Vout) ≈ −0.0324 V  
- All MOSFETs operate in **saturation region** ✔  



## Common Mode Range

### Input Common Mode Voltage

VinCM(min) = −0.334 V  
VinCM(max) = 0.176 V  



### Output Common Mode Voltage

VoCM(min) = −0.366 V  
VoCM(max) = 0.566 V  



## Differential Input Range

Linear region condition:

|vid| ≤ √2Vov  

|vid| ≤ 0.472 V  



## Small Signal Gain

- gm ≈ 2.99 mS  
- Gain ≈ 32.377 dB (simulation)  
- Gain ≈ 41.6 V/V  



## AC Analysis

- Bandwidth (BW) = 446.21 MHz  
- Unity Gain Bandwidth (UGB) ≈ 18.56 GHz  
- Gain Bandwidth Product (GBP) ≈ 18.56 GHz  



## Transient Analysis

### Linear Region (vid < √2Vov)

- Output is sinusoidal  
- No distortion observed  
- Current equally shared  



### Nonlinear Region (vid > √2Vov)

- Output shows distortion (compression)  
- Current steering occurs  
- One transistor dominates conduction  



# 2. Inference

- The circuit is properly biased, ensuring all MOSFETs operate in saturation.  
- The differential pair provides symmetrical current distribution, confirming correct design.  
- The amplifier shows **linear behavior for small differential inputs** and transitions smoothly to nonlinear behavior for large inputs.  
- High bandwidth and large GBP indicate that the circuit is suitable for high-frequency applications.  
- The gain obtained from AC analysis matches closely with theoretical expectations, validating the design.  



# 3. Interpretation

- The operation of the differential amplifier depends strongly on **overdrive voltage (Vov)** and **biasing conditions**.  
- The **common mode range** is limited by:
  - NMOS turn-on condition  
  - PMOS saturation requirement  

- The **linear region** exists only when both transistors conduct simultaneously, ensuring proportional amplification.  

- When the input exceeds the linear range:
  - Current steering occurs  
  - One transistor turns OFF  
  - The circuit behaves like a switching device  

- The AC response confirms that:
  - Gain is constant in midband  
  - Bandwidth is wide  
  - UGB ≈ GBP (single-pole behavior)  



# 4. Final Conclusion

The CMOS differential amplifier is successfully designed and analyzed. The circuit satisfies all operating conditions, exhibits proper linear amplification within the defined input range, and demonstrates high-frequency performance with significant gain-bandwidth product. The results confirm the theoretical behavior of differential amplifiers in both linear and nonlinear regions.

 ---


# Detailed Comparison and Interpretation of Circuit 1, Circuit 2, and Circuit 3

---

# 1. Overview of Circuits

- **Circuit 1**: Differential amplifier with resistive load  
- **Circuit 2**: Differential amplifier with improved biasing / partial active behavior  
- **Circuit 3**: Differential amplifier with active load (PMOS current mirror)  

Each circuit represents a progression in performance, efficiency, and complexity.

---

# 2. Gain Analysis

## Circuit 1

Gain expression:

Av = gm × RD  

- Limited by physical resistor value  
- Practical gain ≈ 5.38 V/V (≈14.6 dB)  

 Limitation:
- Increasing gain requires large RD → increases voltage drop and area  

---

## Circuit 2

- Improved biasing stabilizes gm  
- Slight improvement in gain  

 Insight:
- Gain still limited by resistive load  

---

## Circuit 3

Gain expression:

Av = gm × (ro_n || ro_p)  

- Active load provides **very high output resistance**  
- Gain ≈ 41.6 V/V (≈32.37 dB)  

Key Reason:
- ro ≫ RD → much larger gain  

---

## Final Insight (Gain)

Circuit 3 achieves significantly higher gain because:

- It replaces RD with high resistance current source  
- Improves voltage-to-current conversion efficiency  

---

# 3. Power Consumption Analysis

## Circuit 1

- Power dissipated in resistors:
  
  P = I²R  

- Significant static loss  

---

## Circuit 2

- Slight improvement due to bias optimization  

---

## Circuit 3

- Uses current mirror → no resistive loss  
- Same tail current reused efficiently  

 Insight:

Circuit 3 achieves **higher performance at same power**

---

# 4. Area Analysis

## Circuit 1

- Requires large resistors (kΩ range)  
- Occupies large silicon area  

---

## Circuit 2

- Reduced resistor dependency  

---

## Circuit 3

- No resistors  
- Only MOS devices  

 Insight:

Circuit 3 is **most area-efficient**, ideal for IC design  

---

# 5. Input Common Mode Range (ICMR)

## Circuit 1

- Wider range  
- Fewer stacked devices  

---

## Circuit 2

- Moderate range  

---

## Circuit 3

- Limited due to stacking:
  - NMOS pair + PMOS load + tail source  

Insight:

Higher performance comes at the cost of **reduced input range**

---

# 6. Output Swing

## Circuit 1

- Limited by voltage drop across RD  

---

## Circuit 2

- Slightly improved  

---

## Circuit 3

- Better swing due to active load  
- But constrained by saturation conditions  

 Insight:

Circuit 3 achieves **better usable swing**, but requires precise biasing  

---

# 7. Bandwidth and Frequency Response

## Circuit 1

- Low bandwidth (~9.6 MHz)  
- Large RC time constant  

---

## Circuit 2

- Moderate improvement  

---

## Circuit 3

- Very high bandwidth (~446 MHz)  
- UGB ≈ 18.56 GHz  

 Key Reason:

- Smaller parasitics  
- Higher transconductance  
- Lower effective capacitance  

---

# 8. Linearity and Signal Behavior

## Circuit 1

- Good linearity  
- Limited gain  

---

## Circuit 2

- Improved stability  

---

## Circuit 3

- Best linearity for small signals  
- Shows clear transition to nonlinear region  

 Insight:

Circuit 3 clearly demonstrates **current steering behavior**

---

# 9. Trade-Off Summary

| Parameter | Circuit 1 | Circuit 2 | Circuit 3 |
|----------|----------|----------|----------|
| Gain | Low | Medium | High |
| Power Efficiency | Low | Medium | High |
| Area | Large | Medium | Small |
| Bandwidth | Low | Medium | Very High |
| ICMR | Wide | Moderate | Limited |
| Complexity | Low | Medium | High |

---

# 10. Overall Interpretation

The three circuits demonstrate the **evolution of differential amplifier design**:

### Stage 1 — Basic Design (Circuit 1)
- Simple but inefficient  
- Limited gain and speed  

---

### Stage 2 — Improved Biasing (Circuit 2)
- Better control  
- Moderate performance  

---

### Stage 3 — Advanced Design (Circuit 3)

- Uses active load  
- Achieves:
  - High gain  
  - High bandwidth  
  - Low area  
  - Better efficiency  

---

# 11. Final Conclusion

Circuit 3 is the most advanced and optimized design among the three. It overcomes the limitations of resistive loads by using active loads, resulting in significantly higher gain, bandwidth, and power efficiency.

However, this improvement comes with trade-offs such as reduced input common-mode range and increased design complexity.

---

# 12. Final Insight 



**“In analog design, improving gain and bandwidth always comes at the cost of reduced headroom and input range — Circuit 3 clearly demonstrates this fundamental trade-off.”**



# Final Summary of Results — Circuit 1, Circuit 2, Circuit 3

| Parameter | Circuit 1 (Resistive Load) | Circuit 2 (Improved Bias) | Circuit 3 (Active Load) |
|----------|----------------------------|----------------------------|--------------------------|
| Tail Current (Itail) | 1 mA | 1 mA | 1 mA |
| Branch Current (ID) | 0.5 mA | 0.5 mA | 0.5 mA |
| Gain (V/V) | ~5.38 | Moderate | ~41.6 |
| Gain (dB) | ~14.6 dB | ~15–20 dB | ~32.37 dB |
| Bandwidth (BW) | ~9.6 MHz | Moderate | ~446.21 MHz |
| UGB | ~58.3 MHz | Higher than Ckt1 | ~18.56 GHz |
| GBP | ~59.86 MHz | Higher than Ckt1 | ~18.56 GHz |
| Power Consumption | Moderate | Moderate | Low (efficient) |
| Area | Large (Resistors) | Medium | Small (MOS only) |
| Output Swing | Limited | Improved | Best |
| Input CM Range | Wide | Moderate | Limited |
| Linearity | Good | Better | Best (small signal) |
| Complexity | Low | Medium | High |
| Load Type | Resistive | Semi-active | Active (Current Mirror) |

---

# Final Conclusion 

Circuit 3 provides the best performance in terms of gain, bandwidth, power efficiency, and area, while Circuit 1 is simplest but least efficient, and Circuit 2 offers a balance between the two.









 

 












































































 
