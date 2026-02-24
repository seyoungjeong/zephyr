:orphan:

.. _nrf_sys_event_sample:

nRF System Event
################

Overview
********

This sample demonstrates the nRF system event API (``nrf_sys_event``)
for managing power modes on Nordic Semiconductor SoCs. It exercises:

* Requesting and releasing global constant latency mode
* Reference counting verification (multiple request/release cycles)
* IRQ latency measurement with different RRAMC wake-up strategies
  (when ``CONFIG_NRF_SYS_EVENT_IRQ_LATENCY`` is enabled):

  * Default RRAMC mode (~15 µs wake-up time)
  * PPI-triggered RRAMC wake-up before expected interrupt
  * RRAMC standby mode (0 µs wake-up time)

Requirements
************

This sample requires a Nordic Semiconductor development kit. Supported
boards include nRF52, nRF5340, nRF54H20, nRF54L15, and nRF7120 series.
See ``sample.yaml`` for the full list of allowed platforms.

Building and Running
********************

.. zephyr-app-commands::
   :zephyr-app: samples/boards/nordic/nrf_sys_event
   :board: nrf52840dk/nrf52840
   :goals: build flash
   :compact:

To enable IRQ latency measurement with RRAMC wake-up testing:

.. code-block:: console

   west build -p always -b nrf54l15dk/nrf54l15/cpuapp -- \
       -DCONFIG_NRF_SYS_EVENT_IRQ_LATENCY=y

Sample Output
*************

.. code-block:: console

   request global constant latency mode
   constant latency mode enabled
   request global constant latency mode again
   release global constant latency mode
   constant latency mode will remain enabled
   release global constant latency mode again
   constant latency mode will be disabled
   constant latency mode disabled
