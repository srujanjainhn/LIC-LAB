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

## Simulation 

<br>**For 1:1 Aspect Ratio**</br>
Part A : <p>Design a current mirror circuit which has a gain of AV = -10V/V, power supply of Vdd = 1.8V, and power of P <= 1mW. Find reference current (Iref), output current (Id), and total current (Itotal). Perform DC and AC analysis for mirror ratio 1:1, 1:2.</p>
![Image](https://github.com/user-attachments/assets/4fcd86ec-967b-4d96-98ed-6e4da85dbf7c)
  -  The MOSFET should be in saturation region 
<table>
<td>V1>V<sub>th</sub></td>
</table>
i.e 0.5>0.366
 
  -  I<sub>taotal</sub>=P/V<sub>dd</sub>
<table>
<td>I<sub>total</sub>=0.55mA</td>
</table>
I<sub>total</sub>=I<sub>ref</sub> + I<sub>p</sub>
I<sub>ref</sub>=I<sub>p</sub>=(I<sub>total</sub>)/2
<table>
<td>I<sub>ref</sub>=I<sub>p</sub>=0.27mA</td>
</table>

![Image](https://github.com/user-attachments/assets/9b97f1b6-8c16-45cb-90f8-ac0348f00216)  ![Image](https://github.com/user-attachments/assets/92dda9af-d6bb-4973-8655-4f7277f4715e)
 <table> 
<tr>
 <th><b>Parameters</b></th>
 <th><b>MOSFET1</b></th>
 <th><b>MOSFET2</b></th>
 <th><b>MOSFET3</b></th>
</tr>
<tr>
    <td>Model</td>
    <td>CMOSP</td>
    <td>CMOSP</td>
    <td>CMOSN</td>
</tr>
<tr>
    <td>Length</td>
    <td>180nm</td>
    <td>180nm</td>
    <td>180nm</td>
</tr>
<tr>
    <td> Width</td>
    <td>70µm</td>
    <td>70µm</td>
    <td>100.0217999um</td>
</tr>
<tr>
    <td>V<sub>th</sub></td>
    <td> -0.509V</td>
    <td> -0.509V</td>
    <td> 0.495V</td>
</tr>
    <tr>
      <td>Current(I)</td>
      <td>  0.27mA </td>
      <td>  0.270211mA </td>
      <td> 0.270211mA </td>
    </tr>
    <tr>
      <td>Supply Voltage</td>
      <td> 1.8V</td>
      <td> 1.8V</td>
      <td> --- </td>
    </tr>
     <tr>
      <td>Biased Voltage</td>
      <td> --- </td>
      <td> --- </td>
      <td> 0.5697V</td>
    </tr>
</table>
From dc analysis: <br>
V<sub>out</sub> = 1.18143, which is nearly equal to V<sub>x</sub>  i.e  1.18498</br>
I<sub>ref</sub> =0.27mA and I<sub>d</sub> = 0.270211 <br> There is small diviation due to Lamda Effect.

**Transient Analysis**

![Image](https://github.com/user-attachments/assets/caf81b29-cc6f-4c73-8199-200d1dddf341)
The input voltage given for N-MOS is 0.5 and amplitude of 9mV with frequency of 1kHz. <br>
Can observe the output voltage V<sub>out</sub> = 1.42V
 **AC Analysis**
 
![Image](https://github.com/user-attachments/assets/d4cab0bb-1981-4f63-8ba8-557eb7cdd56f)
The obtained gain A<sub>v</sub> is 29.488<sub>dB</sub>. <br>
29.488 - 3 = 26.488<sub>dB</sub>. <br>
The frequency for this particular dB is 58.237MHz, the bandwidth can be calculated as f<sub>H</sub> - f<sub>L</sub>. <br>
= 58.237MHz - 1Hz <br>
= 57.237MHz <br>
## For 1:2 Aspect Ratio
 <table> 
<tr>
 <th><b>Parameters</b></th>
 <th><b>MOSFET1</b></th>
 <th><b>MOSFET2</b></th>
 <th><b>MOSFET3</b></th>
</tr>
<tr>
    <td>Model</td>
    <td>CMOSP</td>
    <td>CMOSP</td>
    <td>CMOSN</td>
</tr>
<tr>
    <td>Mosfet Length</td>
    <td>180nm</td>
    <td>180nm</td>
    <td>180nm</td>
</tr>
<tr>
    <td>Mosfet Width</td>
    <td>70um</td>
    <td>140µm</td>
    <td>140u</td>
</tr>
<tr>
    <td>Threshold Voltage</td>
    <td> -0.509V</td>
    <td> -0.509V</td>
    <td> 0.495V</td>
</tr>
    <tr>
      <td>Current(I)</td>
      <td> I<sub>ref</sub> = 0.185mA </td>
      <td> I<sub>d</sub> = 0.373554mA </td>
      <td> I<sub>d</sub> = 0.373554</td>
    </tr>
    <tr>
      <td>Supply Voltage</td>
      <td> 1.8V</td>
      <td> 1.8V</td>
      <td> --- </td>
    </tr>
     <tr>
      <td>Biased Voltage</td>
      <td> --- </td>
      <td> --- </td>
      <td> 0.5V</td>
    </tr>
</table>

<br>**DC Analysis**</br>

![Image](https://github.com/user-attachments/assets/33a0610a-3d0d-4107-829a-96188918d8c4)
From dc analysis: <br>
V<sub>out</sub> = 1.158341V	 
I<sub>ref</sub> =  0.185mA

**Transient Analysis**

![Image](https://github.com/user-attachments/assets/ac0ea772-5f05-40d7-bad1-19edac3cab27)
**AC Analysis**

![Image](https://github.com/user-attachments/assets/4e4c277d-b1dc-49bb-b455-00c224e7fc59)
The obtained gain from the simulation is 29.23<sub>dB</sub>. <br>
29.23 - 3 = 26.23<sub>dB</sub>. <br>
The frequency for this particular dB is 27.426MHz, the bandwidth can be calculated as f<sub>H</sub> - f<sub>L</sub>. <br>
= 27.426MHz - 1Hz <br>
= 26.426MHz <br>
## Bonus Question 

![Image](https://github.com/user-attachments/assets/8af0aa43-3374-4ed9-be95-1fd4dbcbd5d4)
<ins>Observed Table</ins> <br>
For I<sub>ref</sub> = 100u <br>

  <table> 
<tr>
 <th><b>I<sub>out(expected)</sub>(A)</b></th>
 <th><b>I<sub>out(appeared)</sub>(A)</b></th>
 <th><b>(W/L)<sub>2</sub>(m)</b></th>
 <th><b>(W/L)<sub>1</sub>(m)</b></th>
 <th><b>V<sub>x</sub>(V)</b></th>
 <th><b>V<sub>out</sub>(V)</b></th>
</tr>
<tr>
    <td>100µ</td>
    <td>103.06µ</td>
    <td>(180n/180n)</td>
    <td>(180n/180n)</td>
    <td>1.275V</td>
    <td>1.71512V</td>
</tr>
<tr>
    <td>100µ</td>
    <td>100.7µ</td>
    <td>(500n/500n)</td>
    <td>(500n/500n)</td>
    <td>1.4385V</td>
    <td>1.717V</td>
</tr>
<tr>
    <td>100µ</td>
    <td>100.648µ</td>
    <td>(1µ/1µ)</td>
    <td>(1µ/1µ)</td>
    <td>1.39827V</td>
    <td>1.717V</td>
</tr>
<tr>
    <td>200µ</td>
    <td>197.637µ</td>
    <td>(1µ/1µ)</td>
    <td>(1µ/2µ)</td>
    <td>1.39727V</td>
    <td>1.63734V</td>
</tr>
    <tr>
      <td>50µ</td>
    <td>52.1312µ</td>
    <td>(1µ/1µ)</td>
    <td>(1µ/0.5µ)</td>
    <td>1.3972V</td>
    <td>1.75725V</td>
    </tr>
   
</table> 

## Part B
<b>Design the differential amplifier using the same design specification as experiment 3(differential amplifier). Perform DC, Transient, AC analysis for this.</b> <br>

![Image](https://github.com/user-attachments/assets/7b197f26-3a70-479d-8e32-ee017eaa928e)

**DC Analysis**


![Image](https://github.com/user-attachments/assets/7833efce-2fe1-42f1-9aa8-cca3333b25be)

**Transient Analysis**

![Image](https://github.com/user-attachments/assets/7a7e4b76-1c6a-4f2c-9185-b767e4045f97)

**AC Analysis**

![Image](https://github.com/user-attachments/assets/0e8cc948-4f91-45b8-8eef-55613092c065)

The gain of the circuit is 30.977dB.
<br>BandWdith is 187.35MHz - 1Hz = 186.35MHz

## Inference

<br> 1.Current mirrors copy a reference current accurately, making them useful in many electronic circuits.</br>
<br> 2.Changes in manufacturing, power supply, or temperature can affect performance, but using a stable reference current helps reduce these effects.</br>
<br> 3.NMOS current mirrors work faster, while PMOS current mirrors provide better stability and accuracy.</br>
<br> 4.Small errors occur due to transistor properties, but using longer transistors or special designs can fix this.</br>
<br> 5.Larger transistor sizes improve accuracy, but they also take up more space on the chip.</br>
<br> 6.DC analysis confirms the circuit is working correctly, with the mirrored current closely matching the expected values.</br>
<br> 7.AC analysis shows the circuit has a high gain and wide frequency range, making it good for high-speed applications.</br>
<br> 8.Transient analysis proves that the circuit responds well to changing signals, meaning it works reliably in real-world use.</br>
<br> 9.Using current mirrors in amplifiers gives high gain (~31 dB) and wide bandwidth (~186 MHz), which is great for precise signal processing.</br>
<br> 10.Choosing the right transistor size and reference current is important to get the best balance between power, accuracy, and performance.</br>
