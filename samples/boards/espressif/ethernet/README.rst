:orphan:

.. _esp32_ethernet_sample:

ESP32 Ethernet
##############

Overview
********

This sample demonstrates how to use the Ethernet interface on the ESP32
Ethernet Kit. It initializes the Ethernet driver with DHCP for automatic
IPv4 address assignment, enables the network shell for interactive
debugging, and configures DNS resolution with Google's public DNS server
(8.8.8.8).

The sample enables the following features:

* ESP32 Ethernet driver (``CONFIG_ETH_ESP32``)
* IPv4 with DHCPv4 for automatic address configuration
* DNS resolver for hostname lookups
* Network shell for interactive network diagnostics (``ping``, ``dns``, etc.)

Requirements
************

This sample requires the
`ESP32 Ethernet Kit <https://docs.espressif.com/projects/esp-idf/en/latest/esp32/hw-reference/esp32/get-started-ethernet-kit.html>`_
board with an integrated Ethernet PHY.

Building and Running
********************

.. zephyr-app-commands::
   :zephyr-app: samples/boards/espressif/ethernet
   :board: esp32_ethernet_kit/esp32/procpu
   :goals: build flash
   :compact:

After flashing, the device will attempt to obtain an IPv4 address via DHCP.
Use the network shell to verify connectivity:

.. code-block:: console

   uart:~$ net iface
   uart:~$ net ping 8.8.8.8
   uart:~$ net dns resolve google.com
