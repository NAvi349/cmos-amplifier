![image](https://user-images.githubusercontent.com/66086031/189542813-db7a009d-3f68-4366-8322-7e83cc3e1284.png)


# Motivation and Aim
To design an amplifier that does not contain any biasing resistors and bypass capacitors.

# Biasing Resistors and Capacitors
NMOS amplifier contains resistors and bypass capacitors. We cannot use them on integrated circuits as they occupy a large area relative to that of a transistor.

# Topologies needed
We need six important concepts or topologies to build such an amplifier:
- Dual power supply
- Differential pair
- Current source biasing
- Current source load
- Current mirror
- Cascoding of transistors

## Dual power supply
**Aim:** To remove voltage-divider network and capacitors at the input

**Approach:** Voltage divider at the input is provided such that the Gate is at higher potential than the source. But the biasing resistors and hence the input-coupling capacitors are a problem.

**Solution:** We can provide a negative power supply VSS also. Now the Source is at a lower potential than Gate. We use a source resistor to establish the bias current. Similar to emitter bias configuration of BJT.

Bias current:  I_SS  =((- V_GS- V_ss))/R_D     where VSS = -VDD

## Differential pair
Purpose: To remove source bypass capacitor at the source.

Approach: We need a device that provides low-impedance path to ac.

Solution: Looking towards the source terminal we see a small-signal impedance of  1/gm  . So we couple two NMOS at the source terminal.

## Current source biasing
Purpose: To remove bias resistor RS at the source.

Approach: Using resistor biasing at the source reduces gain due to negative feedback.

Solution: We can replace the bias resistor directly by a current source ISS. It does not affect the small-signal gain. The current source is a NMOS biased in saturation.

## Current source load

Purpose: To remove load resistor RD.

Approach: Output Gain = -〖 g〗_m*R_D . RD is used to provide gain but also provides a voltage drop. Reduction is the positive swing. Saturation condition: V_GS- V_DS≤ V_TH
Using RD ¬limits the positive swing of the output ac-signal. We need a device which provides large impedance to ac but does not limit the positive swing.

Solution: Looking towards the drain-terminal we can see a small-signal impedance rO due to channel-length modulation.  r_o=1/(λ *〖 I〗_D )  This is very large.
So we can use a common-source PMOS (acting as a current source) as a load element. 
Now gain = -〖 g〗_m* r_o

## Current Mirror

Purpose: To copy a highly stable reference current into other circuits.

Approach: We need a highly stable current source that has a high resistance to DC voltage distortions. 

Solution: A reference current is established by using a band-gap reference circuit or by a MOSFET in saturation. We then pass this reference current through a diode-connected 
MOSFET (Gate and Drain terminal shorted together). Now the VGS given by


This VGS is given as input to another MOSFET. Since both have same gate-source voltage they have the same Drain Current. This current mirror is used to implement the current-source as a load and current-source as a bias element.
The output current is given by 

## Cascoding of transistors

Purpose: To increase the stability against supply distortions and to increase the impedance of a current-source load.

Approach: A single MOSFET acting as a current source does not provide much stability and output impedance.

Solution: We can stack transistors on top of another to increase the output impedance. The output impedance is = ro1 * gm1 * ro2. Gain also increased if it is used as a load.

# CMOS Differential Amplifier
We can now apply the topologies we studied to design an NMOS Differential Amplifier without resistors and capacitors.
1 – Reference current: This is used to establish the reference current. It is cascode structure so the stability of current source is increased.
2 – Cascode Current Mirror Circuit: This is used to establish the bias current or the drain current of the differential pair. It gives large output resistance
3 – Active load: This topology uses PMOS current mirror as the active load.

# Result
Thus an amplifier suitable for implementation in an integrated circuit is designed.

# References
-Images taken from Razavi and Donald. A Neamen Books
