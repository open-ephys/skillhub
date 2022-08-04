.. _refground:

***********************************
Ground and Reference Pins
***********************************
.. raw:: html

    <br>
    <center><iframe width="560" height="340" src="https://www.youtube.com/embed/YE2cdXtzlF4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
    </center>
    <br>

What is a reference pin/electrode?
###################################
The world around us is, electrically, very noisy, and we are surrounded by large differences in electric potential. Just walking across a carpet can charge you to 10kV, and different surfaces or objects can easily be at different potentials to each other.

To detect 1mV spikes in this environment, electrophysiology hardware uses amplifiers. See the dedicated page to find out more. In brief, an amplifier has two inputs, a '+' and a '-' , and will output the difference between the two.

.. image:: ../_static/images/subtract_ref.png
  :align: center

To get this result, the '+' pin must contain the signal of interest. The '-' pin must be connected to something that shares only noise with the '+' pin, but none of the real signal (or we will end up subtracting that out).

This could be:

- A 'ground' pin or screw. This is a low-impedance route that will pick up local noise, but not specific activity such as spiking.
- A reference electrode in/on the brain. This electrode will detect the local activity, just like the measurement electrode does. Be aware that spikes detected on a reference electrode will show up as inverted spikes on the recording.


.. image:: ../_static/images/ref_spikes.png
  :align: center


What happens if the reference pin is not connected to anything? It will be 'floating' and picking up the random oscillations in the air, and subtracting this from the neuronal signal. This will look incredibly noisy.

What is the ground pin on a headstage?
###########################################
Amplifiers can only provide as much voltage as their voltage rails allow. If the difference between the two inputs of the amplifier (multiplied by the amplifier gain) is higher than their voltage rails, the amplifier will saturate and only output a high (or low) voltage value. The amplifier is (eventually, through a bunch of components) connected to ground, it will be comparing the input to this 0V. The signal measured in the brain could easily sit several kV higher than ground, and the amplifier will not be able to handle this huge difference in potential. If the voltage rails are 3V, and the amplifier has a 100x gain, even a 0.03V input will :ref:`saturate<saturation>` the amplifier.

A ground pin has very low impedance, which means it can source or sink a lot of current. It will bring anything it is connected to, close to 0 volt. Implanting a screw or pin in the skull, and connecting it through a low-impedance wire to the ground on the headstage, brings this screw/pin and therefore the entire animal closer to ground, at 0V. This can be the voltage that our computer considers ground, or the ground in the wall power sockets. This discharges the large voltage difference between the animal and the measuring setup, bringing it back to a range that the amplifier can cope with. We will still have remaining fluctuations, residual 50 or 60Hz noise from the mains supply, plus other muscles, electrostatic charge, bodies moving through the electric fields in the room and so on, but these can all be handled by the amplifier.

Additionally, :ref:`ground is not (always) earth <whatisearth>`, in many cases it is just a certain circuit we treat as 0. That circuit can have noise on it, just like any other circuit. If the ground you are using has a lot of 50/60Hz noise, it will be charging and discharging the animal (any animal is also a capacitor) constantly through the ground connection. If the ground screw/electrode is low enough impedance and close to our recording site, we’ll manage to keep the animal’s voltage equal to the changing GND level and we won't notice this noise. However, if we put the ground screw/electrode too far away from where we record, e.g. we put the ground connection on the tail (extreme example), then the head of the animal won’t be sufficiently charged/discharged and we’ll encounter what will look like 50/60Hz noise in our tetrode recordings.

When to connect ground and reference?
###########################################
In many ephys setups used for recording extracellular action potentials, you can short-circuit (connect with a wire) the REF and GND on the headstage. Your ground pin becomes your reference electrode AND draws the animal to ground. Action potentials are local signals and will not be detected by the ground pin.

However, this is not always appropriate. This is a choice that will depend on your setup and the signal you are interested in. In EEG and EMG, for instance, because these signals are detectable over much larger ranges, it is pretty much impossible to place an electrode at a point where it serves as a useful ground (i.e. detects the same noise as the measurement) but does not detect EEG signals. For these experiments, strict conventions are used regarding reference electrode placement.
