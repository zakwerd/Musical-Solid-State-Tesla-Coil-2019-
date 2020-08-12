# Musical Solid State Tesla Coil (2019)

## Overview  
This page details the design and build process of my first attempt at a musical solid state Tesla Coil. I will not only be outlining what I did but also the physics and reasoning behind my decisions; hopefully, resulting in a fairly comprehensive overview of how an SSTC is built. Along with my successes, I hope to clearly display my mistakes and their causes. I am currently working on a new SSTC (and eventually QCW DRSSTC), which you can soon find updates for on my github.

*Note: will try to update the math equations to display nicely in markdown instead of being in a text format*

## Theory
*Note: In order to fully explain the physics and electrical components behind an SSTC, I will go through the physics and components behind a standard spark-gap Tesla Coil. The “Design” section was placed after the “Theory” section to hopefully make the design explanations easier to understand.*

### A Basic Overview of the Physics of a Tesla Coil
A Tesla Coil is an inductor-capacitor (LC) resonant transformer. As a magnetic field is produced in one coil, an electrical current flows through the other. Coincidingly, as an electrical current flows through one coil, a magnetic field is induced. With the inclusion of a capacitor that charges and discharges, the induced magnetic field intensifies. For inductor-capacitor circuits, there is a “resonant frequency” that a current can oscillate through at. At the resonant frequency, the impedance, or electrical resistance, of the circuit is at a minimum, resulting in the greatest voltage build up between the end of the secondary to the air.  

The oscillation from an inductor-capacitor circuit inducing magnetic and electric fields occurs at a frequency. By approximating the oscillation of the flow of charge to occur with simple harmonic motion (e.g. q(t) = Asin(wt)), the frequency can be solved to equal f=1/2pi(root(LC)) where L is the inductance and C is the capacitance of the circuit. This frequency is the ideal or “resonant” frequency of the LC circuit. A resonant transformer works when the primary circuit matches the resonant frequency of the secondary coil (LC_primary=LC_secondary), causing both the primary and secondary LC circuits to be driven at the same resonant frequency.

### Spark Gap Tesla Coil Physics  
**Alternating Current (AC)**  
AC is current that switches directions many times per second (typically at 60 Hz in the US). AC has an advantage of DC (direct current) because its voltage can be altered with a transformer. Tesla Coils run on AC to transform a 120V input to an output voltage that’s hundreds of thousands of volts. The high potential difference that builds on the top of the toroid results in the electrical arcs through the air.

**Voltage Transformer**  
A transformer is a means of transferring electrical energy with two coils via a magnetic field. As AC current flows through the primary coil, an oscillating magnetic field is created and passes through the secondary coil, inducing an oscillating current through the secondary coil. The strength of the induced magnetic field and subsequently induced current is dependent on the change in magnetic flux and thus the number of turns in each coil. Voltage is proportional to current (P = IV), so by altering the number of turns, the output voltage can be changed. A transformer can be adjusted with the equation (Primary Turns/Secondary Turns) = (Primary Voltage/Secondary Voltage).

**Spark Gap**  
The spark gap controls the discharge frequency of the capacitors in the Tesla Coil. Current does not run through the spark gap at the resonant frequency. Instead, the spark gap allows for a quick pulse of current which then oscillates in the primary coil at the resonant frequency. A spark gap is simply an open space with two electrically conductive leads on either side. Increasing the width of the spark-gap makes it so a larger potential difference across the leads must be achieved for the capacitor to discharge and arc across. Thus, to arc through a wider gap, there must be more charge stored in the capacitors, which takes more time (Q=It).

### Steps of a Spark Gap Tesla Coil Circuit
1. An AC input is fed into a high voltage transformer, outputting a higher voltage than the input (red box in *Figure 1*).  
2. When totally uncharged, the capacitor acts as short circuit, causing the current to flow into the capacitor and charge it (blue box in *Figure 1*).  
3. As the capacitor charges, it builds a potential difference across its leads. When the potential difference becomes large enough, the capacitor can discharge by arcing across the spark gap and through the primary coil (orange arrows in *Figure 1*). The arrows have directionality, but the actual current is alternating directions through each cycle.  
4. The primary and secondary coils along with their capacitors (high voltage primary capacitor and air capacitor formed with the toroid) are driven at the secondary’s resonant frequency. Charge builds on top of the toroid and eventually discharges into the air, creating sparks.  

