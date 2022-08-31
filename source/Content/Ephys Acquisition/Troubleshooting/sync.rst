.. _refsync:

***********************************
What is synchronization?
***********************************

One of the most common pitfalls in Neuroscience is correctly synchronizing multiple datastreams. How do you know whether your imaging and electrophysiology are aligned in time? How many different clocks do you have on your set up, and which of those can you trust?

Synchronization is important whenever an experiment involves more than one stream of data. This can be any type of data; electrophysiology and a behavioural camera, photometry with optogenetics, two cameras and a miniscope... The goal of synchronization is to know when in time each piece of data was acquired.

This is made tricky by:

- Clock differences; no two clocks will tell exactly the same time.

- Clock drift; any clock will have imperfections in telling time, that will accumulate the longer the experiment runs. Even on two identical devices, built from the same batch in the same factory, this clock drift will vary. That means that two identical devices started at exactly the same time can not be considered synchronized.

- Software clocks vs hardware clocks; Software clocks are more variable than hardware clocks- the idea that a PC has of 1 second can vary if it is busy doing other things. When synchronizing with millisecond precision, always use a hardware clock. Acquisition boards use hardware clocks, and pass this accurate timestamp on to the software.

When building a new setup, decide which hardware device will be in charge of timestamping. Then, send information about the other data streams to this device. Usually, the central clock will be your electrophysiology acquisition device, because it will have the highest acquisition frequency. By sending a signal to this clock every time a camera frame is acquired, or optogenetic stimulation is given, all your data will be timestamped on the same clock, and you will always know when in time an event occurred.


Talk: Acquisition and Synchronization
########################################

For an in-depth introduction to this topic, watch the lecture by OEPS founder Filipe Carvalho below. The code for the exercises Filipe shows is available `on google drive <https://drive.google.com/drive/folders/1Gw1QuXJKFy_i0V61b9DCHU8d6C0iIxHG?usp=sharing>`_ if you want to try it out yourself.

.. raw:: html

  <br>
  <center><iframe width="560" height="340" src="https://www.youtube.com/embed/F0uwA3RUlB0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></center>
  <br>
