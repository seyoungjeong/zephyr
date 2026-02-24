:orphan:

.. _mec172x_rom_api_sample:

MEC172x ROM API
###############

Overview
********

This sample demonstrates the use of the MEC172x ROM API for hardware-
accelerated cryptographic hash computations via the Zephyr crypto API.
It verifies SHA-224, SHA-256, SHA-384, and SHA-512 hash operations using
known test vectors with multiple message sizes (37, 185, and 238 bytes).

The sample tests:

* Multi-block hash computation with block-aligned updates plus remainder
* Arbitrary chunk-size hash computation (0, 8, and 23 byte chunks)
* Digest comparison against pre-computed expected values

Requirements
************

* Microchip MEC172x EVB (``mec172xevb_assy6906``)

Building and Running
********************

.. zephyr-app-commands::
   :zephyr-app: samples/boards/microchip/mec172xevb_assy6906/rom_api
   :board: mec172xevb_assy6906
   :goals: build flash
   :compact:

Sample Output
*************

.. code-block:: console

   It lives! mec172xevb_assy6906
   ROM API say GIVE MEMORY, MORE MEMORY!
   ...
   Test Zephyr crypto hash API for multiblock plus remainder
   SHA-224
   Hash computation PASS
   ...
   Application done
