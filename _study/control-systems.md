---
layout: study_guide
title: 'Control Systems'
caption: Memorial University ENG5821
description: > 
date: '14-04-2022'
---

* this unordered seed list will be replaced by the toc
{:toc}

## Introduction

### System Configuration

<p align="center">
    <img src="/assets/img/study-guides/control-systems/system-blocks.png">
</p>

**Open Loop** systems do not monitor or correct the output for disturbances; however, they are simpler and less expensive than closed-loop systems.

**Closed Loop** systems monitor the output and compare it to the input. If an error is detected, the system corrects the output and hence corrects the effects of disturbances.

### Analysis and Design Objectives

#### Transient Response

That part of the response curve due to the system and the way the system acquires or dissipates energy. In stable systems it is the part of the response plot prior to the steady-state response.

#### Steady-State Response

Also known as **Forced Response**, for linear systems, that part of the total response function due to the input. It is typically of the same form as the input and its derivatives.

#### Stability

That characteristic of a system defined by a natural response that decays to zero as time approaches infinity.

## Modeling in the Frequency Domain

## Time Response

## Reduction of Multiple Systems

### Block Diagrams

The block diagram of a linear, time-invariant system consists of four elements: *signals*, systems, summing junctions , and *pickoff points* . These elements can be assembled into three basic forms: *cascade*, *parallel* , and *feedback*.

<p align="center">
    <img src="/assets/img/study-guides/control-systems/reduction.png">
</p>

#### Cascade Form

<p align="center">
    <img src="/assets/img/study-guides/control-systems/cascade.png">
</p>

#### Parallel Form

<p align="center">
    <img src="/assets/img/study-guides/control-systems/parallel.png">
</p>

From the above diagram, it is clear that each branch will be $$R(s)G_1(s)$$, $$R(s)G_2(s)$$, or $$R(s)G_3(s)$$, and when the three are summed at the summer, $$R(s)[G_1(s) + G_2(s) + G_3(s)]$$.

#### Feedback Form

<p align="center">
    <img src="/assets/img/study-guides/control-systems/feedback.png">
</p>

#### Moving Blocks

From these diagrams, the logic of moving each process can be validated when summing each signal and multiplying by each process, then doing the same for its equivalent system.

$$[R(s) + X(s)] * G(s) = R(s)G(s) + X(s)G(s)$$  $$\equiv$$
$$R(s)G(s) + X(s)G(s) = C(s)$$

<p align="center">
    <img src="/assets/img/study-guides/control-systems/move1.png">
</p>

<p align="center">
    <img src="/assets/img/study-guides/control-systems/move2.png">
</p>

## Stability

### Routh-Hurwitz Criteria

<p align="center">
    <img src="/assets/img/study-guides/control-systems/routh-1.png">
</p>

<p align="center">
    <img src="/assets/img/study-guides/control-systems/routh-2.png">
</p>

### Routh-Hurwitz Special Cases

#### Zero Only in the First Column

<p align="center">
    <img src="/assets/img/study-guides/control-systems/routh-e.png">
</p>

<p align="center">
    <img src="/assets/img/study-guides/control-systems/routh-e2.png">
</p>

Assume a value for the variable $$\epsilon$$, and follow through the system, tracking sign changes. This should be the same for either assumed value of $$\epsilon$$.

Alternately, the reverse coefficients of the denominator can be used in analysis, as seen below:

<p align="center">
    <img src="/assets/img/study-guides/control-systems/routh-recip.png">
</p>

<p align="center">
    <img src="/assets/img/study-guides/control-systems/routh-recip2.png">
</p>

#### Entire Row Is Zero

If an entire row is zero, return to the row above, and form the equation represented by those coefficients. For example, from the system below, at row $$s^3$$ there is a row of zeroes. From the row $$s^4$$ above, form the equation $$s^4 + 6s^2 + 8$$. The derivative of this equation will take the place of the row of zeroes. Therefore, $$4s^3 + 12s + 0$$ will take the place of the zeroes in row $$s^3$$.

<p align="center">
    <img src="/assets/img/study-guides/control-systems/routh-roz.png">
</p>

