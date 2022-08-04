.. _refheadstages:

***********************************
Headstages
***********************************

.. toctree::
  :maxdepth: 2
  :glob:

  *

Electrodes, whether they are silicon probes or tetrodes, will almost always be attached to a headstage. Before the signal reaches the headstage, it is an analogue signal of very small amplitude that is directly powered by the brain or biological tissue. The headstage amplifies, filters, and digitizes this signal, and provides a new power source to propagate the signal through the rest of the acquisition system. It is therefore almost always best to have the headstage as close as possible to the electrode.

What headstages do
###################################

Amplify
***********************************
Headstage contain :ref:`Amplifiers`. These electronic components allow the headstage to perform several functions:

- The input to the amplifiers comes from the electrodes, which can only provide a very limited amount of current. The output from amplifiers is powered by an external voltage source (through the acquisition board), which can provide a lot of current. The amplifier creates a barrier between the electrodes and the rest of the acquisition system, and prevents current being drawn from the electrode/brain. Instead, the much larger voltage source of the headstage drives the rest of the acquisition circuit. For more information see our `ephys course <https://ahleighton.github.io/OE-ephys-course/>`_ which includes simulator exercises to test this idea.

-	Rejects common mode noise. The headstage compares the signal at a measurement electrode to a reference point, subtracting the reference signal. This gets rid of signal that the two points share ('common mode noise'). By choosing the reference wisely, this will reduce noise.

-	Finally, the amplifiers actually amplify; it increases the range of the signal to fit the dynamic range of our digitizer.

.. raw:: html

  <center><iframe width="560" height="340" src="https://www.youtube.com/embed/NP6nE5P82e8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></center>

Filter
***********************************
Most headstages will contain some filters to get rid of certain frequencies.

Digitize
***********************************
The analogue signal from the electrodes can take on any value in Volts. Digital signals are expressed in a binary format, taking on either value 0 or 1. In electronic circuits, this is expressed with two different voltage levels, for instance 1.2V represents 0, and 5V represents 1. Some noise in a digital circuit is therefore not such an issue; even if a noise signal increases the voltage on the 1.2V to 1.3 or 1.4, the circuit will not confuse it with 5V and will pass on the signal faithfully. Analogue signals are much more sensitive as any variation in voltage due to noise becomes indistinguishable from the desired signal.

Communicate with Acquisition Board
***************************************
In a typical acquisition system, the headstage is controlled by an acquisition board. The board will send commands to the headstage, requesting data from its channels, setting certain parameters, and providing it with power. The organisation of these commands is the data protocol that the two share. The Open Ephys Board uses an SPI protocol to allow the headstage and the acquisition board to communicate.
