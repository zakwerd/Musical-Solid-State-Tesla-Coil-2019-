# Musical Solid State Tesla Coil (2019)

## Overview  
This page details the design and build process of my first attempt at a musical solid state Tesla Coil. I will not only be outlining what I did but also the physics and reasoning behind my decisions. Hopefully, this will result in a fairly comprehensive overview of how an SSTC is built. Most of the first part of this paper will go into how SSTCs and Tesla Coils work, so if you just want to skip to my build, you can begin at *Figure 7.* Along with my successes, I hope to clearly display my mistakes and their causes. I am currently working on a new SSTC (and eventually QCW DRSSTC), which you can soon find updates for on my github.

I have included a credits section at the bottom, but I would like to acknowledge Gao Guangyan from LoneOceans Labs here as well. Gao has not only provided some of the most comprehensive overviews of how Tesla Coils are built and the physics behind them, but he also responded to some hyper-specific questions I emailed him regarding my circuit. I attribute a majority of what I've learned about Tesla Coils to Gao, so he deserves a monumental amount of credit for helping me achieve my accomplishments (both past and future) regarding Tesla Coils.

If you notice any errors regarding grammar, formatting, or explanations, please notify me! I appreciate your help!

*Note: will try to update the math equations to display nicely in markdown instead of being in a text format*