In the case of a row of zeroes formed by a row of even polynomials, for example $$s^4 + s^2 + 1$$, it can be determined that its roots are symmetric about the origin. If we don't have a row of zeroes, we cannot have roots on the $$jw$$-axis. Once a row of zeroes is found for an even polynomial, everything from that row to the end is a test of only the even polynomial. Because in the example above, the zeroes occur in the $$s^3$$ row, it's considered the $$s^4$$ row that causes the zeroes, and it is therefore even.

<p align="center">
    <img src="/assets/img/study-guides/control-systems/routh-zeroes.png">
</p>

<p align="center">
    <img src="/assets/img/study-guides/control-systems/routh-roz-analysis.png">
</p>

From the example above, the row of zeroes can be seen to occur in the $$s^4$$ row. The rest of rows are therefore a test of the even polynomial, where it is determined there are no changes in sign. Thus, there are no poles in the right half plane, and no left plane poles can exist due to symmetry. Therefore, all four poles must be on the $$jw$$-axis.

The findings for the even polynomials are then combined with the findings for the rest of the system:

<p align="center">
    <img src="/assets/img/study-guides/control-systems/routh-even.png">
</p>

## Steady State Errors

\textit Steady State Error  is defined as the difference between the input and output as t $$\rightarrow \infty$$. When testing for factors such as constant position, constant velocity and constant acceleration, inputs such as unit steps $$u(t)$$, ramps $$r(t)$$ and parabolas are used. This discussion is limited to stable systems.\\

<p align="center">
    <img src="/assets/img/study-guides/control-systems/inputs.png">
</p>

Most steady state errors $$E(s)$$ arise from the input and/or the configuration of the system, as seen in the diagrams below for general closed loop and unity feedback systems.

<p align="center">
    <img src="/assets/img/study-guides/control-systems/closedlooperror.png">
</p>

<p align="center">
    <img src="/assets/img/study-guides/control-systems/unityfeedback.png">
</p>

In the first case $$E(s) = R(s) - C(s)$$ is the error. If the input $$R(s)$$ is a step input, then $$C(s)$$ should $$= R(s)$$ and $$E(s) = 0$$. However, if gain $$K$$ is introduced, $$C(s) = KR(s)$$ and $$E(s)$$ must be finite and non-zero.

<p align="center">
    <img src="/assets/img/study-guides/control-systems/integrator.png">
</p>

From these systems we see that $$C(s)$$ = $$KE(s)$$, or $$E(s) = \frac{1}{K} C(s)$$

### Steady State Error for Unity Feedback Systems

Steady-state error can be calculated from transfer function $$T(s)$$ or the open loop transfer function $$G(s)$$. Once $$E(s)$$ is found, the steady state error can be found using the \textit Final Value Theorem , which states that the value at infinity is equal to the Laplace as $$s \rightarrow 0$$.

<p align="center">
    <img src="/assets/img/study-guides/control-systems/closedlooperror.png">
</p>

$$E(s) = R(s) - C(s)$$
$$C(s) = R(s)T(s)$$
$$E(s) = R(s)[1 - T(s)]$$
$$e(\infty) = \text{lim}_s\rightarrow \infty   e(t) = \text{lim}_s\rightarrow 0   sE(s)$$
$$e(\infty) = \text{lim}_s\rightarrow 0  sR(s)[1 - T(s)]$$

#### Steady State Error in Terms of $$G(s)$$

<p align="center">
    <img src="/assets/img/study-guides/control-systems/unityfeedback.png">
</p>

$$E(s) = R(s) - C(s)$$
$$C(s) = E(s)G(s)$$ 
$$E(s) = \frac{R(s)}{1 + G(s)}$$
$$e(\infty) = \text{lim}_s\rightarrow \infty  \frac{sR(s)}{1 + G(s)}$$

### Static Error Constants and System Type

The steady-state error for unit step inputs is

$$e(\infty) = \frac{1}{1 + \text{lim}_s\rightarrow 0  G(s)}$$

The steady-state error for ramp inputs of unit velocity is

$$e(\infty) = \frac{1}{\text{lim}_s\rightarrow 0  sG(s)}$$

The steady-state error for parabolic inputs of unit acceleration is

$$e(\infty) = \frac{1}{\text{lim}_s\rightarrow 0  s^2G(s)}$$

The terms in the denominator are known as $$k_p, k_v, k_a$$, the **static error** constants , representing position, velocity and acceleration, respectively.

Systems can also be defined by **system type**. This defines the number of pure integrations in the forward path, assuming a unity feedback system. Increasing the system type decreases the steady-state error as long as the system is stable.