![shJ4l5NRJFMEGdNqGnOgjuA](https://user-images.githubusercontent.com/59108656/89960685-88b09b00-dbf4-11ea-874f-4346856ebe1c.png)  
*Figure 1. Basic spark-gap Tesla Coil circuit diagram consisting of an AC input, voltage transformer, spark gap, capacitor, primary coil, and secondary coil.*

### Solid State Tesla Coil Basic Overview  
A SSTC is the same as a spark-gap Tesla Coil, but the spark-gap is replaced with an IC to control the pulse frequency and width (“on-time”) of the capacitor discharges through the primary. The IC circuit controls the gates of high-power transistors; thus, controlling the discharge frequency of the main capacitor(s).

### Musical SSTC Main Components and Physics (Continuation of Spark Gap Description)  
**How Music is Made**  
A clap produces a single, quick note. A clap’s sound has an “on-time” (the duration that the sound is emitting) that is only a fraction of a second. The “on-time” of a clap can’t be changed, but the frequency can. By clapping at an increasing rate, the spacing between the “on-times” shrinks, increasing the pulse width percentage (the on-time percentage of each on and off cycle) and frequency of the clapping (demonstrated by the change between *Figure 2* and *Figure 3*). At a certain point, clapping at a high enough frequency will sound like a constant tone (e.g. when a large audience claps its perceived as a constant noise instead of hundreds of individual, distinct clap sounds). By increasing the capping frequency beyond this point, the constant tone will get higher in pitch. This is how the sparks can produce musical sounds. Each spark is a clap in this analogy. At a high enough frequency (100+ Hz), sparks will sound like a constant loud note, and by increasing the frequency, the note can change. Thus, by controlling just the frequency of the spark output (and keeping the pulse width constant as in the clapping example), music can be made.

![IMG_0890](https://user-images.githubusercontent.com/59108656/89960908-1c826700-dbf5-11ea-93e0-c2ba509760c5.jpg)  
*Figure 2. Example of the sound outputs of five equally spaced claps in which a clap has roughly an “on-time” of 2 milliseconds. Each clap is producing a sound during the rectangular peaks, and there is silence elsewhere.*

![IMG_0891](https://user-images.githubusercontent.com/59108656/89960944-34f28180-dbf5-11ea-8428-235b31439342.jpg)
*Figure 3. Example of the sound outputs of claps as the frequency increases. Note that the on-time is the same as in Figure 2, but the on-time percentage of each cycle has increased along with the frequency. This sequence of claps would sound higher pitched than the sequence in Figure 2.*

**Inverter (In Replacement of Spark Gap)**  
An inverter (purple box on Figure 7) uses transistors (typically MOSFETs or IGBTs) and large capacitors to produce an AC square wave across the primary coil at the coil’s resonant frequency. In electronics, an “inverter” is something that converts DC to AC. When the AC charges the polarized capacitors, the current will then release in one direction (now DC). The DC is then taken through half-bridge “inverter” circuit, which uses transistors and diodes to alternate the direction in which the capacitors’ discharged current flows (now back to AC - circuit walkthrough below for further explanation).  

For the transistors used, IGBTs (insulated gate bipolar transistors) have a voltage drop that increases with the log of the current flowing through (which approximates to a power loss of IV). MOSFETs act as resistors, having a power dissipation of I^2R, meaning there is a greater power loss than IGBTs. MOSFETs have the advantage of being able to switch on and off quicker and with a lower gate current, but they tend to be more expensive. For the prototype SSTC, IGBTs found onhand (Fairchild G30N60) are being implemented. The transistors used must be capable of switching on and off at the resonant frequency of the coil. The IGBTs implemented are rated for up to 222kHz, but can be pushed slightly above this frequency. For this reason, the prototype coil build (see current progress section) was designed to have a resonant frequency around 250kHz. For future builds that run at high resonant frequencies (400kHz+), MOSFETS will be used instead.  

Free-wheeling diodes are added in front of the gate of the IGBTs. These reduce flyback, a sudden voltage spike across an inductive load when voltage suddenly changes. 

High-power diodes are added in series with the capacitors. These diodes force the capacitors to discharge in specific directions, allowing for the DC to be converted to AC (see walkthrough below).

Unipolar capacitors convert the AC input into DC before later being inverted back to AC through the primary coil. The capacitors store the large amounts of charge that run through the primary coil powering the secondary coil.

High resistance (100k-ohms+) resistors are added in parallel with the bus capacitor(s) to act as bleeder resistors: if the capacitors are still charged after use, the bleeder resistors will safely dissipate the remaining charge.

**Feedback System (In Replacement of Spark Gap)**  
The feedback system picks up a signal from the current oscillating in the secondary (this is at the resonant frequency) and send it to the gate drive chips to open and close the transistors accordingly. This also allows SSTCs to be self tuning: if the environment changes, altering the resonant frequency of the secondary, the feedback system will pick up the new resonant frequency and adjust the switch time of the gate driver.  

Feedback is typically done with a current, feedback transformer or an antenna. The transformer feedback uses the ground end of the secondary in a toroidal transformer to pick up the frequency it is running at which feeds into the input signal pins of the drive chips. Similarly, the antenna picks up the sinusoidal current through the secondary and delivers it to the drive chips. The antenna method tends to be simpler (it is essentially just a wire), but the drive transformer is more compact and reliable. In the current SSTC build, both methods are being experimented with, but a feedback transformer will be used for the final version. 

**Gate Driver (In Replacement of Spark Gap)**  
This amplifies signals from the feedback system and sends them to the transistors of the inverter to open and close the gates at the correct frequency. The most common SSTC gate driver uses the UCC27321 and UCC27322 MOSFET drive chips together, outputting a 12V, 9A signal to the gate of the transistors of the inverter. A transformer is commonly added to the output of the drive chips to increase the voltage, ensuring that the gates of the transistors are fully triggered.

**Interrupter (In Replacement of Spark Gap, Allows for Music)**  
A small controller to turn the gate driver on and off, allowing the duty cycle of the SSTC to be adjustable (controls pulse width - inverter on-time - and frequency). This is typically done with either a 555 chip with a potentiometer to control the duty cycle or an IC (like an ATtiny or Arduino IC) with a potentiometer to control the duty cycle. By controlling the gate driver, the interrupter also prevents high currents from constantly running through the transistors in the inverter circuit and breaking them (this becomes more important for DRSSTCs and QCW DRSSTCs when there are much higher currents running through the circuit). The gate driver on and off time is different than the output pulses from the gate driver. The gate driver may be switching the inverter transistors at 250kHz while the interrupter switches the gate driver at a rate of 200Hz. 

![sh-MA_WHMdrhCl8SJhayR9A](https://user-images.githubusercontent.com/59108656/89961382-61f36400-dbf6-11ea-9a82-47af016b03c1.png)  
*Figure 4. Example output signal from the inverter that is sent to the transistors (around 166kHz). The signal enclosed in the red box is the same signal enclosed in the red box on Figure 5. The sharp peaks before flattening out are due to the 555 chip circuit not producing a perfect square wave.*  


![sn4ZrEeJ0I2JhYpbMhebWIw](https://user-images.githubusercontent.com/59108656/89961383-63249100-dbf6-11ea-88ea-c975fd43178c.png)  
*Figure 5. Example of an interrupter switching the inverter on and off at a frequency of 100Hz. The red box represents what is displayed in the red box in Figure 4.*  

**Inverter (In Replacement of Spark Gap)**  
An inverter uses transistors (typically MOSFETs or IGBTs) and large capacitors to produce an AC square wave across the primary coil at the coil’s resonant frequency. In electronics, an “inverter” is something that converts DC to AC. When the AC charges the polarized capacitors, the current will then release in one direction (now DC). The DC is then taken through half-bridge “inverter” circuit, which uses transistors and diodes to alternate the direction in which the capacitors’ discharged current flows (now back to AC - circuit walkthrough below for further explanation).  

For the transistors used, IGBTs (insulated gate bipolar transistors) have a voltage drop that increases with the log of the current flowing through (which approximates to a power loss of IV). MOSFETs act as resistors, having a power dissipation of I2R, meaning there is a greater power loss than IGBTs. MOSFETs have the advantage of being able to switch on and off quicker and with a lower gate current, but they tend to be more expensive. For the prototype SSTC, IGBTs found onhand (Fairchild G30N60) are being implemented. The transistors used must be capable of switching on and off at the resonant frequency of the coil. The IGBTs implemented are rated for up to 222kHz, but can be pushed slightly above this frequency. For this reason, the prototype coil build (see current progress section) was designed to have a resonant frequency around 250kHz. For future builds that run at high resonant frequencies (400kHz+), MOSFETS will be used instead.  

Free-wheeling diodes are added in front of the gate of the IGBTs. These reduce flyback, a sudden voltage spike across an inductive load when voltage suddenly changes.   

High-power diodes are added in series with the capacitors. These diodes force the capacitors to discharge in specific directions, allowing for the DC to be converted to AC (see walkthrough below).  

Unipolar capacitors convert the AC input into DC before later being inverted back to AC through the primary coil. The capacitors store the large amounts of charge that run through the primary coil powering the secondary coil.  

High resistance (100k-ohms+) resistors are added in parallel with the bus capacitor(s) to act as bleeder resistors: if the capacitors are still charged after use, the bleeder resistors will safely dissipate the remaining charge.  




## Credits
Thank you to [LoneOceans](https://www.loneoceans.com/labs/) for giving me the foundation of all I know about Tesla Coils.  
Thank you to [Steve Ward](https://www.stevehv.4hv.org/SSTCindex.htm) for providing an abundance of knowledge regarding Tesla Coils and for revolutionizing Tesla Coil technology.  
Thank you to Dr. James Dann (my Advanced Science Research teacher) for always believing in me and always being willing to help.
