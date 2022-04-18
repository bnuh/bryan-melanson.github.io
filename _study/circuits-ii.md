---
layout: study_guide
title: 'Electronic Circuits II'
caption: Memorial University ENG5854
description: > 
date: '14-04-2022'
---

* this unordered seed list will be replaced by the toc
{:toc}

## Operational Amplifiers

An *Operation Amplifier* is a device which, when powered by $$+V$$ and $$-V$$ DC power sources, will amplify an input signal with infinite gain. The input terminals are known as the *non-inverting* ($$+$$) and *inverting* ($$-$$) terminals.

Where no input current enters $$+$$ and $$-$$, and the *input impedance is infinite*.

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/op.png">
</p>

Ideal Op Amp
{:.figcaption}

$$A$$ is referred to as the **Open Loop Gain**, where the output and inputs have not been connected. The **Closed Loop Gain** will be denoted as $$G$$.

The **Differential Input Signal** $$v_{id}$$ and **Common Mode Input Signal** $$v_{Icm}$$ are two signals that define the operation of the op-amp. Because the op-amp is designed to detect the difference between two signals, they are denoted as the term $$v_id$$. The op-amp will also reject common signals, because only the difference between the two signals will be used for output.

$$v_{id} = v_2 + v_1$$

$$v_{Icm} = \frac{1}{2}(v_1 + v_2)$$

### Inverting Configuration

In the inverting configuration, the output of the op-amp is connected back into the inverting terminal. Because in the inverting configuration $$v_2$$ is grounded, the negative output counteracts the inifite gain and *closes the loop* around the op amp so that it provides a stable output.

In the case where a resistance is placed between $$v_2$$ and $$v_o$$, there would be a **Positive Feedback**, and the output would increase exponentially.

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/invert.png">
</p>

Inverting Configuration of Op Amp
{:.figcaption}

$$v_3 = A(v_2-v_1)$$

If $$v_2 = v_1$$, the output will be $$0$$. Where $$A$$ is infinite,

$$\frac{v_3}{A} = v_2-v_1$$

$$0 = v_2-v_1$$

$$v_2 = v_1$$

This is known as a *Virtual Short Circuit*.

The **Closed Loop Gain** $$G$$ is defined as $$\frac{v_o}{v_i}$$

From Figure 1, we can see that knowing $$v_1 = v_2 = 0$$, therefore $$i_1$$ can be calculated, and passes to the input without entering the op amp terminals.

$$G = \frac{v_0}{v_i} = -\frac{R_2}{R_1}$$

Closed Loop Gain of a Non-Inverting Amplifier
{:.figcaption}

#### Finite Open-Loop Gain

When the open-loop gain $$A$$ is not finite, $$\frac{v_3}{A} = v_2-v_1$$ no longer produces $$v_2 = v_1 = 0$$, instead $$v_2 = v_1 = \frac{v_o}{A}$$. Knowing this, calculations for $$i_1$$ will follow the same logic, instead with accounting for $$\frac{v_0}{A}$$.

#### Input and Output Resistance

The input resistance is equal to $$R_1$$, and the output resistance is $$0$$.

#### Weighted Summer

In this configuration, $$i$$ will be the sum of all incoming currents. Therefore,

$$i = \frac{v_1}{R_1} + \frac{v_2}{R_2} + ...$$

In the case where a design must be created to fit an equation with multiple inverted signs, two op-amps can used in series to flip the initial signals.

$$v_o = v_1(\frac{R_a}{R_1})(\frac{R_c}{R_b}) + v_2(\frac{R_a}{R_2})(\frac{R_c}{R_b}) - v_3(\frac{R_c}{R_3}) - v_4(\frac{R_c}{R_4})$$

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/summer-2.png">
</p>

Weighted Summers in Series
{:.figcaption}

### Non-Inverting Configuration

The Non-inverting configuration occurs when a voltage input enters the $$v_2$$ terminal, instead of $$v_1$$, while the resistor loop configuration is identical. As with the other closed loop, there is a virtual short circuit between $$v_2$$ and $$v_1$$, therefore $$v_2 = v_1 = v_I$$, the applied voltage.

The $$v_1$$ terminal, grounded in this case, creates $$i_1 = \frac{v_I}{R_1}$$, and the solution can follow as before.

$$G = \frac{v_0}{v_i} = 1 + \frac{R_2}{R_1}$$

