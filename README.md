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

## Credits
Thank you to [LoneOceans](https://www.loneoceans.com/labs/) for giving me the foundation of all I know about Tesla Coils.  
Thank you to [Steve Ward](https://www.stevehv.4hv.org/SSTCindex.htm) for providing an abundance of knowledge regarding Tesla Coils and for revolutionizing Tesla Coil technology.  
Thank you to Dr. James Dann (my Advanced Science Research teacher) for always believing in me and always being willing to help.