![thumbnail_IMG_2164](https://user-images.githubusercontent.com/59108656/90054606-f14d5580-dc90-11ea-87a2-eade87794c16.jpg)  
*Figure 8. My final coil build being displayed at our school's Maker Faire. Next to me is Ethan Zhang, displaying his crazy awesome coil gun.* 

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
An inverter uses transistors (typically MOSFETs or IGBTs) and large capacitors to produce an AC square wave across the primary coil at the coil’s resonant frequency. In electronics, an “inverter” is something that converts DC to AC. When the AC charges the polarized capacitors, the current will then release in one direction (now DC). The DC is then taken through half-bridge “inverter” circuit, which uses transistors and diodes to alternate the direction in which the capacitors’ discharged current flows (now back to AC - circuit walkthrough below for further explanation).  

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

The Tesla Coil sparks are produced due to the inverter signal sent at the resonant frequency (Figure 4). However, the frequency that sparks are produced and the “on-time” of the sparks can be adjusted with the interrupter (Figure 5). Thus, by controlling the on-time and frequency of the sparks, the interrupter has control over the sound the sparks create. Because of this, the interrupter can be programmed to switch the inverter on and off at a specific sequence of frequencies and pulse durations. This would result in a sequence of tones. To produce a song, each musical note needs to be correlated with a frequency and pulse width, which is then created by the interrupter and sent to the inverter. The musical interrupter will thus be made by programming an Arduino to output a 5V square wave with a frequency and pulse width dependent on a MIDI input from the keyboard.

![swo-4kIDKUovcsPdngQvr3w](https://user-images.githubusercontent.com/59108656/90052493-0ffe1d00-dc8e-11ea-8182-011ea865c8f4.png)  
*Figure 6. All rights to this image and intellectual property belong to LoneOceans Labs (see credits below). Example SSTC Circuit Diagram. Note that the gate drive transformer (right of orange box) is set up improperly. In the diagram, the transformer output would open and close the gates of the IGBTs simultaneously whereas they should be triggered as opposites (one on one off). The fix to this is changing the labeled winding direction of one of the transformer outputs.

**SSTC - Overview of the Circuit Process**
*Note: There are many variations of an SSTC in which this process, especially in regards to the inverter, will vary. This is a very general description of how the main components of an SSTC will work. Look to the circuit diagram on Figure 6 above for visual reference*  
1. A separate circuit is made to transform the 120VAC wall output into 5V and 12V outputs to power the ICs (red box on Figure 6).  
2. The interrupter (green box on Figure 6) outputs a square-wave signal with adjustable pulse-width and frequency. The signal is sent to the gate driver (orange box on Figure 6) to turn it on and off. When the driver chips are enabled, the hex inverter in the feedback system will send a short pulse allowing the oscillation to begin.  
3. The gate driver amplifies the feedback signal’s current and sends it to the inverter.  
4. Following along with the pink box on Figure 6: 120VAC feeds into the two capacitors. The gate driver’s signal will trigger the top IGBT (arbitrarily chosen for this example) and leave the bottom IGBT off. Top capacitor will be unable to discharge. With the top IGBT open, the bottom capacitor can discharge through both diodes, through the top IGBT, and across the primary coil (red arrows in Figure 6 display the flow of current when capacitor discharges). When this ends, the IGBTs switch being on and off, discharging the other capacitor through the coil as the other recharges.  

## Design

### Circuit Diagram  
![SSTC 1 0 Circuit_schem](https://user-images.githubusercontent.com/59108656/90052023-6d459e80-dc8d-11ea-956c-d77f54b3a51b.png)  
*Figure 7. My circuit Diagram of current SSTC build. Includes a 555 controlled interrupter instead of a MIDI circuit for simplicity. Excludes a feedback system in replacement for a 555 chip controlled feedback system that outputs a signal at the resonant frequency. 

### My Design/Circuit Decisions and Their Reasoning  
**IGBTs and Coils**  
To achieve a compact build, a resonant frequency between 200kHz and 300kHz would have to be used. IGBTs have less power loss than MOSFETs, but switch at a lower max speed. The IGBTs being used (Fairchild G30N60) are rated for switch speeds up to 222kHz, so the build was designed to have a resonant frequency at around the same value. There are many different combinations of primary and secondary wire gauges in conjunction with winding heights and radii that could have resulted in the final resonant frequency used (250 kHz). Therefore, the height and radii of the coil were chosen purely for aesthetic purposes, and the gauges of the coils’ wires were chosen to match the needed resonant frequency.  

**Capacitors**  
The capacitors being used were selected based on what capacitors were available in the Whitaker lab and what capacitors were typically used for compact musical Tesla Coils. In short, there is no “perfect capacitor” for a musical Tesla Coil. Testing has revealed that the capacitors currently being used may not be able to charge and discharge quickly enough. If true, special capacitors with faster switch speeds will need to be used instead.

**No Feedback System**  
The feedback system sends a signal that tells the IGBTs what frequency to trigger at, which gets the coil running. However, to test the feedback system, the coil has to already running in the first place. To work around this, a 555 chip circuit that creates a square wave at 250kHz (just around the resonant frequency) was made to act like the feedback circuit. The feedback circuit is still being tested with and has yet to work. Once the feedback circuit works, it will replace the 555 chip controlled circuit.

![thumbnail_IMG_2164](https://user-images.githubusercontent.com/59108656/90054606-f14d5580-dc90-11ea-87a2-eade87794c16.jpg)  
*Figure 8. My final coil build being displayed at our school's Maker Faire. Next to me is Ethan Zhang, displaying his crazy awesome coil gun.*  

## Results, My Mistakes, What I Learned, and Concluding Thoughts  
The final build was only able to produce tones within a two to three octave range, and then it would abruptly go silent. I haven't done much research regarding this issue, so it is entirely possible that there are audible frequencies that coils just can't produce all that well. I think it is more likely that my inverter and gate drive system weren't perfectly optimized. This is based on the fact that the sparks were smaller than expected (at their best, they were around two inches in length).

There were many mistakes throughout this engineering endeavor. Firstly, the entire build clearly was not optimized. Secondly, the feedback system didn't seem to make any noticable difference. There were many other minor circuitry errors (like the gate drive resistor values being slightly off, possibly creating a significant performance hindrance in the gate driver). Most of my mistakes originated simply from a lack of rigorous understanding of the operation of Tesla Coils. As I try to recreate this build, I will dedicate significantly more time towards fully understanding all of the physics nuances regarding Tesla Coils before I touch a soldering iron. This step is crucial for endeavoring to build more advanced coils, like QCWs, in which there is hardly any build information available online.

After this project, I learned a significant amount of Electrical Engineering knowledge and skills. For that reason, despite the coil not working to my expectations, I am incredibly happy with the results.

If you have made it this far, I hope you enjoyed my paper.

## Credits
Thank you to [LoneOceans](https://www.loneoceans.com/labs/) for giving me the foundation of all I know about Tesla Coils.  
Thank you to [Steve Ward](https://www.stevehv.4hv.org/SSTCindex.htm) for providing an abundance of knowledge regarding Tesla Coils and for revolutionizing Tesla Coil technology.  
Thank you to Dr. James Dann (my Advanced Science Research teacher) for always believing in me and always being willing to help.