<p align="center">
    <img src="/assets/img/study-guides/control-systems/types.png">
</p>

This will also be apparent by the structure of the system. An $$s$$ factor in the denominator which won't cancel with $$u(t)$$ input indicates the system is not Type 0. Therefore, testing with a ramp and parabola input will determine whether the static constant is finite for each input.

### Steady-State Error Specifications

The steady-state error is inversely proportional to the static error constant - the larger the constant, the smaller the steady-state error. Increasing gain increases the static error constant, thus, increasing the gain decreases the steady-state error if the system is stable.

### Steady State Disturbances

<p align="center">
    <img src="/assets/img/study-guides/control-systems/disturbance.png">
</p>

$$C(s) = E(s)G_1(s)G_2(s) + D(s)G_2(s)$$

However, $$C(s) = R(s) - E(s)$$, therefore,
    
$$E(s) = \frac{1}{1 + G_1(s)G_2(s)}R(s) - \frac{G_2(s)}{1+G_1(s)G_2(s)}D(s)$$
    
$$e(\infty) = \frac{s}{1 + G_1(s)G_2(s)}R(s) - \frac{sG_2(s)}{1+G_1(s)G_2(s)}D(s)$$

$$e(\infty) = e_R(\infty) + e_D(\infty)$$

### Forming Equivalent Unity from Non-Unity Systems

<p align="center">
    <img src="/assets/img/study-guides/control-systems/nonunity.png">
</p>

## Root Locus Techniques

The following sections apply to \textbf Negative Feedback Closed Loop  systems.

### Sketching the Root Locus

#### Number of Branches

The number of branches in a root locus equal the number of poles.

#### Symmetry

The root locus is symmetrical about the real axis.

#### Real Axis Segments

On the real axis, for $$K > 0$$ the root locus exists to the left of an odd number of real-axis, finite open-loop poles and/or finite open-loop zeros.

#### Starting and Ending Points

The root locus begins at the finite and infinite poles of $$G(s)H(s)$$ and ends at the finite and infinite zeros of $$G(s)H(s)$$.

#### Behavior at Infinity

<p align="center">
    <img src="/assets/img/study-guides/control-systems/asymptotes.png">
</p>

When finding $$K$$, remember that the denominator of the transfer function $$T(s)$$, $$1 + KG(s)H(s) = 0$$ if the point is on the root locus. Set $$s$$ to a known point on the root locus (break in points work) and solve $$1 + KG(s)H(s) = 0$$ for $$K$$.

### Refining the Sketch

#### Breakaway/Break-in Point

At the breakaway or break-in point, the branches of the root locus form an angle of 180°/$$n$$ with the real axis, where $$n$$ is the number of closed-loop poles arriving at or departing from the single breakaway or break-in point on the real axis. These are the points when gain is at its minimum and maximum, respectively.

For all points on the root locus,

$$K = -\frac{1}{G(s)H(s)}$$, $$\frac{1}{G(s)H(s)} = -1$$ and by differential calculus,

$$dK = 0$$ will produce $$\sigma$$, whose zeroes will produce the break-in points.

<p align="center">
    <img src="/assets/img/study-guides/control-systems/breakpoints.png">
</p>

Or, conversely,

$$\sum \frac{1}{\sigma + z_i} = \sum \frac{1}{\sigma + p_i}$$

Where $$z$$ and $$p$$ are the zero and pole values. By equating the two sides and simplifying to a single equation, factoring can produce $$\sigma$$.

#### $$j\omega$$-Axis Crossings

The crossing of the $$j\omega$$ axis defines when the system becomes unstable. The crossing of the $$\omega$$ axis deines the frequency of oscillation, while the gain at the $$j\omega$$ axis yields the maximum positive gain for system stability.

The $$j\omega$$ axis crossings can be found using the Routh-Hurwitz criterion. Forcing a row of zeros yields the gain, then going back a row and solving for the roots yields the frequency at the imaginary axis crossing.

#### Angles of Departure and Arrival

If we assume a point on the root locus $$\epsilon$$ close to a complex **pole** , the sum of angles drawn from all finite poles and zeros to this point is an odd multiple of 180$$^\circ$$. Except for the **pole** that is $$\epsilon$$ close to the point, we assume all angles drawn from all other poles and zeros are drawn directly to the \textbf pole  that is near the point. Thus, the only unknown angle in the sum is the angle drawn from the \textbf pole  that is $$\epsilon$$ close. We can solve for this unknown angle, which is also the angle of departure from this complex **pole**.

