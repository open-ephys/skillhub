***********************************
Connectors and Cables
***********************************

Many different types of connections are used to physically link neuroscience hardware devices, and it gets confusing pretty quickly; there is almost no consistency in the names used to describe them, other than that they are often obscure initialisms. Sometimes the connector is described by brand (e.g. 'Omnetics','Hirose'), function (e.g. 'SPI', 'USB'), some physical property ('a 50 Ohm cable') or creator ('BNC').

Describing a Connection
###################################
Every connection between devices on a setup will actually have:

1) Physical characteristics
-------------------------------
These include properties like the shape of the connector, the resistance of the wire, and the number of lines running through the cable.

Cable types
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
There are main two types of cable used:

  - Twisted wire cables

  .. image:: ../../../_static/images/Basics/twisted_wires.png

  - Coaxial cables

  In coaxial cables, the ground of the cable surrounds a central line. This provides a degree of shielding which protects the inner wire from noise. Coaxial cables are often described with an impedance value, e.g. 'a 50 Ohm cable' (see `here <https://www.allaboutcircuits.com/textbook/alternating-current/chpt-14/50-ohm-cable/>`_ for more info on what 50 Ohms means in this context). A BNC connector is coaxial, as are SMA connectors.

Connector types
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
See our library below!

2) Data transmission
-------------------------------

The same physical connection can transmit different kinds of data. For two devices to be able to communicate, they need to use the same interface specification. This specification describes the data organisation that the devices on both sides of the cable/connector expect to see.

Examples of data protocols are SPI (Serial Peripheral Interface, used between Intan headstages and the acquisition Board) or ONI (Open Neuro Interface, specifications for high-bandwidth).

The same physical connection can be used to send different types or arrangements of data. For example, take the HDMI cable, commonly used to transmit uncompressed video and audio, such as when you connect your laptop to an external screen. The physical HMDI cable is a twisted-wire cable with two HDMI connectors. Usually, when two devices can be connected with an HDMI cable, they implement the EIA/CEA-861 protocol, which is a format that describes how data transfer between the devices should look. Though it is technically an HDMI connection implementing a EIA/CEA-861 data format, the two usually go hand-in-hand. However, a different data protocol could be used over the same cable. For instance, the Open Ephys Acquisition Board uses an HDMI cable to link an input/output board to the main acquisition device. That link uses a different data protocol, suitable for the type of data the board is designed to receive.


3) Brand
-----------------------------
The most straightforward; the company that has produced this particular product. Due to patents or just fame, company names can become intrinsically linked with types of connectors.


Connector Library
###################################

12-pin Omnetics PZN-12 polarized nano connectors.

Omnetics

BNC

SPI

SMA

MCXX SMA

USB

HMDI
