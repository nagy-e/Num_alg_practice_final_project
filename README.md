# Num_alg_practice
Semester 3 numerical algorithm project

Project Title: Non-Linear RLC Circuit

Name: Eszter Nagy (CSNXNB) & Erik Balogh (VA5SWG)




    Goal:

To introduce the physical difference between a linear and a non-linear RLC circuit.
To compare two difference algorithms ODEs solvers (Euler method and Runge-Kutte 4th Order method) and see which one is more accurate to handle the characteristics of a chaotic system.




    Description:

The project starts with the introduction of a normal, linear RLC electronic circuit, and then replace the capacitor with a non-linear component, a varactor diode.

The behaviour of a standard RLC circuit can be decribed by a second order linear ordinary differential equation:
(1): L*(d^2q)/(dt^2) + R(dq/dt)+ 1/C*q = V(t), 
where L is the inductance factor of the coil, R is the resistance of the resistor, C is the capacitance of the capacitor. V(t) is the time dependent input voltage, we will consider a sinusoidal input voltage. 

By defining current as I=dq/dt, we can convert this into a system of two first-order ODEs, to be able to calculate the capacitor voltage and inductor current over time.
One equation is simply: (2): I= dq/dt => the first derivative of the charge is the current
The other equation using the original equation and substituting the I=dq/dt relation into it: 
L*(dI/dt) + R*I + 1/C*q = V(t) = Vo*cos(ωt) => The first derivative of the current is: (3): dI/dt = 1/L * (V(t) - RI- 1/C q)
The phyton loop will track 2 variables q & I.


The non-linear RLC circuit can be set up changing the linear component capacitor with a non-linear component. In our system this non-linear characteristic is caused by a varactor diode.
In this case the voltage drop at the diode is not simply V = q/C, but (4): V = aq + bq^3
Substituting it into the original equation (1): 
(5): L*(d^2q)/(dt^2) + R(dq/dt)+ aq + bq^3 = V(t) = Vo*cos(ωt)
Again we split it into 2 first order ODEs:
I= dq/dt
(6): dI/dt = 1/L*(Vo*cos⁡(ωt)-RI-aq-bq^3)
The parameters will be defined in the beginning.

With Fourier transform the data are transformed from time domain into frequency domain to plot the frequency spectrum.
With another root-finding method the location of the frequency jump points will be determined.




    Plots:

Linear RLC:
The current in the function of time for both Euler and RK4 methods to see the simulation error.

Non-linear RLC:
Phase Space: Current against the charge to visualize the chaotic dynamics.
Amplitude against frequency (using Fourier Transformation) to show the multiple harmonic frequency peaks. The Liner RLC circuit has only one resonance frequency.
The peak amplitude against the driving frequency(ω) to see the exact resonance curve and to show the discontinuous amplitude jumps.




    Libraries:
So far the following libraries are going to be used:
numpy
spicy
matplotlib