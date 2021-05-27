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

There are a lot of resources available for learning about more fundamental physics topics, this is a brief overview that will focus on how impedance measurements relate to electrophysiology.

Introductory talk
###################################

`Link to Joana Neto's talk about impedance. <https://youtu.be/fVloDI4b1ts>`_

What is impedance
###################################
If we apply an alternating voltage to a resistor, capacitor or circuit, and measure the current flow, we can determine the impedance Z, measured in Ohm. The impedance represents opposition to current flow, allowing us to describe the relationship between voltage and current for time-varying signals. Just as with resistance and Ohm’s Law, the impedance Z assumes an AC current of a specific frequency and can be computed as:

.. math::

  Z = \frac{V(t)}{I(t)}

Impedance can be represented as a vector defined in terms of magnitude and phase (θ). Therefore, impedance provides both the magnitude and phase relationship between V and I over a broad frequency range (from 1 Hz to 10 kHz). Let’s examine the response of resistors and capacitors to an applied sinusoidal voltage (an alternating signal).

Resistors
***********************************
For resistors, the impedance magnitude (Z) is constant and does not vary with the frequency of signal applied. The impedance follows Ohm's Law (V = IR), which doesn't take the frequency of the signal into account.

Capacitors
***********************************
In contrast, for a capacitor the current is 90° out of phase with the voltage, and the magnitude of impedance decreases as the frequency increases. We can therefore only describe the impedance of a capacitor at a certain frequency.

.. math::

  Zc = \frac{1}{2 \pi fC}

So the magnitude of impedance of a capacitor will decrease with increasing frequency. The larger the capacitance C, the lower the impedance at a specific frequency.

.. hint::
  If you want to play around with this idea before moving on, try plotting the relationship between impedance and frequency for a capacitor with C = 2. Then plot the same line for C = 20. What is the difference? Remember that we are interested in signals that last 1 ms, so are around 1kHz.

.. _refwhyimpedance:

Why is impedance important?
###############################

If we look at the equivalent circuit of the electrode, we can see that the signals coming from our neurons can be lost to ground by passing through the electrode circuit and the shunt capacitance (|Csh|), causing a difference between Vec and Vin.

.. raw:: html

    <div class="col-lg-12 col-md-12 col-sm-12 col-xs-12 d-flex mx-auto" style = "max-width: 100%">
        <div class="card text-center intro-card border-white">
        <img src="../_static/images/eea_fig-9.png" class="card-img-top">
        </div>
    </div>

We can replace the resistors and capacitors with a representation of the impedance (Z) they provide.

.. raw:: html

    <div class="col-lg-12 col-md-12 col-sm-12 col-xs-12 d-flex mx-auto" style = "max-width: 100%">
        <div class="card text-center intro-card border-white">
        <img src="../_static/images/eea_fig-27.png" class="card-img-top">
        </div>
    </div>

This gives us a voltage divider, where:

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

Amplifiers
###################################

Let’s go over what an operational amplifier does.

.. raw:: html

    <div class="col-lg-12 col-md-12 col-sm-12 col-xs-12 d-flex justify-content-center mx-auto" style = "max-width: 100%">
        <div class="card text-center intro-card border-white">
        <img src="../_static/images/eea_fig-28.png" class="card-img-top">
        </div>
    </div>

The operational amplifier has two inputs, and basically takes the voltage difference between them. If that difference is positive, it connects its output to one ‘power rail’, like for example 3V, and if it's negative it connects its output to the other rail, that could be ground, or -3V. Another way to say the same thing would be that it amplifies the difference between its input with a huge factor, also called ‘gain’.

While doing that, the operational amplifier draws basically no current on its inputs.

.. raw:: html

    <div class="col-lg-12 col-md-12 col-sm-12 col-xs-12 d-flex justify-content-center mx-auto" style = "max-width: 100%">
        <div class="card text-center intro-card border-white">
        <img src="../_static/images/eea_fig-29.png" class="card-img-top">
        </div>
    </div>

If we connect the output of the operational amplifier to the ‘-’ input, then the following happens:

-	Initially, the operational amplifier will output a very high voltage if the difference across it inputs is positive, and a very low one if its negative (like we said, the gain is extremely high).

-	If we connect the output back to ‘-’, this behaviour will keep the voltages at its ‘+’ and ‘-’ inputs the same. Any positive difference between its input terminals will lead to a higher voltage applied to the ‘-’ input, bringing them back together, and vice-versa.

-	Now, *the ‘-’ input is always actively driven to follow the voltage on the ‘+’ input*. This means that whatever voltage we connect to the ‘+’ input can be measured just by looking at the ‘-’ input (which is connected to / the same as the output).

We can look at the voltage that is on ‘+’ by just measuring the output of the operational amplifier, BUT because the ‘+’ input draws almost no current at all (in other words, very high input impedance), we can now measure weak signals. The output of the operational amplifier on the other hand side has very low output impedance, in other words we can draw a lot of current from it and it will keep its voltage.