$$-\theta_1 + \theta_2 + \theta_3 - \theta_4 - \theta_5 + \theta_6 = (2k+1)180^\circ$$

*or*

$$\theta_1 = \theta_2 + \theta_3 - \theta_4 - \theta_5 + \theta_6 = (2k+1)180^\circ$$

<p align="center">
    <img src="/assets/img/study-guides/control-systems/angles-pole.png">
</p>

If we assume a point on the root locus $$\epsilon$$ close to a complex **zero** , the sum of angles drawn from all finite poles and zeros to this point is an odd multiple of 180$$^\circ$$. Except for the **zero** that is $$\epsilon$$ close to the point, we can assume all angles drawn from all other poles and zeros are drawn directly to the **zero** that is near the point. Thus, the only unknown angle in the sum is the angle drawn from the **zero** that is $$\epsilon$$ close. We can solve for this unknown angle, which is also the angle of arrival to this complex **zero**.

$$-\theta_1 + \theta_2 + \theta_3 - \theta_4 - \theta_5 + \theta_6 = (2k+1)180^\circ$$
    
*or*

$$\theta_2 = \theta_1 - \theta_3 + \theta_4 + \theta_5 - \theta_6 = (2k+1)180^\circ$$

<p align="center">
    <img src="/assets/img/study-guides/control-systems/angles-zero.png">
</p>

Note that finding the angle at these points is calculating the length from the poles or zeroes to this point.

### Plotting and Calibrating the Root Locus

When locating points on the root locus and finding their specified gain, for example as it crosses the radial line representing 20% overshoot, such as the below graph where $$\zeta = 0.45$$

Evaluating the graph at points along the line, and summing the angles from poles and zeros, it can be determined if a point is on the root locus if the angles are a multiple of 180$$^\circ$$.

<p align="center">
    <img src="/assets/img/study-guides/control-systems/calibrating.png">
</p>

$$\zeta = cos(\theta)$$, therefore $$cos^{-1} \zeta = \theta$$

From this value $$\theta$$, the $$x$$ and $$y$$ components of the radial line can be plotted, using cos$$\theta$$, sin$$\theta$$, and $$r$$sin$$\theta$$, $$r$$cos$$\theta$$ to find the components of each radius.

### Generalized Root Locus

If finding the root locus of a system concerning a single parameter instead of gain $$K$$, an equivalent system can be used where the denominator is represented as $$1 + p_1G(s)H(s)$$. From the below system,

$$T(s) = \frac{KG(s)H(s)}{1 + KG(s)H(s)} = \frac{10}{s^2 + (p_1 +2)s + 2p_1 + 10}  = \frac{10}{s^2 + 2s + 10 + p_1(s + 2)}$$

<p align="center">
    <img src="/assets/img/study-guides/control-systems/parameter1.png">
</p>

### Positive Feedback Systems

$$KG(s)H(s) = 1 = 1 \angle k 360^\circ$$

$$k = 0, 1, 2, 3 ...$$

* **Number of Branches**
No change
* **Symmetry**
No change
* **Real Axis Segments**
On the real axis, the root locus for positive-feedback systems exists to the left of an even number of real-axis, finite open-loop poles and/or finite open-loop zeros.
* **Starting and Ending Points**
The root locus for positive-feedback systems begins at the finite and infinite poles of $$G(s)H(s)$$ and ends at the finite and infinite zeros of $$G(s)H(s)$$.
* **Behavior at Infinity**
The root locus approaches straight lines as asymptotes as the locus approaches infinity. Further, the equations of the asymptotes for positive-feedback systems are given by the real-axis intercept, $$\sigma_a$$, and angle, $$\theta_a$$, as follows:


$$\sigma_a = \frac{\sum \text{Finite Poles} - \sum \text{Finite Zeros}}{\text{# of Finite Poles} - \text{# of Finite Zeros}}$$

$$\theta_a = \frac{k2\pi}{\text{# of Finite Poles} - \text{# of Finite Zeros}}$$

## Design via Root Locus

<p align="center">
    <img src="/assets/img/study-guides/control-systems/comps.png">
</p>

## Frequency Response Techniques