Closed Loop Gain of a Non-Inverting Amplifier
{:.figcaption}

#### Finite Open-Loop Gain

When the open-loop gain $$A$$ is not finite, $$\frac{v_3}{A} = v_2-v_1$$ no longer produces $$v_2 = v_1 = 0$$, instead $$v_2 = v_1 = \frac{v_o}{A}$$. Knowing this, calculations for $$i_1$$ will follow the same logic, instead with accounting for $$\frac{v_0}{A}$$.

#### Buffering Amplifier or Voltage Follower

In this configuration, the loop is closed by short circuiting the output to non-inverting input. This will again create a virtual short circuit between $$v_2$$ and $$v_1$$, and because a real short circuit exists between $$v_1$$ and $$v_o$$, all terminal values will be equal to the voltage source, $$v_I$$.

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/buff.png">
</p>

Buffer Amplifier or Voltage Follower
{:.figcaption}

### Difference Amplifiers

A Difference Amplifier is one where voltage sources are applied to the $$v_2$$ and $$v_1$$ inputs. The output can then be considered a non-inverting configuration and an inverting configuration superimposed on each other. By using supoerposition, the effect of each voltage source can then be calculated separately and summed together independent of one another.

In a case like this, $$v_o = A_dv_{id} + A_{cm}v_{Icm}$$, and the efficiency of the Difference Amplifier can be determined by its *common-mode rejection ratio (CMRR)*

$$\text{CMRR} = 20 \text{log}\frac{|A_d|}{|A_{cm}|}$$

Common Mode Rejection Ratio
{:.figcaption}

In a Difference amplifier with voltage sources at $$v_2$$ and $$v_1$$, it can be seen that this will have a inverting and non-inverting output superimposed on one another. However, the gain ratio of both inputs must be equal for the common mode ratio rejection, so the $$v_2$$ input must use a voltage divider ($$v_3$$ and $$v_4$$) to reduce the input voltage.

Therefore, $$\frac{R_4}{R_4 + R_3}(1 + \frac{R2}{R1}) = \frac{R2}{R1}$$, and $$\frac{R4}{R3} = \frac{R2}{R1}$$.

To find values concering solely the $$v_{Id}$$ and $$v_{Icm}$$, consider a voltage source $$v_Id$$ or $$v_Icm$$ applied at the inputs, where $$v_Icm$$ is applied to both, and the negative and positve termals of $$v_{id}$$ are connected in series between the two terminals.

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/diff.png">
</p>

Difference Amplifier
{:.figcaption}

#### Instrumentation Bridge Amplifiers

The Instrumentation Bridge Amplifier is a Difference Amplifier created as a solution to the low input resistance of Difference Amplifiers, without sacrificing ease of control. From Figure 6, it can be noted that $$R_1$$ can be used to control the output voltage of the circuit.

$$v_o = \frac{R4}{R3}(1 + \frac{R_2}{R_1})v_{Id}$$

Output of the Instrumentation Bridge Amplifier
{:.figcaption}

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/instr.png">
</p>

## Filters and Tuned Amplifiers

A filter is a linear two-port network with a transfer function $$T(s) = V_o(s)/V_i(s)$$. For physical frequencies, the filter transmission is expressed as $$T(j\omega) = \mid{T}(j\omega)\mid{e^{j\phi(\omega)}}$$. The magnitude of transmission can be expressed in decibels using either the gain function $$G(\omega) = 20\text{log}\mid{T}\mid$$ or the attenuation function $$A(\omega) = −20 \text{log}\mid{T}\mid$$.

Note on Imaginary Numbers:

Magnitude = $$\sqrt{\Re^2 + \Im^2}$$

$$|\frac{\omega_0}{\omega_0+\omega j}| = \frac{\sqrt{\omega_0 ^2}}{\sqrt{\omega_0^2 + \omega^2}} = \frac{\omega_0 ^2}{\sqrt{\omega_0^2 + \omega^2}}$$

Phase = $$\text{tan}^{-1}(\Im / \Re)$$

$$\phi(\frac{\omega_0}{\omega_0+\omega j}) = \frac{\text{tan}^{-1}\frac{0}{\omega_0}}{\text{tan}^{-1}\frac{\omega}{\omega_0}}$$

### Filter Transmission

