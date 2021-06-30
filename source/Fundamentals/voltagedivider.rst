:notoc:

***********************************
Voltage Divider
***********************************

When we measure how much voltage is provided by a voltage source (such as a battery, microcontroller, or our neurons), we always measure it relative to a point that we consider 0V. In a circuit powered by a battery, we consider the negative terminal to be at 0V. If there is a connection to earth, or ground, this is taken as 0V.

Voltage (potential energy) ‘drops’ over each resistor, as potential energy is converted to another form of energy (such as heat or light). In a circuit powered by a 9V battery, all 9V of potential energy from our battery source *must* drop over circuit components, so that we end up back at 0V.

The higher the value of the resistor, the higher the voltage drop over it, but the total voltage drop over the circuit must equal the provided voltage.

.. image:: ../_static/images/EEA/eea_fig-18.png
  :align: center

That means that, in a circuit with multiple resistors in series, the ratio of their resistances determines how much voltage will drop over each. We can therefore split up (divide) the voltage from a source across resistors. If we measure the voltage in between these resistors as |Vout|:

.. math::

  |Vout| = |Vin| \frac{R1}{R1+R2}

.. note::
    Want to test your understanding? Try using a circuit simulator (here’s an empty full-screen https://tinyurl.com/y477e9qd) to build a voltage divider circuit in which you use a 3V battery and two resistors to provide an 800 mV output voltage |Vout|. Replace one of the resistors to make your output voltage as small as you can get it. What’s the smallest reading you can still pick up with your multimeter? How does this compare to the amplitude of a spike measured in the extracellular space?
