##Experiment 3:- MOS Differential Amplifier 
## AIM:Design and analyse the MOS differential amplifier circuit for the given specification.
VDD=3.3V

P<=3mW

Vicm=1.72V

Vocm=1.81V

Vp= 0.7V
### *Perform DC analysis, transient analysis and frequency response and extract the required paramenters.* 

## introduction:


A MOS differential amplifier is an important circuit used to amplify the difference between two input signals, while minimizing noise that affects both inputs equally. This makes it essential in applications where precision is key. In this experiment, we’ll dive into the key performance factors of the amplifier, like its differential-mode gain, common-mode gain, and common-mode rejection ratio (CMRR). By measuring and analyzing these factors, we’ll get a hands-on understanding of how the amplifier works and why it’s so valuable in real-world scenarios.

The amplifier works in two main ways:

1. **Common Mode**: This looks at the part of the signals that the inputs share, essentially the average voltage between them, calculated as (V₁ + V₂) / 2. It’s the common signal both inputs have in common.

2. **Differential Mode**: This mode focuses on the difference between the two inputs, which is represented as V₁ - V₂. This is the signal that the amplifier is meant to amplify, and it’s typically the one we care about most in practical applications.

By looking at these two modes, we can better understand how the amplifier handles different signals and why it’s so good at reducing unwanted noise in situations where accuracy matters.


**Circuit Diagram:**
![MOS differential amplifier](https://github.com/srujanjainhn/LIC-LAB/blob/91caaaa34cf4eaac888352cc663904416c701fbc/images/images./1.png)

**Working Principle**
### Working Principle of a MOS Differential Amplifier

**Differential Input:** The amplifier works by processing the difference between two input signals, amplifying just the difference (called the differential component) while rejecting any signals that are common to both inputs. This helps the amplifier ignore noise that affects both inputs equally, improving its overall noise immunity.

**Current Source Biasing:** A stable current source provides a constant bias current (Ib) to the amplifier, ensuring the circuit operates consistently and predictably.

**Output Voltages:** The amplified signal, which represents the difference between the two inputs, appears at the output terminals (Vout+ and Vout-). This output can then be used for further processing, depending on the specific application.

### Current Flow in the Circuit

The total current flowing through both MOSFETs (ID1 + ID2) always equals the bias current (IB), which remains constant.

In an ideal scenario where both MOSFETs are perfectly matched and no differential input voltage is applied, each MOSFET will conduct exactly half of the bias current (IB).

When a differential input is applied, the current through one transistor increases while the current through the other decreases. However, the total current (ID1 + ID2) stays the same, ensuring the circuit remains stable.

### Behavior in Saturation Mode

When the MOSFETs are operating in saturation mode, their drain current follows a specific equation:

ID = 1/2 un Cox W/L (VGS - Vth)^2 (1 + lambda VDS)

Since the bias current (IB) is fixed, the circuit adjusts the source voltage so that the gate-to-source voltage (VGS) is set correctly to produce the needed drain current. This automatic adjustment ensures the amplifier operates as required.

### Circuit 1
![Screenshot 2025-03-09 175910](https://github.com/srujanjainhn/LIC-LAB/blob/91caaaa34cf4eaac888352cc663904416c701fbc/images/images./2.JPG)

## DC Analysis:
The DC analysis of a MOS differential amplifier establishes the transistors' operating point (bias conditions) by varying the input voltages and examining the resulting DC output voltages and currents.
![Screenshot 2025-03-09 180533](https://github.com/srujanjainhn/LIC-LAB/blob/91caaaa34cf4eaac888352cc663904416c701fbc/images/images./4.JPG)
![Screenshot 2025-03-09 180634](https://github.com/srujanjainhn/LIC-LAB/blob/78aa30e6ef0e96759a0067512c9131f40ecdd7b9/images/images./6.png)

Length( M1 and M2) = 180nm

Width ( M1 and M2) = 2.0558um

for mosfet M1:

Vicm = 1.72V

Vocm = 1.81V

Id(M1) = 0.37mA

Vtn = 0.487V


VDD = IdRd + VDS +Vp

VDS = 3.3 - 1.454 - 0.7

VDS = 1.146V

for mosfet M2:

Vicm = 1.72V

Vocm = 1.81V

Id(M2) = 0.37mA

Vtn = 0.487V

VDD = IdRd + VDS +Vp

VDS = 3.3 - 1.454 - 0.7

VDS = 1.146V


The Q-points of both the mosfets(M1 and M2) are (1.146V, 0.37mA)

### Transient Analysis:

Transient analysis is a method used to observe how a circuit behaves over time when it is exposed to changing inputs, such as pulses, sine waves, or step signals. This type of analysis is especially important in high-speed applications, as it helps assess key factors like rise time, fall time, and propagation delay, all of which affect how well an amplifier can handle fast signals. Additionally, transient analysis shows how a MOSFET reacts to sudden changes in input voltage or load conditions, giving valuable insights into the circuit’s performance during dynamic situations.

![Screenshot 2025-03-09 184903](https://github.com/srujanjainhn/LIC-LAB/blob/e89c2c90d7059577ab1b129ff1bdeca2399c7564/images/images./7.png)

**Input and Output Waveform**
![image](https://github.com/srujanjainhn/LIC-LAB/blob/e89c2c90d7059577ab1b129ff1bdeca2399c7564/images/images./3.JPG)


From the graph ,we can observe the 180 degree phase shift in the output signal and the output voltage (at Vocm node) is amplified .

**Gain(Av) = Voutpeak/Vinpeak**

=1.875-1.7504/1.7705-1.6709  = 1.251V/V
**20log(1.251)dB =1.9451dB ** 

## AC Analysis

![image](https://github.com/srujanjainhn/LIC-LAB/blob/39e8c0b9e2569ee4bf748f99d7e362ac54155ef4/images/images./8.png)

![image](https://github.com/srujanjainhn/LIC-LAB/blob/39e8c0b9e2569ee4bf748f99d7e362ac54155ef4/images/images./5.JPG)

From the graph gain in dB scale is
20log(1.251)=1.9451dB