The transmission characteristics of a filter are specified in terms of the edges of the passband(s) $$\omega_p$$ and the stopband(s) $$\omega_s$$. The maximum allowed variation in passband transmission, $$A_{max}$$ (dB); and the minimum attenuation required in the stopband, $$A_{min}$$ (dB). In some applications, the phase characteristics are also specified.

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/transmission.png">
</p>

$$T(s) = \frac{a_1s + a_0}{s + \omega_0}$$

General First-Order Transfer Function
{:.figcaption}

The filter transfer function can be expressed as the ratio of two polynomials in $$s$$. The degree of the denominator polynomial, $$N$$, is the filter order. The $$N$$ roots of the denominator polynomial are the poles (natural modes).

### Filter Types

**High Pass** allows high frequencies to pass through (the *passband*) and attenuates frequences below (the *stopband*).

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/highpass2.png">
</p>

**Low Pass** allows low frequencies to pass through.

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/lowpass2.png">
</p>

**Band Pass** will pass all bands, but invert phase.

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/bandpass2.png">
</p>

**Band Stop** will stop all bands within the specified range.

In each case of attenuation, the slope will be -20 dB per decade.

The **All Pass Filter** is a special case which does not attenuate, but serves as a phase shifter, with a unity gain and phase shift at $$\omega_0$$.

### Filter Transmission (2nd Order Filters)

$$T(s) = \frac{a_2s^2 + a_1s + a_0}{s^2 + (\omega_0/Q)s + \omega_{0}^2}$$

General Second-Order Transfer Function
{:.figcaption}

### Filter Types

**High Pass** goes zero as the $$s$$ value goes to zero, and $$a_2$$ as $$s$$ goes to $$\infty$$.

$$T(s) = \frac{a_0}{s^2 + (\omega_0/Q)s + \omega_{0}^2}$$

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/highpass3.png">
</p>

**Low Pass** allows low frequencies to pass through.

$$T(s) = \frac{a_2s^2}{s^2 + (\omega_0/Q)s + \omega_{0}^2}$$

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/lowpass3.png">
</p>

**Band Pass** will attenuate all but the $$\omega_0$$ frequency.

$$T(s) = \frac{a_1s}{s^2 + (\omega_0/Q)s + \omega_{0}^2}$$

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/bandpass3.png">
</p>

**Notch** will attenutate at the center frequency $$\omega_0$$.

$$T(s) = a_2\frac{s^2+\omega_{0}^2}{s^2 + (\omega_0/Q)s + \omega_{0}^2}$$

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/notch.png">
</p>

$$Q = 1/\sqrt{2} = $$The Butterworth Maximally Flat Response

$$\text{BW} = \omega_2 - \omega_1 = \omega_0/Q$$

### Second Order LCR Resonator

Resonators are used to realize second order filters.

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/resonator.png">
</p>

For a current applied to this circuit,

$$v_0 = I \cdot \frac{1}{Y}$$
    
$$\frac{1}{Y} = \frac{1}{\frac{1}{SL} + Cs + \frac{1}{R}}$$
            
$$\frac{s/C}{s^2+\frac{s}{CR}+\frac{1}{CL}}$$

In this case, $$\omega_{0}^2 = \frac{1}{CL}$$ and $$\frac{\omega_0}{Q} = \frac{1}{CR}$$

$$\omega_0 = 1/\sqrt{LC}$$

$$Q = \omega_0 CR$$

Using this structure,

$$T(s) = \frac{v_0}{v_i} = \frac{Z_2}{Z_1+Z_2}$$

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/res-lpf.png">
</p>

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/res-notch.png">
</p>

By following the structure $$T(s) = \frac{v_0}{v_i} = \frac{Z_2}{Z_1+Z_2}$$, it can be seen that from these structures the transfer function for each second order filter can be derived by these circuits. It can also be seen that the order of capacitors are mirrored by the single order op amp filters.

#### Antoniou Inductance Circuit

Inductors in the resonator circuits can be replaced by a system of op amps, such as the *Antoniou Inductance Simulation Circuit*.

From the circuit below, an impedance $$Z = sC_4R_1R_3R_5/R_2$$, $$L = C_4R_1R_3R_5/R_2$$

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/antoniou.png">
</p>

The design of this circuit is usually based on selecting $$R_1 = R_2 = R_3 = R_5 = R$$ and $$C_4 = C$$, which leads to $$L = CR^2$$. When used in a resonator,

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/antoniou-res.png">
</p>

