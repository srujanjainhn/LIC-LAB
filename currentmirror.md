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

## Aim : Design and Analyze Current mirror circuit as active load in amplifier circuit.

Given :

Vdd=1.8 V.<br>
P <=1 mW.<br>
Av>-10 V/V.<br>

## Circuit Diagram

![image](https://github.com/srujanjainhn/LIC-LAB/blob/9fa2f609fed7155cfe55a70d612212fdb9d3b0b4/images/Screenshot%202025-04-06%20183740.png)



**Calculation**:

Drain current equation is given by:

ID = (1/2)μnCox(W/L)(VGS - Vth)^2<br>
ITotal = P / VDD<br>
ITotal = Iref + Ix<br>
For 1:1 ratio Iref = Ix<br>
Iref(2) = ITotal<br>
Iref = ITotal/2<br>
ITotal = 1 mW/1.8 V<br>
ITotal = 0.555 mA<br>
Iref = 0.555 m/2<br>
Therefore, Iref = 0.2777 mA.<br>

**Case 1** : 1:1 Current mirror

**DC Analysis**

**Case1: L=180nm**

![image](https://github.com/srujanjainhn/LIC-LAB/blob/8d51eb25f890f100536d5276933432c18b1ab4d0/images/current%20mirror.%5C/Screenshot%202025-04-06%20184109.png)

PMOSFET = length is 180nm, width is 10um<br>
NMOSFET = length is 180nm, width is 114.025um<br>
Vout= 0.967276V<br>
Vx= 0.967276V<br>
Iref = 0.277mA<br>

**Case2: L=500nm**

![image](https://github.com/srujanjainhn/LIC-LAB/blob/8d51eb25f890f100536d5276933432c18b1ab4d0/images/current%20mirror.%5C/Screenshot%202025-04-06%20184118.png)

PMOSFET = length is 500nm, width is 10um<br>
NMOSFET = length is 500nm, width is 207.617um<br>
Vout= 0.644713V<br>
Vx= 0.644703V<br>
Iref = 0.277mA<br>

**Case3: L=1um**

![image](https://github.com/srujanjainhn/LIC-LAB/blob/8d51eb25f890f100536d5276933432c18b1ab4d0/images/current%20mirror.%5C/Screenshot%202025-04-06%20184126.png)

PMOSFET = length is 1um, width is 10um<br>
NMOSFET = length is 1um, width is 251.54um<br>
Vout= 0.293193V<br>
Vx= 0.293177V<br>
Iref = 0.277mA<br>

### Tabular column:
|  Length  |            Width           |   V<sub>x</sub>  | V<sub>out</sub>  |   I<sub>ref</sub>|
|----------|----------------------------|------------------|------------------|------------------|
|   180nm  | Pmos= 10u; Nmos=114.025u   |    0.967276V     |     0.967276V    |    0.277mA       |
|   500nm  | Pmos= 10u; Nmos=207.617u   |    0.644703V     |     0.644713V    |    0.277mA       |
|    1um   | Pmos= 10u; Nmos=251.54u    |    0.293177V     |     0.293193V    |    0.277mA       |


### Transient analysis:
1.Case 1: 180nm
![Image](https://github.com/srujanjainhn/LIC-LAB/blob/8d51eb25f890f100536d5276933432c18b1ab4d0/images/current%20mirror.%5C/Screenshot%202025-04-06%20184142.png)
* Peak to Peak volatge = 1.934V
* Maximum output swing = Vdd-Vov2+Vov3 = 1.8-(-0.00847-0.36)+(0.5-0.36)= 2.29V

<br>

2.Case 2: 500nm
![Image](https://github.com/srujanjainhn/LIC-LAB/blob/8d51eb25f890f100536d5276933432c18b1ab4d0/images/current%20mirror.%5C/Screenshot%202025-04-06%20184159.png)
* Peak to Peak volatge = 1.28V
* Maximum output swing = Vdd-Vov2+Vov3 = 1.8-(-0.00000907-0.36)+(0.5-0.36)= 2.29V

<br>

3.Case 3: 1um
![Image](https://github.com/srujanjainhn/LIC-LAB/blob/8d51eb25f890f100536d5276933432c18b1ab4d0/images/current%20mirror.%5C/Screenshot%202025-04-06%20184213.png)
* Peak to Peak volatge = 0.607V
* Maximum output swing = Vdd-Vov2+Vov3 = 1.8-(0.0000165-0.36)+(0.5-0.36)= 2.29V

<br>

**AC Analysis**

**Case1: L=180nm**

![image](https://github.com/srujanjainhn/LIC-LAB/blob/8d51eb25f890f100536d5276933432c18b1ab4d0/images/current%20mirror.%5C/Screenshot%202025-04-06%20184226.png)

**Case2: L=500nm**

![image](https://github.com/srujanjainhn/LIC-LAB/blob/8d51eb25f890f100536d5276933432c18b1ab4d0/images/current%20mirror.%5C/Screenshot%202025-04-06%20184241.png)

**Case3: L=1um**

![image](https://github.com/srujanjainhn/LIC-LAB/blob/8d51eb25f890f100536d5276933432c18b1ab4d0/images/current%20mirror.%5C/Screenshot%202025-04-06%20184256.png)

### Tabular column:
|  Length  |  3dB Gain   |  3dB Bandwidth   | 
|----------|-------------|------------------|
|   180nm  |    27dB     |   265.185MHz     |
|   500nm  |    36dB     |   52.4645MHz     |     
|    1um   |    35.75dB  |   39.4948MHz     |   

### Inference:
* Reference current is copied or mirrored for other two mosfets.The output currentis exactly equal to the reference current.
* The output current remains the same regardless of the connected load, as long as the transistor stays in the saturation region
* V<sub>x</sub> and V<sub>out</sub> will be same when current gets mirrored.
* As length increases V<sub>x</sub> and V<sub>out</sub> decreases.
* As gain increases bandwidth decreases.
* As the refence current is 0.277mA and doing 1:1 ratio of current mirroring the Current must be copied of the same that is 0.277mA.
* In transient analysis we see the maximum output swing caused.
  
<br>

**Case 2** : 1:2 Current mirror

**Circuit Diagram**

![image](https://github.com/srujanjainhn/LIC-LAB/blob/8d51eb25f890f100536d5276933432c18b1ab4d0/images/current%20mirror.%5C/Screenshot%202025-04-06%20184313.png)




### Components :
PMOSFET-2, NMOSFET- 1, supply volatage-2, current source-1.

### Procedure:

1. Build the circuit as per the circuit diagram using LTspice.
2. Set the Vdd as 1.8V.
3. Download the library file.
4. Create a folder. Save the library file and LTspice file to the folder.
5. Import the library file to LTspice using spice directive(.op).
6. Find the current value for the given power rating.
7.  Set the mosfet model name CMOSN for NMOSFET and CMOSP for PMOSFET as given in the library file, length as 180nm and vary the width  of NMOSFET till you get the exact Q point. Set the gate volatge of NMOSFET as 0.5V. 
8. DC analysis: In edit simulation option, change to dc offset to get list of values obtained from the circuit. We should get the calculated current value in the simulation result.So that we need to vary the value of width since width is directly proportional to Drain current(Id) keeping other parameters constant. Since we are doing current mirroring the current of both mosfets should be same as the reference current even the output also should match too. 
9. Transient analysis: In edit simulation option, change from dc offset to transient. Set the dc offset as 0.5V, Amplitude 5mV, frequency 1KHz. Keep stop time for 3ms and run to get the expected waveform.Find the maximum output swing.
10. AC analysis : In edit simulation option, change from transient to ac analysis. Set type of sweep as decade, number of points per decade as 20, start and stop frequency as 0.1Hz and 1THz to get the expected ac waveform. Note down the 3dB gain of the circuit and its bandwidth.

<br>

### Calculations:
* Power <= 1mW
* Vdd = 1.8V
* I<sub>total</sub> = power/Vdd = 1mW/1.8 = 55.5mA
* I<sub>D</sub>= I<sub>total</sub>/3 = 0.185mA.
* 1:2 ratio = 0.185mA : 0.37mA.

<br>

**DC Analysis**

**Case1: L=180nm**

![image](https://github.com/srujanjainhn/LIC-LAB/blob/8d51eb25f890f100536d5276933432c18b1ab4d0/images/current%20mirror.%5C/Screenshot%202025-04-06%20184332.png)

PMOS1 : L=180nm ; W=70um <br>
PMOS2 : L=180nm ; W=140um <br>
NMOS11 = L=180nm ; W=135.867um<br>
Vout= 1.20094V<br>
Vx= 1.20934V<br>
Iref = 0.185mA<br>

**Case2: L=500nm**

![image](https://github.com/srujanjainhn/LIC-LAB/blob/8d51eb25f890f100536d5276933432c18b1ab4d0/images/current%20mirror.%5C/Screenshot%202025-04-06%20184344.png)

PMOS1 : L=500nm ; W=70um <br>
PMOS2 : L=500nm ; W=140um <br>
NMOS11 = L=500nm ; W=256.773um<br>
Vout= 1.15935V<br>
Vx= 1.16085V<br>
Iref = 0.185mA<br>

**Case3: L=1um**

![image](https://github.com/srujanjainhn/LIC-LAB/blob/8d51eb25f890f100536d5276933432c18b1ab4d0/images/current%20mirror.%5C/Screenshot%202025-04-06%20184358.png)

PMOS1 : L=1um ; W=70um <br>
PMOS2 : L=1um ; W=140um <br>
NMOS11 = L=1um ; W=307.294um<br>
Vout= 1.08026V<br>
Vx= 1.07969V<br>
Iref = 0.185mA<br>

### Tabular column:
|  Length  |                Width            |   V<sub>x</sub>  | V<sub>out</sub> | I<sub>ref</sub>  |
|----------|---------------------------------|------------------|-----------------|------------------|
|   180nm  | Pmos= 70u,140u; Nmos=135.867um  |     1.20934V     |     1.20094V    | 0.185mA : 0.37mA |
|   500nm  | Pmos= 70u,140u; Nmos=256.773um  |     1.16085V     |     1.15935V    | 0.185mA : 0.37mA |
|    1um   | Pmos= 70u,140u; Nmos=307.294um  |    1.07969V      |     1.08026V    | 0.185mA : 0.37mA |


### Transient analysis:
1.Case 1: 180nm
![Image](https://github.com/srujanjainhn/LIC-LAB/blob/8d51eb25f890f100536d5276933432c18b1ab4d0/images/current%20mirror.%5C/Screenshot%202025-04-06%20184419.png)
* Peak to Peak volatge = 2.39V
* Maximum output swing = Vdd-Vov2+Vov3 = 1.8-(-0.00847-0.36)+(0.5-0.36)= 2.30V

<br>

2.Case 2: 500nm
![Image](https://github.com/srujanjainhn/LIC-LAB/blob/8d51eb25f890f100536d5276933432c18b1ab4d0/images/current%20mirror.%5C/Screenshot%202025-04-06%20184430.png)
* Peak to Peak volatge = 2.25V
* Maximum output swing = Vdd-Vov2+Vov3 = 1.8-(-0.0015-0.36)+(0.5-0.36)= 2.3015V

<br>

3.Case 3: 1um
![Image](https://github.com/srujanjainhn/LIC-LAB/blob/8d51eb25f890f100536d5276933432c18b1ab4d0/images/current%20mirror.%5C/Screenshot%202025-04-06%20184441.png)
* Peak to Peak volatge = 2.048V
* Maximum output swing = Vdd-Vov2+Vov3 = 1.8-(0.000575-0.36)+(0.5-0.36)= 2.2V

**AC Analysis**

**Case1: L=180nm**

![image](https://github.com/srujanjainhn/LIC-LAB/blob/8d51eb25f890f100536d5276933432c18b1ab4d0/images/current%20mirror.%5C/Screenshot%202025-04-06%20184453.png)

**Case2: L=500nm**

![image](https://github.com/srujanjainhn/LIC-LAB/blob/8d51eb25f890f100536d5276933432c18b1ab4d0/images/current%20mirror.%5C/Screenshot%202025-04-06%20184509.png)

**Case3: L=1um**

![image](https://github.com/srujanjainhn/LIC-LAB/blob/8d51eb25f890f100536d5276933432c18b1ab4d0/images/current%20mirror.%5C/Screenshot%202025-04-06%20184535.png)

### Tabular column:
|  Length  |  3dB Gain   |  3dB Bandwidth   | 
|----------|-------------|------------------|
|   180nm  |  26.212dB   |   105.81654MHz   |
|   500nm  |  34.71dB    |   29.731326MHz   |     
|    1um   |  37dB       |   18.6247MHz     |   

### Inference:
* Reference current is copied or mirrored for other two mosfets.The output currentis exactly equal to the reference current.
* The output current remains the same regardless of the connected load, as long as the transistor stays in the saturation region
* V<sub>x</sub> and V<sub>out</sub> will be same when current gets mirrored.
* As length increases V<sub>x</sub> and V<sub>out</sub> decreases.
* As gain increases bandwidth decreases.
* As the refence current is 0.277mA and doing 1:2 ratio of current mirroring the Current must be copied of the same that is in the form of 0.185mA : 0.37mA..
* In transient analysis we see the maximum output swing caused.

<br>

**Part B**

Aim : Design the diffrential amplifier having VDD=2V, P<=1mW, Vicm =1V as per the 3rd experiment and perform DC, Transient , AC analysis.<br>

**Circuit Diagram**

![image](https://github.com/srujanjainhn/LIC-LAB/blob/8d51eb25f890f100536d5276933432c18b1ab4d0/images/current%20mirror.%5C/Screenshot%202025-04-06%20184555.png)

### Components:
PMOSFET-2, NMOSFET- 4, supply volatage-4, current source-1, ground, wires.

### Circuit overview:
1.Differential Pair (M3, M4):
* M3 and M4 form a differential pair using NMOS transistors.
* They receive differential input signals and control the output voltage.

<br>

2.Active Load (M1, M2):
* M1 and M2 are PMOS transistors serving as a current mirror load.
* This helps in converting the differential input signal into a single-ended output.

<br>

3.Current Source (M5, M6, I1):
* M6 is an NMOS transistor acting as a current source to bias the differential pair.
* I1 (0.25 mA) sets the tail current, ensuring proper operation.

<br>

4.Biasing Voltages (V1, V2, V3, V5):
* V1 and V2 (1V) provide gate biasing for M3 and M4.
* V3 and V5 (2V) power the PMOS transistors and ensure proper operation.

<br>
  
5.Output (Vout):
* The output is taken from the common node of M2 and M4.
* It provides an amplified voltage signal.

<br>

### Calculation:
* P=1mW
* I<sub>total</sub> = P/V = 1mW/2V =0.5mA
* I<sub>D1</sub> = I<sub>D2</sub> = I<sub>total</sub>/2 = I<sub>ref</sub> =0.25mA 
* V<sub>DD</sub>= 2V
* V<sub>inCM</sub>=1V

<br>


**DC Analysis**

**Case1: L=180nm**

![image](https://github.com/srujanjainhn/LIC-LAB/blob/8d51eb25f890f100536d5276933432c18b1ab4d0/images/current%20mirror.%5C/Screenshot%202025-04-06%20184631.png)

M1,M2 = W=70um<br>
M3, M4 = W=238.7um<br>
M5 = W=70um<br>
M6 = W=140um<br>
Vout= 1.39017V<br>
Iref = 0.25mA<br>

**Case2: L=500nm**

![image](https://github.com/srujanjainhn/LIC-LAB/blob/8d51eb25f890f100536d5276933432c18b1ab4d0/images/current%20mirror.%5C/Screenshot%202025-04-06%20184654.png)

M1,M2 = W=70um<br>
M3, M4 = W=693.6um<br>
M5 = W=70um<br>
M6 = W=140um<br>
Vout= 1.32674V<br>
Iref = 0.25mA<br>

**Case3: L=1um**

![image](https://github.com/srujanjainhn/LIC-LAB/blob/8d51eb25f890f100536d5276933432c18b1ab4d0/images/current%20mirror.%5C/Screenshot%202025-04-06%20184723.png)

M1,M2 = W=70um<br>
M3, M4 = W=223.35um<br>
M5 = W=70um<br>
M6 = W=141um<br>
Vout= 1.22711V<br>
Iref = 0.25mA<br>

### Tabular column:  
|  Length  |                       Width                   |  V<sub>out</sub> | I<sub>ref</sub>  |
|----------|-----------------------------------------------|------------------|------------------|
|   180nm  | M1,M2=70um,M3, M4 =238.7um,M5 =70um, M6=140um |      1.39017V    |  0.277mA         |
|   500nm  | M1,M2=70um,M3, M4 =693.6um,M5 =70um, M6=140um |      1.32674V    |  0.277mA         |
|    1um   | M1,M2=70um,M3, M4 =223.35um,M5 =70um, M6=141um|      1.22711V    |  0.277mA         |

<br>

### Transient analysis:
1.Case 1: 180nm
![Image](https://github.com/srujanjainhn/LIC-LAB/blob/8d51eb25f890f100536d5276933432c18b1ab4d0/images/current%20mirror.%5C/Screenshot%202025-04-06%20184749.png)
* Peak to Peak volatge = 2.7794V

<br>

2.Case 2: 500nm
![Image](https://github.com/srujanjainhn/LIC-LAB/blob/8d51eb25f890f100536d5276933432c18b1ab4d0/images/current%20mirror.%5C/Screenshot%202025-04-06%20184803.png)
* Peak to Peak volatge = 2.653V

<br>

3.Case 3: 1um
![Image](https://github.com/srujanjainhn/LIC-LAB/blob/47fb53efd9d5c8217e95bd2405adca9f6a413f92/images/current%20mirror.%5C/Screenshot%202025-04-06%20192945.png)
* Peak to Peak volatge = 2.453V

<br>

**AC Analysis**

**Case1: L=180nm**

![image](https://github.com/srujanjainhn/LIC-LAB/blob/47fb53efd9d5c8217e95bd2405adca9f6a413f92/images/current%20mirror.%5C/Screenshot%202025-04-06%20192957.png)

**Case2: L=500nm**

![image](https://github.com/srujanjainhn/LIC-LAB/blob/47fb53efd9d5c8217e95bd2405adca9f6a413f92/images/current%20mirror.%5C/Screenshot%202025-04-06%20193009.png)

**Case3: L=1um**

![image](https://github.com/srujanjainhn/LIC-LAB/blob/47fb53efd9d5c8217e95bd2405adca9f6a413f92/images/current%20mirror.%5C/Screenshot%202025-04-06%20193024.png)

### Tabular column:
|  Length  |  3dB Gain   |  3dB Bandwidth   | 
|----------|-------------|------------------|
|   180nm  |  32dB       |   107.9033MHz    |
|   500nm  |  41.131dB   |   17.075083MHz   |     
|    1um   |  43.32dB    |   24.278305MHz   |   

### Inference:

1.DC Analysis:
* As the transistor length increases, the output voltage (Vout) decreases.
* This happens because longer channel lengths increase the resistance, affecting the current flow and voltage distribution.
* Reference current (Iref) remains constant (0.277mA) across different lengths.
* This shows that the current source (M5 & M6) is properly designed to maintain a steady bias.

<br>

2.Transient Analysis:
* Peak-to-peak voltage (Vpp) decreases with increasing transistor length.
* Longer transistors have higher parasitic capacitances, which slow down the signal response, reducing output swing.
* Shorter channel transistors (180nm) provide better signal swings, making them preferable for high-speed applications.

<br>


3.AC Analysis:
* 3dB Gain increases as transistor length increases.
180nm → 32dB\
500nm → 41.13dB\
1µm → 43.32dB\
* Longer transistors reduce channel-length modulation, leading to better gain performance.
* Bandwidth decreases with increasing transistor length.
180nm → 107.9MHz\
500nm → 17.08MHz\
1µm → 24.28MHz\
* Shorter transistors have lower capacitance, allowing higher frequencies to pass, resulting in a wider bandwidth.
