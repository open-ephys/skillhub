:notoc:

***********************************
Electrodes
***********************************

Getting from `neuronal activity <_refepotential>`_ (Vec) to the input to the recording system (Vin) relies first on the interface between the electrode and the extracellular space. Extracellular microelectrodes are usually made from metallic conductors. A thin insulated metal wire with an exposed tip is the most basic, and still widely used, device for in vivo extracellular recording from brains. Twisting four such wires gives you a `tetrode <_reftetrodeintro>`_. Metals such as platinum, gold, tungsten, iridium, titanium nitride, stainless steel, iridium, iridium oxide, and alloys, nickel-chrome, platinum-iridium and platinum-tungsten have all been used in neural electrodes.

.. image:: ../_static/images/EEA/eea_fig-7.png
  :align: center

.. raw:: html

  <center><i> Figure 7: The double layer interface between an electrode and the extracellular fluid.</i></center>

This transition from ion flow in the extracellular space (neural activity) to electron (electrode) flow is made through the double layer interface. When a metal is placed in a saline solution two phenomena occur: water dipoles close to the metal surface become oriented, and assuming the metal surface is negatively charged, the solution close to the metal surface become depleted of negative ions (anions), leaving behind a cloud of positive ions (cations). This cloud of cations screens the electric field caused by the excess of charge on the metal. Electroneutrality across the interface requires that the charge on the metal is always equal and opposite to the total charge on the solution side of the interface (Musa et al., 2012). The resulting charge distribution - two narrow regions of equal and opposite charge - is known as the electrical double layer (EDL). Figure 10 shows a model for the distribution of electric potential across a metal-solution interface, where the double layer region (represented in pink in the schematics) yields a capacitance Ce which typically has a value around 20 μF cm-2 (Musa, 2011).

The signal transduction takes place across the electrode-extracellular space when the charge distribution changes on the extracellular fluid side. The electric potential variation in the extracellular space is accompanied by a redistribution of the ion concentration close to the metal electrode, and hence, changes in the electrode’s charges.

How does the electrode detect Vec?
***********************************
Neuronal membranes have resistance- they are resistors. They also have capacitance, just as anything that is made up of two conducting layers, separated by a non-conducting layer, will have capacitance. We can extract the electrical behaviour of neural membranes and electrodes by making an ‘equivalent circuit’, which describes their electrical properties.


.. image:: ../_static/images/EEA/eea_fig-8.png
  :align: center

.. raw:: html

  <center><i> Figure 8: The equivalent circuit describes the electrical properties of the double-layer interface between electrode and extracellular fluid.</i></center>

In the above figure, the interface between the solution and the electrode is represented by a parallel ReCe combination in series with resistances Rm (metal) and Rs (solution).
•	Re represents leakage resistance; the charge transfer due to charge carriers crossing the electrical double layer.
•	Ce is the capacitance of the electrical double layer at the interface of the exposed metal and the solution.
Usually Re and Rs are small. For example, a tungsten microelectrode as the one used by Hubel and Wiesel in the 1950’s and 60’ has a value for Rm ~ 10 to 100 Ohm
(Rm= (resistivity x length)/ cross sectional area), a Ce ~ 0.2 pF / um2 ~ 10 - 20 pF (unplated) and Re ~ 10 to 100 MOhm. This microelectrode is considered a ‘polarized’ electrode.
There are two general types of electrode, ‘non-polarised’ and ‘polarized’. Each has a different mechanism through which ion flow in the solution leads to electron flow in the electrode.

Non-polarized electrodes
***********************************
The well-known silver-silver chloride (Ag-AgCl) electrode approaches the ideal nonpolarizable type. In these ‘charge transfer’ electrodes, surface-confined species are oxidized and reduced (Bard & Faulkner, 2001, Merrill et al., 2005).
Non-polarizable electrodes have a small Re, allowing charge-transfer across the electrode-solution interface. If Re is small, it bypasses the capacitor Ce, thus providing a DC path for the measurement of steady potential levels.

Polarized electrodes
***********************************
Alternatively, the transition from ion flow in the solution to electron flow in the electrode could be of capacitive nature, involving the charging and discharging of the electrode-solution double layer. This happens with noble metal (e.g., stainless steel, gold and platinum) electrodes, where no charge transfer can occur across the metal-solution interface. Instead, electrode polarization is required to motivate current flow in the external recording circuit. In metals, such as aluminium and copper, charge transfer occurs and causes metal’s deterioration (i.e., oxidation).
The value of Re of polarized electrodes is large, in the order of several megohms, and the effective equivalent circuit is dominated by the capacitor, Ce. Therefore, processes in polarizable electrodes are purely electrostatic and caused by the charging and discharging of the double layer capacitance. Although charge does not cross the interface, external currents can flow when the potential or solution composition changes (Cooper, 1971).
