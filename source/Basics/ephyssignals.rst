.. _refephyssignals:

.. |Ve| replace:: V\ :sub:`e`\
.. |Ce| replace:: C\ :sub:`e`\
.. |Rm| replace:: R\ :sub:`m`\
.. |Re| replace:: R\ :sub:`e`\
.. |Cs| replace:: C\ :sub:`s`\
.. |Vin| replace:: V\ :sub:`in`\
.. |Vec| replace:: V\ :sub:`ec`\
.. |Vout| replace:: V\ :sub:`out`\
.. |Na+| replace:: Na\ :sup:`+`\
.. |K+| replace:: K\ :sup:`+`\
.. |Ca2+| replace:: Ca\ :sup:`2+`\
.. |Cl-| replace:: Cl\ :sup:`-`\

***********************************
Electrophysiology: Signals
***********************************

Electrophysiologists measure biologically generated electrical signals. The source of these signals will depend on the scientific or medical question;  signals can be recorded from various tissues (e.g. the brain, heart, muscles) and different cells (excitatory, inhibitory). Sometimes we are interested in the activity of a single neuron, and sometimes in the combined activity of large populations of cells. See `here <refephysmethods>`_ for an overview of different methods of electrophysiology.

What do they have in common?

1) Unit: Signals are measured in Volts: they are therefore measurements of `electric potential difference <refepot>`_. Changes in electric potential difference are mediated by `charged particles <refchargedparticles>`_, usually ions. These ions can cross cell membranes, both into and out of cells.
2) Size: Signals are measured in micro or millivolts: they are very small signals, and we need to take this into account when building or choosing acquisition systems.

What are we measuring?
=====================================
When we perform extracellular recordings, we are measuring changes in the electric potential difference between the tip of our electrode and a point we have chosen as ground (and therefore 0V). These changes are caused by the current flows and membrane potential changes of cellular activity.

The Membrane Potential
***************************************
Neuronal activity relies mainly on ions such as |Na+|, |K+|, |Ca2+| and |Cl-|. Whenever these charges flow across the cell membrane, we have a **current**. In neurons, our **resistance** to current flow is formed by the permeability of the cell membrane to our ion, which can be changed by opening or closing ion channels in the membrane. When more channels open, the resistance to a certain ion is lowered, and more current able to flow in or out of the cell. For current to flow, the ion must experience a net **driving force** in a certain direction.

What kind of driving forces can cause current flow?
1. Concentration gradient
Ions will tend to diffuse away from areas where there is a high concentration of that ion, to areas with a lower concentration.
2. Electrical force
Depending on their charge, ions will be attracted to or repelled by other charged particles. Positive charges will move towards areas of more negative `electric potential <refepot>`_. This follows `Ohm's Law <refresistance>`_.

The **membrane potential** is the difference in electric potential between the inside of the cell membrane and the extracellular fluid. A neuron typically has a resting membrane potential of around -70 mV compared to the extracellular fluid (set at 0V).

The interaction of the concentration and electrical driving forces is described in the electrochemical gradient of the ion. This balance is summarised by the Nernst equation. Please read `Wright 2004 <https://journals.physiology.org/doi/pdf/10.1152/advan.00029.200>`_ for a clear refresher on this, and to understand how the -70mV membrane potential is maintained by the cell.

Changes in Membrane Potential
=====================================
When ions cross the membrane, the charge distribution across the membrane changes, which can increase or decrease the membrane potential. When positive ions enter the cell, this decreases the electric potential difference over the membrane, *de-polarising* the membrane. Positive ions leaving the cell can *re-polarise* the membrane back to its resting potential.
Changes in membrane potential happen when the cell receives inputs and when the cell fires an action potential.

Neuronal output: Action Potentials
=====================================
When a neurotransmitter binds to a postsynaptic receptor, specific ion channels can open, locally reducing the membrane resistance to that ion and allowing a current to flow. Often, these are |Na+| or |Ca2+| channels. |Na+| can then follow its concentration and electrical gradient from outside the cell, where the |Na+| concentration is high, to the inside of the cell, where |Na+| concentration is low and the intracellular medium has a lower electric potential (Kandel, Schwartz, & Jessel, 2000).

