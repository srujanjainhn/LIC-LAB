 EXPERIMENT 1: CS Amplifier 

**AIM**: To simulate the CS amplifier circuit of the MOSFET in the LTspice and obtain DC analysis, AC analysis, transient analysis and determining DC operating point, gain, bandwidth, power also observing the variations of current by varying width and length of the channel.



**OVERVIEW**:A Common Source (CS) Amplifier is a widely used circuit in analog electronics, employing a **MOSFET** for signal amplification. It features a common source, producing a high voltage gain with a 180° phase shift between input and output. The amplifier’s performance is analyzed through DC analysis (t#o determine the biasing point), AC analysis (to study gain and frequency response), and transient analysis (to observe signal behavior over time). Due to its efficient signal amplification, it is commonly found in audio processing, RF applications, and integrated circuits.



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
### *Transient analysis*: - 
- set input voltage sine wave 1khz 50mv and dc offset value 0.9v 
- simulate-> transient, set stop time 5ms and run simulation 
### *AC analysis*
- set AC amplitude as 1v and configure for ac analysis tyoe of sweep- decade,no of points per decade-20, start frequency 0.1hz, stop frequency - 1T .
- from this obtain gain and bandwidth 


## **Results**

**DC analysis**:


![**DC Analysis**](https://github.com/srujanjainhn/LIC-LAB/blob/8cb36b8edce8c55e7a91dcbcea7403ec368539fa/images/2.png)



**transient analysis**

![**Transient Analysis**]()




**frequency analysis**

![**ac  Analysis**](https://github.com/srujanjainhn/LIC-LAB/blob/242ceda5e8886cc2ab84fad5da4670e2812ba61f/images/3.png)




## INFERENCE 
