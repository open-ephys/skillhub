.. _refplating:

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
Plating Electrodes
***********************************

The very tips of tetrodes are often plated with a layer of gold, though other coatings can also be used. The goal is to decrease the impedance of the electrode (:ref:`why? <refwhyimpedance>`).

The capacitance of a capacitor, in Farads, is proportional to the area of the capacitor plates (A) divided by the distance (d) between them. ε is the electrostatic constant.

.. math::

  C = \frac{\epsilon}{A}

To make C bigger, we can increase A by increasing the surface area of the electrode, which is what happens when we gold-plate.

.. raw:: html

    <div class="d-flex col-lg-12 col-md-12 col-sm-12 col-xs-12 justify-content-right mx-auto" style = "max-width: 100%">
        <div class="card text-center intro-card border-white">
        <img src="../_static/images/sh_fig-7.png" class="card-img-top">
        </div>
    </div>

We can also coat electrodes with materials that are already complemented with pseudo-capacitance, such as conducting polymers or transition metal oxide films, e.g IrOx (Green, Lovell, Wallace, & Poole-Warren, 2008; Musa, 2011).

Electrode impedance magnitude is often measured at 1 kHz, before and after electrode coating, showing an impedance decrease up to 10-fold (Neto et al., 2018). By increasing the capacitance (|Ce|) of our electrode, the electrode impedance (|Ze|) will be smaller, preserving more of our signal amplitude at |Vin| (|Vin| = |Vec|). Electrodes impedance values are in the kOhm to MOhm range at 1 kHz.
