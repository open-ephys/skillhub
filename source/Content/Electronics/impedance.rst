:notoc:

.. _refimpedance:

.. |Ve| replace:: V\ :sub:`e`\
.. |Ce| replace:: C\ :sub:`e`\
.. |Rm| replace:: R\ :sub:`m`\
.. |Rsh| replace:: R\ :sub:`sh`\
.. |Rs| replace:: R\ :sub:`s`\
.. |Re| replace:: R\ :sub:`e`\
.. |Za| replace:: Z\ :sub:`a`\
.. |Ze| replace:: Z\ :sub:`e`\
.. |Csh| replace:: C\ :sub:`sh`\
.. |Vin| replace:: V\ :sub:`in`\
.. |Vec| replace:: V\ :sub:`ec`\
.. |Vout| replace:: V\ :sub:`out`\

***********************************
Impedance
***********************************

This is a brief overview that will focus on how impedance measurements relate to electrophysiology recordings.

Joana Neto introduces Impedance
###################################

.. raw:: html

  <center><iframe width="560" height="340" src="https://www.youtube.com/embed/fVloDI4b1ts" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></center>
  <br>

What is impedance
###################################
Resistance (measured in Ohms) tells us how much opposition there is to current flow, when that current is flowing in one consistent direction. However, our mains power supplies and our neurons have *alternating signals* where current flow changes direction at certain frequencies. In the mains power supply this is usually at 50 or 60hz, depending on the country you live in. In our neurons, this alternating current is generated because our positive and negative ions can cross the lipid bilayer both into and out of the cell. Sometimes you will have a net positive current coming towards your electrode, and sometimes the positive ions will be moving away from your electrode. To measure the opposition to current flow in these situations, we use Impedance (Z) instead of resistance.

If we apply an alternating voltage to a resistor, capacitor or circuit, and measure the current flow, we can determine the impedance Z, measured in Ohms. The impedance Z is specific to a certain frequency and represents opposition to current flow at that frequency, allowing us to describe the relationship between voltage and current for time-varying signals. The impedance Z can be computed as:

.. math::

  Z = \frac{V(t)}{I(t)}

So why can't we just keep using resistance as a measurement? First, because resistance only has magnitude. Impedance is a vector value, which has both magnitude and phase (θ). Impedance provides the magnitude and phase relationship between V and I and can be measured over a broad frequency range (from 1 Hz to 10 kHz). Let’s examine the response of resistors and capacitors to an applied sinusoidal voltage (an alternating signal).

Resistors
***********************************
For resistors, the impedance magnitude (Z) is constant and does not vary with the frequency of signal applied. The impedance follows Ohm's Law (V = IR), which doesn't take the frequency of the signal into account. This is why we usually talk about resistance rather than impedance when we're dealing with resistors, because we don't need the frequency/phase component.

Capacitors
***********************************
In contrast, when we apply an alternating signal to a capacitor, we see that the current is 90° out of phase with the voltage. To be able to accurately convey what the capacitor does to the circuit, we need a value to describe this phase difference.
Secondly, and this is very crucial for electrophysiology, the magnitude of capacitor impedance *decreases* as the frequency of the signal *increases*. We can therefore only describe the impedance of a capacitor at a certain frequency, as:

.. math::

  Zc = \frac{1}{2 \pi fC}

The larger the capacitance C of the capacitor, the lower the impedance at a specific frequency.

.. hint::
  If you want to play around with this idea before moving on, try plotting the relationship between impedance and frequency for a capacitor with C = 2. Then plot the same line for C = 20. What is the difference? Remember that we are interested in signals that last 1 ms, so are around 1kHz.

.. _refwhyimpedance:

Why is impedance important?
###############################

Essentially, impedance is important because all parts of our acquisition system resist current flow, and therefore provide impedance. Depending on the relative sizes of these impedances, we can either protect or precious neuronal signal, or lose all of it to ground. Additionally, there are certain frequencies that are particularly important in our electrophysiology signal, depending on what you are measuring. We have to make sure that our acquisition system has appropriate impedance *at the frequency we are interested in*, so that these signals are passed through the system.

If we look at the equivalent circuit of the electrode, we can see that the signals coming from our neurons can be lost to ground by passing through the electrode circuit and the shunt capacitance (|Csh|), causing a difference between the voltage picked up at the electrode (|Vec|) and the voltage that reaches the acquisition system (|Vin|).

.. image:: ../_static/images/EEA/eea_fig-9.png
  :align: center

We can simplify the resistors and capacitors in the circuit with a representation of the impedance (Z) they provide.

.. image:: ../_static/images/EEA/eea_fig-27.png
  :align: center

This gives us a :ref: Voltage Divider , where:

.. math::

  Vin = \frac{ZCs}{ZCs+Ze} Vec

Therefore, the ratio of impedance between the electrode and shunt capacitance determines how much of our electrode tip voltage reaches the rest of the recording system.

To get more of our voltage |Ve| into our recording system, we can adjust this ratio by either:

1.	Reducing the electrode impedance |Ze|
2.	Increasing the shunt impedance Z |Csh|

Electrode Impedance
***********************************
The impedance of an electrode is a measure of its ability to resist the flow of charge across the electrode-solution interface (i.e., across the electronic conductor (metal) and ionic conductor (extracellular fluid)). It is the impedance of the whole electrode equivalent circuit we built yesterday, consisting of the resistance of the solution (|Rs|), the resistance of the electrode metal (|Rm|) and the resistance (|Re|) and capacitance (|Ce|) of the double layer at the electrode-solution interface.
Since |Re| is large, in the order of several megohms, and |Rs| and |Rm| are low (Ohms), the equivalent circuit is dominated by the double-layer capacitor, |Ce|.  Therefore, in practice, the electrode is primarily a capacitor in series with |Rm| and |Rs| , whose leakage resistance Re, while not negligible, does not make an important contribution (Robinson, 1968).

So far, we know that the impedance magnitude of a capacitor decreases with increased capacitance, and that electrode impedance is dominated by double layer capacitor, |Ce|. Therefore, to decrease our electrode impedance, we need to increase the electrode capacitance |Ce|. How can we increase the value of |Ce|?

.. math::

  C = \frac{\epsilon}{A}

The capacitance of a capacitor, in Farads, is proportional to the area of the capacitor plates (A) divided by the distance (d) between them. ε is the electrostatic constant. To make C bigger, we can increase A by increasing the surface area of the electrode. We can also coat electrodes with materials complemented with pseudo-capacitance, such as conducting polymers or transition metal oxide films, such as IrOx (Green, Lovell, Wallace, & Poole-Warren, 2008; Musa, 2011).
Electrode impedance magnitude is often measured at 1 kHz, before and after electrode coating, showing an impedance decrease up to 10-fold (Neto et al., 2018). By increasing the capacitance (|Ce|) of our electrode, the electrode impedance (|Ze|) will be smaller, preserving more of our signal amplitude at |Vin| (|Vin| = |Vec|). Electrodes impedance values are in the kOhm to MOhm range at 1 kHz.

Recording System Impedance
***********************************
The building blocks of the recording system are amplifiers. These integrated circuits provide incredibly high ‘input impedance’. It is as if any input has to cross a huge resistor first before getting to the amplifier.
