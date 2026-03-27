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

✔ Transistor operates in **saturation region**

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

## 🔧 Circuit Setup

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

✔ All MOSFETs operate in **saturation region**

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

#  2) Circuit Design Calculations:

## Given Specifications

- VDD = 0.9 V  
- VSS = −0.9 V  
- Maximum Power P ≤ 1.8 mW  
- Tail node voltage Vp = −0.7 V  
- Input common mode voltage VinCM = 0 V  
- Channel length L = 480 nm  



## Technology Parameters (TSMC 0.18 µm)

### NMOS

- Threshold voltage VTHn = 0.366 V  
- Electron mobility μn = 0.0115689 m²/V·s  

### PMOS

- Threshold voltage |VTHp| ≈ 0.39 V  
- Hole mobility μp = 0.02738 m²/V·s  



## Oxide Capacitance

Cox = εox / tox  

εox = 3.453 × 10⁻¹¹ F/m  
tox = 4.1 × 10⁻⁹ m  

Cox = 8.42 × 10⁻³ F/m²  



## 1. Total Current Calculation

P = (VDD − VSS) × Itotal  

1.8 mW = 1.8 × Itotal  

Itotal = 1 mA  



## 2. Current Distribution

- Tail current (M3): 1 mA  
- Each branch current:

Ibranch = 0.5 mA  

So,

- ID1 = ID2 = 0.5 mA  
- ID3 = 1 mA  
- ID4 = ID5 = 0.5 mA  



## 3. Gate-Source Voltage (M1, M2)

VGS = Vin − Vs  

VGS = 0 − (−0.7)  

VGS = 0.7 V  



## 4.  Overdrive Voltage

To ensure M3 saturation:

VDS3 ≥ VOV  

VDS3 = 0.2 V  

Choose:

VOV = 0.2 V  



## 5. Bias Voltage (VB / V4)

VGS3 = VTH + VOV  

VGS3 = 0.366 + 0.2  

VGS3 = 0.566 V  

VB = VGS3 + VS  

VB = 0.566 + (−0.9)  

VB = −0.334 V  



## 6. Width Calculation (NMOS)

ID = (1/2) μn Cox (W/L) VOV²  

W/L = 2ID / (μn Cox VOV²)  

Substitute:

ID = 0.5 mA  
VOV = 0.2  

W/L ≈ 256  

L = 480 nm  

W ≈ 256 × 480 nm  

Wn ≈ 122.9 µm  



## 7. Width Calculation (PMOS)

ID = (1/2) μp Cox (W/L) VOV²  

W/L ≈ 108  

W ≈ 108 × 480 nm  

Wp ≈ 51.8 µm  



## 8. Output Common Mode Voltage

VoCM = 0 V  



## 9. Saturation Condition Check

### NMOS (M1, M2)

VDS = 0 − (−0.7) = 0.7 V  

0.7 > 0.2 → Saturation  



### Tail NMOS (M3)

VDS3 = −0.7 − (−0.9) = 0.2 V  

0.2 ≥ 0.2 → Saturation (edge condition)  



### PMOS (M4, M5)

VSD = 0.9 − 0 = 0.9 V  

0.9 > 0.2 → Saturation  



## Final Results

- Total current = 1 mA  
- Branch current = 0.5 mA  
- VOV = 0.2 V  
- VB = −0.334 V  
- NMOS width ≈ 122.9 µm  
- PMOS width ≈ 51.8 µm  
- All transistors operate in saturation

### DC ANALYSIS ( OPERATING POINT ) :

***BEFORE TUNNING*** :

Wn ≈ 122.9 µm  

Wp ≈ 51.8 µm 

<img width="1919" height="895" alt="image" src="https://github.com/user-attachments/assets/5013eb4a-3c69-48b4-9f96-d4534c17dd9d" />




 

 












































































 
