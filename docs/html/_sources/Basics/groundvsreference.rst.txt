.. _refground:

***********************************
Ground vs Reference
***********************************

What is the ground pin/electrode?
###################################

`Start with Jakob Voigts' talk about Ground vs Reference. <https://www.youtube.com/watch?v=YE2cdXtzlF4>`_



`Headstages <headstage>`_ contain instrumentation amplifiers, that can subtract the signal of the reference electrode (-) from our measurement electrode (+). This should get rid of the common mode that the signals share. However, if the difference between the - and + inputs becomes too large, the amplifiers will saturate- they won't be able to provide the required output voltage.

The world around us is, electrically, very noisy, and we are surrounded by large differences in electric potential. Just walking across a carpet can charge you to 10kV. The ‘-’ inputs of the two input operational amplifiers (op-amps) are connected to ground, via a bunch of resistors. If your mouse is charged to 10kV compared to ground, we’re asking these op-amps to deal with pretty high values individually, and they will saturate. Each op-amp can only go as high or low as its voltage rails (say the voltage rails are 3V, so with a 100x gain, a 0.03V input will saturate the amplifier).

.. figure:: ../_static/images/eea_fig-53.png
    :scale: 80
    :align: center
    :target: https://tinyurl.com/yjxekrv5

A ground pin or wire has very low impedance- it can source or sink as much current as necessary. It will bring anything it is connected to, close to 0 volt. We use the ground pin/electrode to first bring the mouse/our body to a reasonable voltage level - for example the voltage that our computer considers ground, or the ground in the wall power sockets. Once we’ve done that, our entire body is not floating at 10kV anymore but at 0V. We will still have remaining fluctuations, residual 50 or 60Hz noise from the mains supply, plus other muscles, electrostatic charge, bodies moving through the fields in the room and so on, but these can all be handled by the amplifier.

One more detail: ground is not (always) earth, in many cases it is just a certain circuit we treat as 0. That circuit can have noise on it, just like any other circuit. If the ground you are using has a lot of 50/60Hz noise, we’ll be charging and discharging the animal (any animal is also a capacitor) constantly through the ground connection. If the ground screw/electrode is low enough impedance and close to our recording site, we’ll manage to keep the animal’s voltage equal to the changing GND level and we won't notice this noise. However, if we put the ground screw/electrode too far away from where we record, e.g. we put the ground connection on the tail (extreme example), then the head of the animal won’t be sufficiently charged/discharged and we’ll encounter what will look like 50/60Hz noise in our tetrode recordings.
