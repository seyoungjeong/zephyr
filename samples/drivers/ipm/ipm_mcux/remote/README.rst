:orphan:

.. _ipm_mcux_remote_sample:

IPM MCUX Mailbox (Remote Core)
##############################

Overview
********

This is the remote core component of the IPM MCUX mailbox sample. It runs
on the secondary processor (Cortex-M0+ or CPU1) and implements a simple
ping-pong message echo using the NXP LPC mailbox inter-processor
messaging (IPM) driver.

When the remote core receives a message from the primary core via the
mailbox interrupt, it echoes the same data back to the sender. This sample
is intended to be used together with the primary core application located
at ``samples/drivers/ipm/ipm_mcux``.

Requirements
************

* NXP LPCXpresso54114 (``lpcxpresso54114/lpc54114/m0``) or
  NXP LPCXpresso55S69 (``lpcxpresso55s69/lpc55s69/cpu1``)

Building
********

Build the remote core image first, then build the primary core application
which will automatically include the remote image.

.. zephyr-app-commands::
   :zephyr-app: samples/drivers/ipm/ipm_mcux/remote
   :board: lpcxpresso54114/lpc54114/m0
   :goals: build
   :compact:

See Also
********

* Primary core sample: ``samples/drivers/ipm/ipm_mcux``
