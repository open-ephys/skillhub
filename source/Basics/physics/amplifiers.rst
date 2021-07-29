.. _refamplifierintro:

***********************************
Amplifiers
***********************************

Let’s start with what an operational amplifier does.

.. image:: ../_static/images/EEA/eea_fig-28.png
  :align: center

The operational amplifier has two inputs, and basically takes the voltage difference between them. If that difference is positive, it connects its output to one ‘power rail’, like for example 3V, and if it's negative it connects its output to the other rail, that could be ground, or -3V. Another way to say the same thing would be that it amplifies the difference between its input with a huge factor, also called ‘gain’.

While doing that, the operational amplifier draws basically no current on its inputs.

.. image:: ../_static/images/EEA/eea_fig-29.png
  :align: center

If we connect the output of the operational amplifier to the ‘-’ input, then the following happens:

-	Initially, if '+' is higher than '-', the operational amplifier will output a very high voltage.

-	If we connect the output back to ‘-’, the amplifier will continue to output a high voltage, but now this voltage starts to increase the value of '-', bringing the value of the inputs closer together. This behaviour will keep the voltages at its ‘+’ and ‘-’ inputs the same.

-	Now, *the ‘-’ input is always actively driven to follow the voltage on the ‘+’ input*. This means that whatever voltage we connect to the ‘+’ input can be measured just by looking at the ‘-’ input (which is connected to / the same as the output).

We can look at the voltage that is on ‘+’ by just measuring the output of the operational amplifier, BUT because the ‘+’ input draws almost no current at all (in other words, very high input impedance), we can now measure weak signals. The output of the operational amplifier on the other hand side has very low output impedance, in other words we can draw a lot of current from it and it will keep its voltage.

You can run this example in the simulator, and see if what we said above about the operational amplifier makes sense. You should see that the operational amplifier stops the cable from drawing current from the electrode, and that the operational amplifier instead manages to ‘drive’ the cable effortlessly, by providing a lot of current.

|

.. image:: ../_static/images/EEA/eea_fig-30.png
  :align: center
  :target: https://tinyurl.com/y6pvxdx9


Our electrodes will be attached to a headstage, which contains an amplifier. This amplification step performs several functions:

-	Prevents us from drawing current from the brain and allows to drive current to ADC and computer
-	Rejects common mode noise
-	Increases the range of the signal to fit the dynamic range of our digitizer

.. raw:: html

  <center><iframe width="560" height="340" src="https://www.youtube.com/embed/NP6nE5P82e8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></center>


Amplifier Impedance
***********************************
The input impedance of an amplifier is very high. This means that the circuit acts as though the current has to cross a very high resistor to actually enter the amplifier. The amplifier input impedance, Z\ :sub:`a`\  represents its tendency to oppose the flow of current from the electrodes through the amplifier to ground. This high impedance prevents us from drawing current from the brain to ground. By designing amplifiers which have high input impedances, the current flow becomes low (Ferree et al., 2001).

Here is the amplifier added into our circuit diagram:

.. image:: ../_static/images/EEA/eea_fig-31.png
  :align: center


The path from our neuronal currents first crosses the electrode and then goes either through the amplifier to ground, or through shunting routes (|Csh| and |Rsh|) to ground. The amplifier has its own (very high) impedance |Za|.

The output impedance of amplifiers is very low. Low impedance means that a lot of current can flow. This current enables the driving of the signal through all the subsequent circuits (e.g., interconnect lines, multiplexer, and ADC). By placing an amplifier in our circuit, we make sure that the rest of our recording circuit is driven by current provided by the amplifier, not by current provided by the neurons.
