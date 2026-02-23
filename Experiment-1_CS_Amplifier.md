<h1 style="font-size:30px;">Experiment–1</h1>

<h1 style="font-size:25px;">PMOS Common Source Amplifier Analysis</h1>

This experiment demonstrates the **DC, AC, Transient, and DC Sweep analysis** of a PMOS Common Source (CS) amplifier using LTspice.

---

<h1 style="font-size:25px;">Abstract</h1>

In this experiment, a PMOS Common Source amplifier is analyzed using DC, AC, and transient simulations.  
DC analysis determines the operating point and verifies saturation condition.  
Transient analysis observes time-domain amplification and phase inversion.  
AC analysis evaluates frequency response, midband gain, and bandwidth.

---

<h1 style="font-size:25px;">Theory</h1>

# PMOS Common Source (CS) Amplifier – Theory

## Introduction

A **PMOS Common Source amplifier** is a MOSFET amplifier configuration in which:

- Input is applied to the **Gate**
- Output is taken from the **Drain**
- Source is connected to **VDD** (common terminal)

It provides voltage amplification by varying the drain current ($I_D$) in response to changes in gate-to-source voltage ($V_{SG}$).

The output is **180° out of phase** with the input signal.

---

## Characteristics

- High input impedance
- Moderate to high output impedance
- Voltage amplification with phase inversion

---

## Conditions for Proper Operation (PMOS)

For correct amplification, the PMOS must operate in **Saturation Region**.

### 1. Turn-On Condition

$$
V_{SG} \ge |V_{th}|
$$

### 2. Saturation Condition

$$
V_{SD} \ge V_{SG} - |V_{th}|
$$

### 3. Small Signal Condition

Input signal must be small to ensure linear amplification.

### 4. Proper Biasing

- Correct selection of $R_D$
- Midpoint biasing for maximum symmetrical swing

---

## Drain Current in Saturation Region (PMOS)

$$
I_D = \frac{1}{2} k_p (V_{ov})^2
$$

Where,

$$
V_{ov} = V_{SG} - |V_{th}|
$$

$k_p$ = Process transconductance parameter for PMOS

---

## Small Signal Parameters

### Transconductance

$$
g_m = \frac{2 I_D}{V_{ov}}
$$

### Voltage Gain

$$
A_v = - g_m R_D
$$

Negative sign indicates **phase inversion**.

---

<h1 style="font-size:25px;">Experiment Specifications</h1>

## Given Design Requirements

| Parameter | Symbol | Value | Unit |
|------------|--------|--------|------|
| Supply Voltage | VDD | 1.8 | V |
| Maximum Power | Pmax | ≤ 1 | mW |
| Load Capacitance | CL | 10 | pF |
| Channel Length | L | 180 | nm |
| Technology Node | — | 180 | nm |
| Simulation Tool | — | LTspice | — |

---

## Power Constraint

$$
P = V_{DD} \times I_D
$$

Given:

$$
P_{max} = 1mW
$$

$$
I_D \le \frac{P_{max}}{V_{DD}}
$$

$$
I_D \le \frac{1}{1.8}
$$

$$
I_D \le 0.555mA
$$

---

<h1 style="font-size:25px;">DC Analysis</h1>

## Objective

To determine the operating point and verify saturation region.

DC analysis calculates:

- $I_D$
- $V_{SG}$
- $V_{SD}$

to ensure proper biasing.

---

## Saturation Verification

Check:

$$
V_{SD} \ge V_{SG} - |V_{th}|
$$

If satisfied → Proper amplification.

---

## Power Verification

$$
P = V_{DD} \times I_D
$$

Power must satisfy:

$$
P \le 1mW
$$

---

<h1 style="font-size:25px;">Transient Analysis</h1>

## Objective

- Observe time-domain response
- Verify 180° phase shift
- Measure voltage gain

---

## Voltage Gain Calculation

Using peak-to-peak values:

$$
A_v = \frac{V_{out(pp)}}{V_{in(pp)}}
$$

Since PMOS CS amplifier inverts signal:

$$
A_v = - \frac{V_{out(pp)}}{V_{in(pp)}}
$$

---

## Reason for Phase Inversion

When input voltage increases:

- $V_{SG}$ decreases
- Drain current decreases
- Voltage drop across $R_D$ decreases
- Output voltage increases

Thus output is inverted.

---

<h1 style="font-size:25px;">DC Sweep Analysis</h1>

## Objective

To obtain transfer characteristics ($V_{out}$ vs $V_{in}$).

### SPICE Command

```
.dc Vin 0 1.8 0.01
```

---

## Bias Point Selection

For symmetrical output swing:

$$
V_D = \frac{V_{DD}}{2}
$$

$$
V_D = \frac{1.8}{2}
$$

$$
V_D = 0.9V
$$

From DC sweep graph, find $V_{in}$ such that:

$$
V_{out} \approx 0.9V
$$

This becomes the DC bias voltage.

---

<h1 style="font-size:25px;">AC Analysis</h1>

## Objective

To determine:

- Midband gain
- -3 dB frequency
- Bandwidth

---

## Why Load Capacitor is Added

A capacitor (e.g., 10 pF) is added at output to:

- Model load capacitance
- Introduce dominant pole
- Obtain realistic bandwidth

Without capacitor → Bandwidth appears unrealistically high.

---

## Midband Gain (dB)

$$
A_v(dB) = 20 \log_{10} |A_v|
$$

---

## -3 dB Frequency

Half-power frequency occurs when gain drops by 3 dB from midband gain.

$$
BW = f_H - f_L
$$

If no low-frequency cutoff:

$$
BW \approx f_H
$$

---

<h1 style="font-size:25px;">Conclusion</h1>

- PMOS operates in saturation region
- Proper biasing achieved
- Phase inversion verified
- Gain calculated from transient response
- Bandwidth determined from AC analysis
- Power constraint satisfied

The PMOS Common Source amplifier successfully demonstrates voltage amplification with expected theoretical behavior.
