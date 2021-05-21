.. toctree::
   :maxdepth: 3

.. _refEDay3:

.. |Ve| replace:: V\ :sub:`e`\
.. |Ce| replace:: C\ :sub:`e`\
.. |Rm| replace:: R\ :sub:`m`\
.. |Re| replace:: R\ :sub:`e`\
.. |Cs| replace:: C\ :sub:`s`\
.. |Vin| replace:: V\ :sub:`in`\
.. |Vec| replace:: V\ :sub:`ec`\
.. |Vout| replace:: V\ :sub:`out`\

Exercises Day 3
================================

.. note::
  By end of day; everyone should have EMG. This day is usually a lot of debugging and going over things that have been covered before, making sure everyone understands what is going on.


Today we are going to build an EMG circuit! We'll use the electrodes in your kit, an instrumentation amplifier as our headstage, and the Teensy will be our acquisition board. We now have all the steps of the acquisition in place to simulate a lab experiment.

.. raw:: html

    <div class="col-lg-12 col-md-12 col-sm-12 col-xs-12 d-flex mx-auto" style = "max-width: 100%">
        <div class="card text-center intro-card border-white">
        <img src="../_static/images/EEA/eea_fig-5.png" class="card-img-top">
          <div class="card-body">
          <h5 class="card-title" > https://tinyurl.com/yf9jdf2b </h5>
          </div>
        </div>
    </div>

Electrodes
***********
.. warning::

  Your kit contains surface electrodes that we will use for EMG. These measurements involve attaching yourself to a circuit, so follow these rules to be safe:

  A.	Do not use anything other than the recommended batteries to power your circuit. Do not connect your circuit to mains supply for power, ground, anything.
  B.	Only connect the EMG electrodes to one arm. Don’t attach them to both arms. This is to avoid any current travelling across your heart.
  C.	If you are using a laptop, disconnect your laptop charger & run from battery while the electrodes are attached to you. This is to prevent any surges from mains supply from backpropagating through your laptop, to you.

The electrodes clip onto the cable with three wires. We’ll be using an audio-to-breadboard jack to get the signal from the electrodes into the breadboard.

Instrumentation Amplifier
**************************

`This <https://www.analog.com/media/en/technical-documentation/data-sheets/AD622.pdf>`_ is the datasheet for the instrumentation amplifier in your kit.

.. raw:: html

    <div class="col-lg-12 col-md-12 col-sm-12 col-xs-12 d-flex mx-auto" style = "max-width: 50%">
        <div class="card text-center intro-card border-white">
        <img src="../_static/images/EEA/eea_fig-61.png" class="card-img-top">
        </div>
    </div>


EMG circuit
************

First, we’ll wire up our electrodes to our instrumentation amp and read out the result with our oscilloscope. Later, we'll add the Teensy.

1.	Click the surface electrodes onto the ends of the cable
  a.	Black = ground electrode
  b.	Blue = - (reference) electrode
  c.	Red = + electrode
2.	Put a 220 Ohm resistor over the instrumentation amplifier
3.	Use your oscilloscope to measure EMG! You should see a clear signal when you tense your muscles. Moving your arm will cause large motion artefacts (why?) so try to find the nicest signal.
4.	The resistor across the instrumentation amplifier sets the gain of the amplifier. Change the gain of the amplifier by changing Rg. What happens when the value for Rg is very low?

.. raw:: html

    <div class="col-lg-12 col-md-12 col-sm-12 col-xs-12 d-flex mx-auto" style = "max-width: 100%">
        <div class="card text-center intro-card border-white">
        <img src="../_static/images/EEA/eea_fig-62.png" class="card-img-top">
        </div>
    </div>

    <div class="col-lg-12 col-md-12 col-sm-12 col-xs-12 d-flex mx-auto" style = "max-width: 100%">
        <div class="card text-center intro-card border-white">
        <img src="../_static/images/EEA/eea_fig-63.png" class="card-img-top">
        </div>
    </div>


.. tip::
  If you have a lot of noise on your recording, try:
  •	Disconnecting from 60/50Hz contaminated ground by using laptop battery
  •	Try twisting or braiding the cables


Streaming data from a microcontroller
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

We’re going to start streaming data to the pc, by using our Teensy microcontroller to digitize the analog signals we collect.

A. Connect the output from your amplifier to an analog input node on the Teensy as shown below. This is a 220 Ohm resistor across the instrumentation amplifier, and a voltage divider made of two equal resistors (anything above 1KOhm, see the text on ‘shifting the bipolar signal up’ below).
B. Upload ‘Firmata.ino’ to the Teensy
C. Open Bonsai and create an Analog Input node.

.. raw:: html

    <div class="col-lg-12 col-md-12 col-sm-12 col-xs-12 d-flex mx-auto" style = "max-width: 100%">
        <div class="card text-center intro-card border-white">
        <img src="../_static/images/EEA/eea_fig-64.png" class="card-img-top">
        </div>
    </div>

.. note::
  It should work with just ‘AnalogInput’. It’s nicer to use the ‘CreateArduino’ node and specify the Teensy, this also allows you to set the sampling interval, so you can increase it if the computer is struggling. Use .csvwriter to save signals.

Shifting the signal
^^^^^^^^^^^^^^^^^^^^^
The EMG signal is from -3 to +3V, but we can only digitize positive voltages. With a simple trick we can shift the signal up from -3 to 3V exactly into the 0-3V range we want, while still providing the amplifier with a -3 to +3V range.

.. raw:: html

    <div class="col-lg-12 col-md-12 col-sm-12 col-xs-12 d-flex mx-auto" style = "max-width: 100%">
        <div class="card text-center intro-card border-white">
        <img src="../_static/images/EEA/eea_fig-65.png" class="card-img-top">
        </div>
    </div>

This voltage divider is not going to mess with our signal, because the signal is protected by the amplifier. You could in theory use almost any reasonable values for R, over 1kΩ, because the output impedance of the instrumentation amplifier is low and the input impedance (of the teensy analog input) is decently high. If you make R too small, this will still work on paper, but you’re now asking the op-amp to keep shovelling current into ground (or in this case, the 3V rail) through a small R, and eventually even an op-amp will get unhappy.


Acknowledgements
===============================
Written by:

* Alexandra Leighton
* Joana Neto
* Jakob Voigts
* Aarón Cuevas López
* Jon Newman

With material from:

* Joana Neto, 2018; Materials and neuroscience: validating tools for large-scale, high-density neural recording, 2018.
* Jon Newman and Jakob Voigts, 2017; Intro to Chronic Ephys (presentation at TENSS)
* Mitra Javadzadeh, 2017; Building an analog ephys recording system (practical exercises developed for TENSS)

Licensing
===============

This work is licensed under CC BY-SA 4.0. To view a copy of this license, visit https://creativecommons.org/licenses/by-sa/4.0/