You can run this example in the simulator, and see if what we said above about the operational amplifier makes sense. You should see that the operational amplifier stops the cable from drawing current from the electrode, and that the operational amplifier instead manages to ‘drive’ the cable effortlessly, by providing a lot of current.

.. raw:: html

    <div class="col-lg-12 col-md-12 col-sm-12 col-xs-12 d-flex justify-content-center mx-auto" style = "max-width: 100%">
        <div class="card text-center intro-card border-white">
        <img src="../_static/images/eea_fig-30.png" class="card-img-top">
              <a href="https://tinyurl.com/y6pvxdx9" class="btn btn-light stretched-link">Simulator Link</a>
        </div>
    </div>

Our electrodes will be attached to a headstage, which contains an amplifier. This amplification step performs several functions:

-	Prevents us from drawing current from the brain and allows to drive current to ADC and computer
-	Rejects common mode noise
-	Increases the range of the signal to fit the dynamic range of our digitizer

Amplifier Impedance
***********************************
The input impedance of an amplifier is very high. This means that the circuit acts as though the current has to cross a very high resistor to actually enter the amplifier. The amplifier input impedance, Z\ :sub:`a`\  represents its tendency to oppose the flow of current from the electrodes through the amplifier to ground. This high impedance prevents us from drawing current from the brain to ground. By designing amplifiers which have high input impedances, the current flow becomes low (Ferree et al., 2001).

Here is the amplifier added into our circuit diagram:

.. raw:: html

    <div class="col-lg-12 col-md-12 col-sm-12 col-xs-12 d-flex justify-content-center mx-auto" style = "max-width: 100%">
        <div class="card text-center intro-card border-white">
        <img src="../_static/images/eea_fig-31.png" class="card-img-top">
        </div>
    </div>

The path from our neuronal currents first crosses the electrode and then goes either through the amplifier to ground, or through shunting routes (|Csh| and |Rsh|) to ground. The amplifier has its own (very high) impedance |Za|.

The output impedance of amplifiers is very low. Low impedance means that a lot of current can flow. This current enables the driving of the signal through all the subsequent circuits (e.g., interconnect lines, multiplexer, and ADC). By placing an amplifier in our circuit, we make sure that the rest of our recording circuit is driven by current provided by the amplifier, not by current provided by the neurons.

Shunt Impedance
***********************************
Shunt impedance is the total impedance of shunt capacitance |Csh| and shunt resistance |Rsh|. Remember that any two conducting surfaces, with a non-conducting layer in between, *is* a capacitor. Shunt capacitance arises mainly from the capacitance across the thin insulation isolating an electrode shaft and the surrounding electrolyte, as well as the cumulative capacitance along cables and connectors (Robinson, 1968). Being capacitive, the impedance decreases with signal frequency (Nelson et al., 2008). Therefore, to create a large shunt impedance, the shunt capacitance should be small:

.. math::
  Z = \frac{1}{2 \pi fC}

Basically, the more signal takes this route to ground, the less signal we will pick up in our recording signal. Though there is also a resistive shunt element (|Rsh|), at the high frequencies we are interested in the capacitive component will usually have the largest effect (because of its low impedance), so |Rsh| is often ignored.

Effective amplifier input impedance
***********************************
The 'effective amplifier input impedance', |Za|’ is the total impedance to the ground seen from the electrode. This includes the path through the amplifier AND the path through the parallel shunting routes (shunt resistance and capacitance) to ground outside the amplifier.

.. raw:: html

    <div class="col-lg-12 col-md-12 col-sm-12 col-xs-12 d-flex justify-content-center mx-auto" style = "max-width: 50%">
        <div class="card text-center intro-card border-white">
        <img src="../_static/images/eea_fig-32.png" class="card-img-top">
        </div>
    </div>

.. math::

  Vin = \frac{Za'}{Za' + Ze} Ve

|Za|' = 'effective amplifier' impedance (|Za| + Z |Csh| + |Rsh|)
|Ze| = electrode impedance

The ratio between the effective amplifier impedance and the electrode impedance determines how much of our precious signal we can pick up. This is particularly important when the electrodes have a large impedance themselves and are therefore more susceptible to attenuation by shunt capacitance (Obien et al., 2015; Robinson, 1968). For instance, the shunt capacitance for a tungsten wire (~50 to 100 pF) is usually higher than for a silicon probe (5-20 pF/cm). (Why? Think of what makes a capacitor, and the relative shape and conductances of these electrodes).

To have no net current flowing, the shunt and amplifier impedance should be infinite. Moreover, if |Za|’ is not substantially greater than |Ze|, |Vin| will be much lower than |Vec|. The best-case scenario is to have high |Za|’ and low |Ze|. To have low |Za|’, we need amplifiers with high input impedance and low shunt capacitance (high impedance).