This circuit would have a pole frequency $$\omega_0 = 1/LC_6 = 1/C_4C_6R_1R_3R_5/R_2$$ 

The gain would be derived from $$+K$$ op amp, $$Q = \omega_0C_6R_6$$, $$\omega_0 = 1/CR$$.

#### Filter Types

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/lp-antoniou.png">
</p>

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/hp-antoniou.png">
</p>

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/bp-antoniou.png">
</p>

The position of the capacitor $$C$$ in each case will mirror the filter type in the first order filters, and in each case the gain will be created through $$+K$$.

### Second Order Active Filters Based on Two Integrators

Biquads based on the two-integrator-loop topology are the most versatile and popular second-order filter realizations. There are two varieties: the KHN circuit, which realizes the LP, BP, and HP functions simultaneously and can be combined with the output summing amplifier to realize the notch and all-pass functions; and the Tow–Thomas circuit, which realizes the BP and LP functions simultaneously. Feedforward can be applied to the Tow–Thomas circuit to obtain the circuit, which can be designed to realize any of the second-order functions.

#### KHN Biquad

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/khn.png">
</p>

Analyzed by superposition,

$$V_{hp} = \frac{R_3}{R_2+R_3}(1+ \frac{R_f}{R_1})V_i + \frac{R_2}{R_2 + R_3}(1 + R_f)(-\frac{\omega_0}{s} V_{hp}) - \frac{R_f}{R_1}(\frac{\omega_{0}^2}{s^2} V_{hp})$$

Where $$R_f/R_1 = 1$$, $$R_3/R_2 = 2Q - 1$$, and $$K = 2 - (1/Q)$$

Center frequency, $$KQ = 2Q - 1$$ and $$\omega_0 = 1/RC$$.

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/tow.png">
</p>

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/tow-feed.png">
</p>

### Single Amplifier Biquadratic Active Filters

Single-amplifier biquads (*SABs*) are obtained by placing a bridged-T network in the negative-feedback path of an op amp. If the op amp is ideal, the poles realized are at the same locations as the zeros of the $$RC$$ network. The complementary transformation can be applied to the feedback loop to obtain another feedback loop having identical poles. Different transmission zeros are realized by feeding the input signal to circuit nodes that are connected to ground. SABs are economic in their use of op amps but are sensitive to the op-amp nonidealities and
are thus limited to low-$$Q$$ applications ($$Q \leq 10$$).

#### Bridged T Amplifiers

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/bridge-t.png">
</p>

$$\omega_0 = 1/\sqrt{C_1C_2R_3R_4}$$

$$Q = (\frac{\sqrt{C_1C_2R_3R_4}}{R_3})(\frac{1}{C_1}+\frac{1}{C_2})^{-1}$$

$$m = 4Q^2$$

$$CR = \frac{2Q}{\omega_0}$$

$$R_3 = R$$, $$R_4 = R/m$$

### Sensitivity

The classical sensitivity function $$S^{y}_x = \frac{\partial{y}/y}{\partial{x}/x}$$ is a very useful tool in investigating how tolerant a filter circuit is to the unavoidable inaccuracies in component values and to the nonidealities of the op amps.

## Signal Generators and Waveform-Shaping Circuits

There are two distinctly different types of signal generator: the linear oscillator, which utilizes some form of resonance, and the nonlinear oscillator or function generator, which employs a switching mechanism implemented with a multivibrator circuit.

### Oscillator Feedback loop

When an output signal is used as input into the $$v_+$$ terminal of an op amp, a feedback loop is formed where, if the gain is found to be greater than unity, the feedback signal will be summed positively. The feedback and gain loop are then:

$$A_f(s) = \frac{A(s)}{1-A(2)\beta(s)}$$

$$L(s) = A(s)\beta(s)$$

For a feedback loop to produce sinusoidal osciallations at frequency $$\omega_0$$,

$$L(j\omega_0) = A(j\omega_0)\beta(j\omega_0) = 1$$

This is the *Barkhausen criterion*.

When analyzing a given oscillator circuit, follow the following steps:

* Break the feedback loop to determine the loop gain $$A(s)\beta(s)$$.
* The oscillation frequency $$\omega_0$$ is found as the frequency for which the phase angle of $$A(j\omega)\beta(j\omega)$$ is zero or, equivalently, 360.
* The condition for the oscillations to start is found from $$A(j\omega_0)\beta(j\omega_0)$$ $$\geq 1$$

