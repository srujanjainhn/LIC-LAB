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


## Circuit 2
By replacing resistor (R3) with a current source (Iss), the circuit is transformed into a fully differential pair with an active current source. This change removes source degeneration, which boosts the amplifier's gain and improves its ability to reject common-mode signals (CMRR). The current source helps maintain a stable bias current, making the circuit less sensitive to variations in component values. Without (R3), the transconductance (gm) becomes higher, leading to a greater differential gain, which is given by the formula (Ad = gm * rd). In simpler terms, the current source ensures the circuit runs more reliably and efficiently, providing better performance overall.


![image](https://github.com/srujanjainhn/LIC-LAB/blob/9b45c61b757819528fd6fd0834e27d98d7c61d1a/images/images./25.jpg)

## DC Analysis

![image](https://github.com/srujanjainhn/LIC-LAB/blob/9b45c61b757819528fd6fd0834e27d98d7c61d1a/images/images./26.png)

![image](https://github.com/srujanjainhn/LIC-LAB/blob/9b45c61b757819528fd6fd0834e27d98d7c61d1a/images/images./27.png)


Mosfet aspect ratio was same ie, L= 180nm, W = 2.0553um

for mosfet M1 & M2:

Vicm = 1.72V

Vocm = 1.81V

Id= 0.37mA

Vtn = 0.487v

VDD = IdRd + VDS +Vp

VDS =3.3 - 1.454 - 0.7

VDS = 1.146 V

The Q-point of both the mosfets are (1.146V, 0.37mA).


## Transient Analysis


**Input and Output Waveform**
![image](https://github.com/srujanjainhn/LIC-LAB/blob/9b45c61b757819528fd6fd0834e27d98d7c61d1a/images/images./21.png)

From the above observation
Gain Av=Vout(peak)/Vin(peak)
Av= 0.3156/0.1004 = 3.143 V/V
Converting it to the decibel(dB):
20log(3.143) = 9.94 dB


## AC Analysis
![image](https://github.com/srujanjainhn/LIC-LAB/blob/9b45c61b757819528fd6fd0834e27d98d7c61d1a/images/images./24.png)

From the graph gain in dB scale is
20log(3.143)=9.94dB


## Circuit 3

### Differential Amplifier with NMOS Current Source Biasing

In this circuit, we've upgraded the typical differential amplifier by replacing the traditional tail resistor with an NMOS transistor (M3), which acts as a current source. This change improves the stability and control of the bias current for the differential pair (M1 and M2), leading to a more consistent operating point and better common-mode rejection.

By using an active NMOS current source, the circuit becomes more accurate and stable when amplifying the difference between the input signals (V2 and V1). This setup ensures the bias current is more tightly regulated, which is especially important for applications that require precise signal processing and strong resistance to unwanted noise that affects both inputs equally. While the core function of amplifying the difference between the inputs remains the same, the active biasing approach enhances the circuit’s overall performance and reliability.

## Circuit Diagram
![image](https://github.com/srujanjainhn/LIC-LAB/blob/cf383d49f9030ee4a1b6ad34ec1a34e779be0667/images/images./4.1.jpg)

## DC Analysis
![image](https://github.com/srujanjainhn/LIC-LAB/blob/cf383d49f9030ee4a1b6ad34ec1a34e779be0667/images/images./4.2.png)
![image](https://github.com/srujanjainhn/LIC-LAB/blob/5df19382ae45936abbe12fb0b4720941fb714f2d/images/4.5.png)


Mosfet aspect ratio was same ie, L= 180nm, W = 2.0549um

for mosfet M1 & M2:

Vicm = 1.72V

Vocm = 1.81V

Id= 0.37mA

Vtn = 0.487v

VDD = IdRd + VDS +Vp

VDS =3.3 - 1.454 - 0.7

VDS = 1.146 V

The Q-point of both the mosfets are (1.146V, 0.37mA).


## Transient Analysis


**Input and Output Waveform**
![image](https://github.com/srujanjainhn/LIC-LAB/blob/5df19382ae45936abbe12fb0b4720941fb714f2d/images/images./4.3.png)

From the above observation
Gain Av=Vout(peak)/Vin(peak)
Av= 0.3126/0.0974 = 3.209V/V
Converting it to the decibel(dB):
20log(3.209) = 10.127 dB


## AC Analysis
![image](https://github.com/srujanjainhn/LIC-LAB/blob/5df19382ae45936abbe12fb0b4720941fb714f2d/images/images./4.4.png)


From the graph gain in dB scale is
20log(3.209)=10.127dB

### Inference: Impact of Different Tail Current Sources in a Differential Amplifier

#### **With Resistor (Rss) as the Tail Current Source:**

**Moderate Differential Gain:**  
The differential gain is limited when using a resistor (Rss) as the tail current source. The amount of current flowing through the differential pair depends on the resistance value, which ultimately limits the amount of amplification the circuit can provide.

**Reason:** A resistor doesn’t actively regulate the current, so it directly controls the flow of current through the differential pair. This limitation restricts how much gain can be achieved.

**Limited Output Voltage Swing:**  
The output voltage swing is also restricted because of the voltage drop across the tail resistor. As the output voltage nears the supply voltage, the current through the resistor drops, limiting the available range for the output signal.

**Reason:** The voltage drop across Rss reduces the supply voltage available for the output, meaning the output signal can’t swing as far before hitting the supply limits.

**Lower Common-Mode Rejection Ratio (CMRR):**  
With a resistor, the CMRR is lower because the tail resistor provides lower impedance, making the circuit more vulnerable to common-mode signals.

**Reason:** The low impedance of Rss allows common-mode signals to affect both sides of the differential pair similarly, making it harder for the circuit to reject unwanted noise.

---

#### **With an Ideal Current Source (Iss) as the Tail Current Source:**

**Higher Differential Gain:**  
When an ideal current source is used, the tail current stays constant, which improves the differential gain by ensuring a steady current supply to the differential pair.

**Reason:** The constant tail current allows the differential pair to operate more effectively, resulting in greater amplification of the input signals.

**Better Output Voltage Swing:**  
An ideal current source eliminates the voltage drop issues that occur with resistors, giving the circuit a broader output voltage range.

**Reason:** Unlike a resistor, an ideal current source doesn’t cause a significant voltage drop, so there’s more headroom for the output signal to swing without hitting supply limits.

**Higher CMRR:**  
An ideal current source offers high impedance, which enhances the circuit's ability to reject common-mode noise, making it less affected by external interference.

**Reason:** The high impedance helps keep the tail current stable, ensuring that variations in power supply or common-mode signals don’t affect the differential pair, improving noise rejection.

---

#### **With NMOS Transistor as the Tail Current Source:**

**Maximum Differential Gain:**  
Using an NMOS transistor as the tail current source provides the highest differential gain. The NMOS transistor actively regulates the tail current with high impedance, keeping the circuit more stable and allowing for the maximum possible gain.

**Reason:** The NMOS current source ensures the tail current is regulated and remains constant, allowing the differential pair to stay optimally biased and achieve the highest gain.

**Widest Output Voltage Swing:**  
An NMOS current source minimizes the voltage loss in the tail, allowing for the largest possible output signal swing.

**Reason:** Unlike a resistor, the NMOS current source has a much lower voltage drop, preserving more of the supply voltage for the output signal to swing over a wider range.

**Best CMRR:**  
The NMOS current source provides the highest impedance, leading to the best common-mode rejection ratio. This results in the greatest isolation from supply fluctuations and external noise.

**Reason:** The high impedance of the NMOS transistor helps keep the tail current stable, preventing common-mode signals from affecting the differential pair, resulting in superior noise rejection.

---

### **Summary of Reasons:**

**Resistor (Rss):**  
- Limits current flow, which restricts differential gain.  
- Causes a voltage drop, reducing the output swing.  
- Low impedance makes the circuit more sensitive to common-mode noise.

**Ideal Current Source:**  
- Supplies a constant current, improving differential gain.  
- Eliminates voltage drop issues, allowing for a wider output swing.  
- High impedance helps improve common-mode rejection.

**NMOS Current Source:**  
- Acts as an active, high-impedance source, optimizing differential gain.  
- Minimizes voltage loss, providing the widest output swing.  
- Offers the best isolation from interference, resulting in the highest CMRR.


