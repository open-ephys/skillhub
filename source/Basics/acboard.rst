.. _refacboard:

***********************************
Acquisition Boards
***********************************

What do acquisition boards do
###################################



What is inside
###################################

The heart of the Open Ephys Acquisition Board is an FPGA (Field Programmable Gate Array).

.. image:: ../_static/images/Basics/ac_board_inside.png

Acquiring with high channel counts at high sampling speeds places heavy requirements on the hardware of the acquisition system. An acquisition system must be able to drive analog-to-digital converters and sensors, pack data and send it to a computer with very strict timing constraints.

Classical, sequential MicroController Units can only execute one command at a time. Performing multiple, synchronized actions can therefore only be approximated by running steps sequentially at high speed. This processor speed is limited by power and thermal considerations (S. H. Fuller and L. I. Millett, 2011).
Parallel computing allows separate and simultaneous acquisition, packing and transmission of data from each sensor.  Various devices are able to perform parallel operations, but are otherwise unsuitable for electrophysiology acquisition. Multicore processors lack enough parallelism, as they can only perform one simultaneous action per core. GPUs can run hundreds of parallel operations, but while they are widely used for processing they
lack the hardware resources needed for driving sensors. Application-Specific Integrated Circuits (ASICs) are custom hardware devices created for a specific task, so they can achieve the desired parallelism with very high performance.
However, they lack flexibility; once produced, and change requires a new fabrication batch.
Field-Programmable Gate Arrays (FPGAs) are integrated circuits featuring configurable digital electronics. By uploading a configuration file called a 'bit file', FPGAs can be configured to act as any digital circuit. The circuits configured into an FPGA can run in parallel and independently, unlike microprocessors which run a single programme step-by-step.

offer the parallel capabilities of an ASIC, albeit with slightly reduced performance, but with the ability of being reconfigured at no cost. `Sparkfun has an excellent introduction on FPGAs <https://learn.sparkfun.com/tutorials/how-does-an-fpga-work?_ga=2.78097236.1328161175.1645203335-838473938.1635861406>`_.

*Adapted from the PhD Thesis of Aarón Cuevas*


S. H. Fuller and L. I. Millett, Computing performance: Game over or next level? Computer, vol. 44, pp. 3138, Jan. 2011. doi: 10.1109/MC.
2011.15
