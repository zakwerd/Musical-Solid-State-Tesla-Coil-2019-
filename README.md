# Musical Solid State Tesla Coil (2019)

## Overview  
This page details the design and build process of my first attempt at a musical solid state Tesla Coil. I will not only be outlining what I did but also the physics and reasoning behind my decisions; hopefully, resulting in a fairly comprehensive overview of how an SSTC is built. Along with my successes, I hope to clearly display my mistakes and their causes. I am currently working on a new SSTC (and eventually QCW DRSSTC), which you can soon find updates for on my github.

## Theory
*Note: In order to fully explain the physics and electrical components behind an SSTC, I will go through the physics and components behind a standard spark-gap Tesla Coil. The “Design” section was placed after the “Theory” section to hopefully make the design explanations easier to understand.*

### A Basic Overview of the Physics of a Tesla Coil
A Tesla Coil is an inductor-capacitor (LC) resonant transformer. As a magnetic field is produced in one coil, an electrical current flows through the other. Coincidingly, as an electrical current flows through one coil, a magnetic field is induced. With the inclusion of a capacitor that charges and discharges, the induced magnetic field intensifies. For inductor-capacitor circuits, there is a “resonant frequency” that a current can oscillate through at. At the resonant frequency, the impedance, or electrical resistance, of the circuit is at a minimum, resulting in the greatest voltage build up between the end of the secondary to the air.  

The oscillation from an inductor-capacitor circuit inducing magnetic and electric fields occurs at a frequency. By approximating the oscillation of the flow of charge to occur with simple harmonic motion (e.g. q(t) = Asin(wt)), the frequency can be solved to equal f=1/2pi(root(LC)) where L is the inductance and C is the capacitance of the circuit. This frequency is the ideal or “resonant” frequency of the LC circuit. A resonant transformer works when the primary circuit matches the resonant frequency of the secondary coil (LC_primary=LC_secondary), causing both the primary and secondary LC circuits to be driven at the same resonant frequency.
