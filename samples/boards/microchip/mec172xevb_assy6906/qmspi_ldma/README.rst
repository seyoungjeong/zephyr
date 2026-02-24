:orphan:

.. _mec172x_qmspi_ldma_sample:

MEC172x QMSPI LDMA
###################

Overview
********

This sample demonstrates the Quad-SPI (QMSPI) interface with Local DMA (LDMA)
on the Microchip MEC172x EVB (``mec172xevb_assy6906``). It exercises SPI flash
operations using the Zephyr SPI API, including:

* Reading the JEDEC ID (W25Q128, W25Q128JV, or SST26VF016B)
* Reading and writing SPI flash status registers
* Erasing sectors and programming pages
* Reading data in multiple modes: slow (1-1-1-0), fast (1-1-1-8),
  dual (1-1-2-8), and quad (1-1-4-8)
* Asynchronous SPI read (when ``CONFIG_SPI_ASYNC`` is enabled)
* Data integrity verification after erase, program, and read cycles

Requirements
************

* Microchip MEC172x EVB (``mec172xevb_assy6906``)
* SPI flash device connected to QSPI0 (W25Q128, W25Q128JV, or SST26VF016B)

Building and Running
********************

.. zephyr-app-commands::
   :zephyr-app: samples/boards/microchip/mec172xevb_assy6906/qmspi_ldma
   :board: mec172xevb_assy6906
   :goals: build flash
   :compact:

Sample Output
*************

.. code-block:: console

   JEDEC ID = 0x001840ef
   W25Q128 16Mbyte SPI flash
   SPI Flash Status1 = 0x00
   SPI Flash Status2 = 0x02
   Quad-Enable bit is set. WP# and HOLD# are IO[2] and IO[3]
   ...
   Data matches
   Program End
