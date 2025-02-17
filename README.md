 DESIGN  1 :    Analysis of CS amplifier

**AIM**: To explore how a MOSFET-based Common Source (CS) Amplifier works by simulating it in LTspice. We will check how the circuit behaves in different conditions—measuring voltage, current, and power. By tweaking the MOSFET's size (channel width & length), we will observe how the performance changes, just like adjusting the size of a water pipe to control flow


**OVERVIEW**:A Common Source (CS) Amplifier is like a small megaphone for electrical signals.
It takes a weak signal and makes it stronger, just like a microphone boosts a quiet voice.
Used in audio systems, it helps transmit clear and loud sounds.
Radios and communication devices rely on it to strengthen signals.
Without it, many everyday electronics wouldn’t work as effectively!.



**COMPONENTS**:

- TSMC 180nm nmos-4
- Resistor (1K)
- Voltage source VDD = 1.8V
- Voltage source VGG = 0.9V

**CIRCUIT DIAGRAM**

![**CIRCUIT DIAGRAM**](https://github.com/srujanjainhn/LIC-LAB/blob/41348dee186eee422369f0f0c53d30a37656ee31/images/1.png)

 
 **PROCEDURE**:
 
 - Set up the circuit in the LTspice
 - From the spice director attach the library file 
 - Specify the values for the parameters as resistor (1K), VGG(0.9), VDD(1.8).
- For MOSFET choose model name- CMOSN, at first instance consider length=180nm and width=1um 
- Configure the analysis for *DC operating* point and observe the value of drain current ID and output voltage VDS
- By using the values of current verify that the mos is operating in the saturation region 
- Change the values of channel width and the lenght and observe the variation in the value of the current.
- Given the power budget as 50uW now we have **P=VDD x ID**, since VDD is fixed we get the value of ID 
- Now assume the suitable values for lenth and width such that the resulting current value should be almost nearer to the above calculated value.
---
### *TRANSIENT ANALYSIS*: - 
- set input voltage sine wave 1khz 50mv and dc offset value 0.9v 
- simulate-> transient, set stop time 5ms and run simulation 
### *AC analysis*
- set AC amplitude as 1v and configure for ac analysis tyoe of sweep- decade,no of points per decade-20, start frequency 0.1hz, stop frequency - 1T .
- from this obtain gain and bandwidth 


## **RESULTS**

**DC ANALYSIS**:


![**DC Analysis**](https://github.com/srujanjainhn/LIC-LAB/blob/8cb36b8edce8c55e7a91dcbcea7403ec368539fa/images/2.png)



**TRANSIENT ANALYSIS**

![**Transient Analysis**](https://github.com/srujanjainhn/LIC-LAB/blob/d389bac9b89a6a346d48e85acecaab7bdad2214f/images/4.png)




**FREQUENCY ANALYSIS**

![**ac  Analysis**](https://github.com/srujanjainhn/LIC-LAB/blob/242ceda5e8886cc2ab84fad5da4670e2812ba61f/images/3.png)




## INFERENCE 
MOSFET in Saturation: Since we are using the MOSFET as an amplifier, it must operate in the saturation region to function correctly. We ensure this by maintaining the right voltage conditions.

Effect of Width and Length on Current: Increasing the width of the MOSFET increases the current, while increasing the length decreases it. However, doubling the width doesn't exactly double the current due to channel length modulation, which slightly reduces the expected increase.

Power Calculation: The circuit consumes 50 µW of power, calculated using the formula P = I × V with the given values (Id = 27.08 µA, Vdd = 1.8V).

Circuit Stability:

Transient Response: The amplifier transitions smoothly over time, meaning it reacts well to changes in input signals.
AC Response: The circuit remains stable across different frequencies, proving its reliability in signal processing.
Gain & Phase Shift: The amplifier provides a 4 dB gain and an almost 180° phase shift, which matches theoretical expectations. This confirms that the circuit is working efficiently under AC conditions.






DESIGN-2

**AIM**: To obtain DC analysis and Transient analysis and AC analysis for the given circuit 

**COMPONENTS**
- Mosfet M1
 
- Mosfet M2
  
- Dc power supply

 **CIRCUIT DIAGRAM**
 ![**CIRCUIT DIAGRAM**](https://github.com/srujanjainhn/LIC-LAB/blob/0c6f26682a0c1e2967b3a705e3eddcc021bd3906/images/Screenshot%202025-02-17%20215921.png)
 ![**CIRCUIT DIAGRAM**]()
 

### **PMOS CONFIGURATION:**

- **Source:** Connected to supply (**1.8V**)  
- **Gate:** Connected to **0.9V**  
- **Drain:** Connected to NMOS drain.  

### **NMOS CONFIGURATION:**

- **Source:** Grounded.  
- **Gate:** Connected to **0.9V**.  
- **Drain:** Connected to PMOS drain.  

### **Chosen Transistor Dimensions:**

PMOS (W/L): 0.61μm / 180nm 

NMOS (W/L): 0.61μm / 180nm

## **DC Analysis**

Our approach in conducting DC analysis involves identifying the quiescent operating point (ID) and node voltages that are required to operate the MOSFET.

- **Supply Voltage (VDD)**: 1.8V  
- **Gate Voltage (VG)**: 0.9V  
- **Power Budget (P)**: 50μW  

P = VDD * ID

ID = P/VDD

ID = 50μW / 1.8V

ID = 27.7μA

![DC ANALYSIS](https://github.com/srujanjainhn/LIC-LAB/blob/d7bb35f27367ae95c2ed0fd0b2144d6a0f60b8dd/images/Screenshot%202025-02-17%20215901.png)



## **AC Analysis**

A sinusoidal input is included in the AC analysis through a modification of gate voltage.

**Sinusoidal Input Voltage**

- DC Offset: 0.9V  
- Amplitude: 50mV  
- Frequency: 1kHz

**Frequency Sweep Parameters**

- Type: Decade  
- Sweeps per Decade: 20  
- Start Frequency: 0.1Hz  
- Stop Frequency: 1THz  

By analyzing the AC, one can determine gain, bandwidth, phase, and other characteristics of the amplifier's frequency response.

![AC ANALYSIS](https://github.com/srujanjainhn/LIC-LAB/blob/e4b988a20519e4edff634803c124dffaf29c599b/images/Screenshot%202025-02-17%20220318.png)


## **Transient Analysis**

By examining the transient response of the amplifier, it is possible to determine its behavior over time when subjected to the sinusoidal input.

**Parameters**

- Stop Time: 5m (5 milliseconds)

The transient analysis provides information about the amplifier's time-domain behavior, such as distortion, settling time, and waveform reproduction.

![TRANSIENT ANALYSIS](https://github.com/srujanjainhn/LIC-LAB/blob/98b7459b869eec9f9cb8a5f61014aa693fa5a2a6/images/Screenshot%202025-02-17%20220129.png)


## **Inference**

**DC Analysis**

- The drain current (ID) required is approximately 27.78A, which should ensure the MOSFET operates correctly at its desired location.
- The conditions of biasing offer a reliable means of amplification.

**AC Analysis**

- The gain response and bandwidth can be analyzed using the AC sweep.
- The amplifier's performance across a broad frequency range, including its cutoff frequencies and phase behavior, will be taken into account when determining its suitability for various applications.

**Transient Analysis**

- The input waveform is accurately reproduced by the amplifier, as demonstrated.

  

