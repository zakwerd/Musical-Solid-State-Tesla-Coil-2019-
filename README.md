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








## Credits
Thank you to [LoneOceans](https://www.loneoceans.com/labs/) for giving me the foundation of all I know about Tesla Coils.  
Thank you to [Steve Ward](https://www.stevehv.4hv.org/SSTCindex.htm) for providing an abundance of knowledge regarding Tesla Coils and for revolutionizing Tesla Coil technology.  
Thank you to Dr. James Dann (my Advanced Science Research teacher) for always believing in me and always being willing to help.
