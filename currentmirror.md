### **Current Mirror Overview**

A **current mirror** is a crucial component in analog circuits, designed to replicate a reference current from one transistor to another. It's used in many circuits such as biasing systems, active loads, and differential amplifiers. In essence, it helps maintain a stable current flow (Iref = Iout), ensuring that the current at the output is as close to the reference current as possible.

Here’s a simple illustration to understand how it works:

![Current Mirror Diagram](https://github.com/user-attachments/assets/1768da11-0189-48ea-9dc7-6f677b3c4609)


### **How a Current Mirror Works:**

#### 1. **Generating the Reference Current (Iref):**
- The first transistor (M1) is set up so that its drain and gate are shorted, which is known as a **diode-connected** configuration.
- A reference current (Iref) is passed through M1 using a current source or resistor.
- This current sets the **gate-source voltage** (Vgs1) of M1, which defines its operating point.

#### 2. **Mirroring the Current:**
- The second transistor (M2) has its gate connected to the gate of M1, so both transistors share the same Vgs.
- If both transistors are designed the same way (same W/L ratio and operating in saturation mode), they will conduct the same current.
- The output current (Iout) will therefore be nearly equal to the reference current (Iref).

#### 3. **Scaling the Output Current:**
- If the **W/L ratio** (width-to-length ratio of the transistors) is different for M2 compared to M1, the output current will be scaled.
  
The relationship can be expressed as:
\[ I_{out} = \left( \frac{W}{L} \right)_2 \div \left( \frac{W}{L} \right)_1 \times I_{ref} \]

This means the output current can be adjusted depending on the transistor dimensions.

---

### **Key Requirements for Proper Operation:**

1. **Saturation Mode:**
   - Both transistors should operate in **saturation** mode to ensure that the drain current depends only on the gate-source voltage (Vgs) and not the drain-source voltage (Vds).

2. **Matching Transistors:**
   - The two transistors need to be as identical as possible. Small differences in their characteristics (like threshold voltage) can lead to inaccuracies.

3. **Channel Length Modulation:**
   - In reality, changes in the **Vds** (drain-source voltage) cause slight variations in the output current. This is called **channel length modulation**.
   - To minimize this issue, a **cascode current mirror** can be used, which improves the output resistance and reduces the effect of Vds variations.

---

### **PMOS Current Mirror:**

![PMOS Current Mirror](https://github.com/user-attachments/assets/1a870006-1e99-448a-b5e7-c4ddd99f8417)

In a **PMOS current mirror**, both transistors are **PMOS** types, and their source terminals are connected to the supply voltage (Vdd). The output current and reference current are related the same way as in an NMOS current mirror.

For the PMOS version:
\[ I_{out} = \left( \frac{W}{L} \right)_2 \div \left( \frac{W}{L} \right)_1 \times I_{ref} \]

The main thing to ensure here is that the first transistor (M1) operates in **saturation** mode. Specifically, the condition to check is that the source-drain voltage (Vsd) should be greater than or equal to the gate-source voltage minus the threshold voltage of the PMOS (Vtp).

---

### **Simulation: NMOS Current Mirror Circuit with a Resistive Load**

#### **Components & Functionality:**
- **V1 (1.8V Supply):** Provides the operating voltage for the circuit.
- **Iref (100µA):** Sets the reference current flowing through the second transistor (M2).
- **M2 (Diode-Connected NMOS):** Operates in saturation mode and defines the gate voltage Vx.
- **M1 (Mirroring NMOS):** Copies the current from M2 and sends it to the load resistor (R1).
- **R1 (820Ω Load Resistor):** Converts the output current into a measurable voltage.

#### **Circuit Diagram:**

![Circuit Diagram](https://github.com/user-attachments/assets/f1a42946-8c17-4549-82df-3ef7a192b852)

---

### **Observation Table:**

For a reference current of **Iref = 100µA**, the following results were observed:

| Iout (Expected) | Iout (Actual)  | (W/L)₂       | (W/L)₁       | Vx (V) | Vout (V) |
|-----------------|----------------|--------------|--------------|--------|----------|
| 100μA           | 103.5μA        | 180n/180n    | 180n/180n    | 1.27   | 1.71     |
| 100μA           | 10.715μA       | 500n/500n    | 500n/500n    | 1.43   | 1.717    |
| 100μA           | 100.648μA      | 1μ/1μ        | 1μ/1μ        | 1.39   | 1.7174   |
| 200μA           | 197.6μA        | 1μ/2μ        | 1μ/2μ        | 1.397  | 1.63     |
| 100μA           | 101.5μA        | 1μ/2μ        | 1μ/2μ        | 1.087  | 1.716    |
| 100μA           | 102.131μA      | 1μ/3μ        | 1μ/3μ        | 0.95   | 1.7172   |

#### **Observations:**

- In most cases, the **output current (Iout)** is slightly higher than expected. For example, with a W/L ratio of 180n/180n, the expected Iout is 100µA, but the measured value is 103.5µA. This happens due to **channel length modulation**, where the effective channel length decreases as the drain-source voltage increases, leading to a higher drain current.
- **Shorter channel lengths** (higher W/L ratios) show more deviation from the expected value. For instance, with W/L = 500n/500n, Iout drops significantly to 10.715μA, which is much lower than expected. This happens because shorter channels have larger variations due to the **channel length modulation effect**.
- **Longer transistors** (increased L) show more stability. As L increases, the gate voltage Vx decreases, which stabilizes the output current (Iout).

---

This explanation should give you a clear idea of how a current mirror works, its key principles, and the results of the simulation. Let me know if you need further clarification or have any additional questions!
