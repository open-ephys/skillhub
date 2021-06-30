:notoc:

***********************************
Filtering 
***********************************

Analog filtering
###################################
Filters are used to remove certain frequencies from our data. We can do this in hardware or in software. Usually hardware filtering (implemented in the amplifier circuit) is used to increase (apparent) signal to noise ratio by rejecting unwanted frequencies and to prevent signal aliasing (e.g., bandpass between 0.5 and 2 kHz).
Remember the exercise where we measured the voltage across our fingers with the oscilloscope, and saw very high values. Even with a differential amplifier, we usually have a decent amount of slow (~<10Hz or so) voltages that are simply too big for the amplifier or ADC (analog to digital converter). Any voltages above or below the amplifier rails (or above/below the input range of the digitizer) will be ‘clipped’ and all we’ll see is a constant value.
The solution is to remove the large amplitude slow components, so we can fit the lower amplitude, faster, interesting components into our dynamic range.

.. image:: ../_static/images/EEA/eea_fig-54.png
  :align: center

Therefore, high-pass filters first remove the large DC offsets present at the electrode-extracellular interface, along with any undesired low-frequency signals (e.g., movement artefacts). Additionally, low-pass filters must be configured to less than half of the ADC frequency sampling rate (Nyquist limit) to prevent aliasing, and may also be used to block undesired high-frequency signals and artefacts. For instance, if our sampling frequency is 30 kHz, the low pass filter should be ~15 kHz. Below is an example of the Intan headstage circuit.

.. image:: ../_static/images/EEA/eea_fig-55.png
  :align: center

Low-pass filters
***********************************
These filters block high frequencies. This is basically another voltage divider, with a frequency-dependent component. You’ve already seen one of these when you charged/discharged a capacitor! The exponential decay of the capacitor gets convolved with our signal. Remember that the impedance of our capacitor decreases as the signal frequency increases. At low frequencies, the high impedance of the capacitor means we get a large voltage drop over the capacitor, and more of our input signal can reach our Vout.

.. image:: ../_static/images/EEA/eea_fig-56.png
  :align: center
  :scale: 60
  :target: https://www.falstad.com/circuit/e-filt-lopass.html


High-pass filters
***********************************
This is the same `idea. <https://www.falstad.com/circuit/e-filt-hipass.html>`_
With increasing signal frequency, the impedance of the capacitor decreases (day 1), reducing the voltage drop over the capacitor and sending more signal to the output.

.. image:: ../_static/images/EEA/eea_fig-57.png
  :align: center
  :scale: 70
  :target: https://www.falstad.com/circuit/e-filt-hipass.html

These are called ‘RC filters’ because they’re built from a resistor (R) and a capacitor (C). Because there's only one of each, we call them ‘single pole’. In real life, filters are built from more than one pair in order to get specific characteristics. This goes beyond the scope of this course but there are entire classes on this topic.