Sufficient depolarisation can open voltage-sensitive |Na+| channels, which trigger further depolarisation and channel opening, causing the membrane potential of the cell to increase rapidly. These membrane potential deflections occur in a stereotypical pattern called the action potential. In neurons, voltage-sensitive |Na+| channels are concentrated at the initial segment of the axon, and it is therefore more likely that an action potential will be generated there rather than in other regions of the cell. The closing of |Na+| channels and opening of |K+| channels begins the process of returning the membrane potential to resting conditions (Hodgkin and Huxley, 1939).

Action potentials can be detected in the extracellular space. Action potentials usually last on the order of 1-2 ms, and are in the range of tens to hundreds of microvolts in amplitude, with the largest potential deflections being detected close to the soma of a neuron.
The figure below illustrates how the shape of the action potential depends on the location of the electrode relative to the cell. The left column shows the Ve (voltage at the electrode) at three different locations. As seen from inside the cell, an action potential is always identical. However, seen from outside the cell, the shape of the action potential will vary depending on the location of the electrode. The main peak of the action potential can even be upward or downward.

The shape of the voltage trace depends on the relative strength of three primary currents (Gold et al., 2006):

1) The capacitive current of |Na+|. The membrane is a capacitor. As the membrane potential decreases, the membrane can separate less charge and |Na+| ions, previously aligned along the membrane, are released. These positive ions flow towards the electrode, causing a positive, upward deflection. (No idea what this means? Read up on `capacitive currents here. <refcapcurrents>`_).
2) |Na+| current enters the axon. These are positive charges flowing away from the electrode, and appear as a negative deflection, strongest near the axon initial segment where the concentration of voltage-dependent |Na+| channels is highest.
3) The repolarizing |K+| current flowing out of the cell.

.. image:: ../_static/images/sh_fig-42.png
  :align: center

.. raw:: html

  <center><h5 class="card-title" >Figure 4: Electric potential generated by current sources in a conductive volume.
    <p style="font-size:12px">  Electric potential generated by current sources in a conductive volume. The extracellular potentials and currents are adapted from Gold et al., 2006. The shape of the extracellular potential waveforms at various spatial positions 're' (marked with black dots) are simulated for a CA1 pyramidal neuron.
    Currents: simulated net membrane current (first column) across the soma and proximal dendrites that best estimates the extracellular potential waveform and membrane current components in terms of Na+, K+ and capacitive currents (second column). In the soma, the positive capacitive current coincides with the larger Na+ current. At locations along the apical trunk, the initial capacitive peak becomes visible. In dendritic compartments the membrane depolarization is initially driven by Na+ current from the soma, until local Na+ currents are activated and the action potential regenerates. In the brief time before the local Na+ currents activate, the positive capacitive current is the dominant membrane current and a capacitive-dominant phase is visible in the net current (Gold et al., 2006).</p></h5></center>


Neuronal input: Postsynaptic potentials
============================================
When synapses are activated, the opening of channels can cause a local change in membrane potential: the postsynaptic potential. Just like action potentials, postsynsaptic potentials can be picked up by an extracellular electrode. These are slower than the action potential, occurring over 10s of milliseconds rather than the 1-2 ms of the action potential. Because postsynaptic potentials last longer, there is more opportunity for signals from multiple cells to summate and result in larger signals, such as those measured with EEG.
If using an extracellular electrode, the signal can be filtered to either focus on high-frequency action potentials or lower-frequency summed synaptic inputs.

The extracellular space
============================================
In the practical exercises for this course, we will be using electrodes attached to the skin. In animal models, we often use electrodes in the extracellular space. To keep things simple, most text book cartoons will draw neurons in the brain with a few synapses and lots of extracellular space in between each cell. If we were to stain all the dendrites and axons from every neuron in a slice of brain tissue, the result would be a solid black picture. A rat brain has about 200 million (and a human brain has about 86 billion) neurons tightly packed together (Herculano-Houzel, 2009). The density in the rat cortex is between 40,000 to 100,000 neurons per mm3 (Defelipe et al., 2002; Markram et al., 2015; Meyer and Moser, 2010). In addition to neuronal cell bodies, axonal fibres, and dendritic structures, the brain also contains glial cells and blood vessels. Very little of the extracellular space is actually “space”; indeed, extracellular fluid is thought to comprise only 12–25 % of the brain’s volume (Nelson et al., 2013; Tønnesen, Inavalli, & Nägerl, 2018). The potential Vec induced by the transmembrane currents depends on the magnitude, sign and location of the current sources, and on the conductivity of the extracellular medium (Buzsaki et al., 2012; Nunez and Srinivasan, 2006).