#### Amplitude Control

A popular limiter circuit used to control the amplitude of oscillating circuits is pictured below. By disconnecting the feedback loop, the linear gain $$-\frac{R_f}{R_1}$$ is found. When the input source goes positive of negative, the limiting value $$L_+$$ or $$L_-$$ can be found, as seen in the transfer characteristic.

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/lim-char.png">
</p>

$$L_+ = V\frac{R_4}{R_3} + V_D(1 + \frac{R_4}{R_3})$$, $$L_- = V\frac{R_3}{R_2} - V_D(1 + \frac{R_3}{R_2})$$

#### Wien Bridge

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/wien.png">
</p>

$$w_0 = 1/CR$$

$$L(s) = (1+\frac{R_2}{R_1})\frac{Z_p}{Z_p+Z_s}$$

### Bistable Multivibrators

A bistable multivibrator is an op amp circuit that switches between two stable states indefinitely when it receives a trigger signal.

The op amp will saturate at the value $$L^+$$ or $$L^-$$, until a value less than, or greater than $$L^+\frac{R_1}{R_1+R_2}$$ is presented at the inverting input.

From the transfer characteristics of the non-inverting feedback loop, we can derive this relationship:

$$v_+ = v_o \frac{R_1}{R_1+R_2} = L^+\beta$$

$$L^+\beta - v_I = 0 \rightarrow \textit{no change}$$

$$L^+\beta - (L^+\beta + 1) = -1 \rightarrow L^-$$

When the $$v_I$$ value exceeds the other input, it will trigger a positive feedback loop which fixes the op amp at its positive or negative saturation.

This pair of values in the negative and positive direction are the $$V_{TH}$$ and $$V_{TL}$$, which can be found to be $$L^+\beta$$ and $$L^-\beta$$.

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/bistable.png">
</p>

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/bistable-neg-char.png">
</p>

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/bistable-pos-char.png">
</p>

For the non-inverting bistable circuit, superposition must be used to find the value of $$v^+$$ due to the input $$v_I$$ and the output $$v_o$$ being fed back into the op amp. Therefore,

$$v^+ = v_I\frac{R_2}{R_1+R_2} + v_o\frac{R_1}{R_1+R_2}$$

To find the $$V_{TH}$$ and $$V_{TL}$$ for this circuit, we must find values that create make $$v^+$$ less than zero. Assuming the state that this will happen, set $$v_o$$ to $$L^+$$, $$v^+$$ to $$0$$, and $$v_I$$ to $$V_{TL}$$. Rearranging and solving for $$V_{TL}$$,

$$V_{TL} = -L_+\frac{R_1}{R_2}$$

This technique can be used to find the $$V_{TH}$$ as well, by rewriting for $$L_+$$.

$$V_{TH} = -L_-\frac{R_1}{R_2}$$

For each case, adding a reference DC voltage $$V_R$$ to an input will move the characteristic horizontally by a value of $$V_R$$, as the $$v_I$$ input must now match $$L^+\beta + V_R$$, for example.

### Astable Multivibrators

By connecting a bistable multivibrator with an RC circuit in a feedback loop, a square wave can be generated where the circuit will switch states periodically. The capacitor will charge until it reaches $$\beta L^+$$, then discharge until $$\beta L^-$$, upon which time it will begin charging again.

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/astable.png">
</p>

The time constant for this circuit is $$\tau = CR$$, which will define the period.

$$T = 2\tau \text{ln}\frac{1+\beta}{1-\beta}$$

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/triangle.png">
</p>

$$T_1 = CR\frac{V_{TH}-V_{TL}}{L^+}$$

$$T_2 = CR\frac{V_{TH}-V_{TL}}{L^-}$$

### Monostable Multivibrator

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/mono.png">
</p>

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/mono-char.png">
</p>

A single pulse seen at point $$E$$ will trigger $$L_-$$ saturation, where point $$B$$ will be pulled through the capacitor, as the negative voltage turns off $$D_1$$.

After the period $$T$$, the circuit will saturate to $$L_+$$ again, upon which point it will stabilize until the next pulse.

### Precision Rectifiers

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/prec-char.png">
</p>

<p align="center">
    <img src="/assets/img/study-guides/circuits-ii/prec-full-char.png">
</p>

