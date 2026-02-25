.. zephyr:code-sample:: device_pm
   :name: Device Idle Power Management
   :relevant-api: pm_device pm_device_runtime

   Demonstrate device power management with a parent-child device hierarchy.

Overview
********

This sample demonstrates Zephyr's device power management subsystem using
a parent-child device hierarchy. Two dummy devices (a parent bus device and
a child peripheral device) are defined with PM action callbacks that handle
:c:enumerator:`PM_DEVICE_ACTION_SUSPEND` and
:c:enumerator:`PM_DEVICE_ACTION_RESUME` transitions.

The application performs the following sequence:

#. The child device is opened, which resumes the parent first via
   :c:func:`pm_device_runtime_get`, then resumes itself.
#. A write and read operation is performed through the parent bus.
#. The child device is closed, which suspends both the child and parent
   via :c:func:`pm_device_runtime_put`.

This sample shows how to:

* Define PM-enabled devices using :c:macro:`PM_DEVICE_DEFINE`.
* Use :c:func:`pm_device_runtime_enable` to enable runtime PM for a device.
* Manage device power state with :c:func:`pm_device_runtime_get` and
  :c:func:`pm_device_runtime_put`.
* Query a device's power state using :c:func:`pm_device_state_get`.
* Coordinate parent-child device power dependencies.

Requirements
************

This sample does not require any special hardware and can be run on QEMU
or any board that supports the device power management subsystem
(:kconfig:option:`CONFIG_PM_DEVICE`).

Building and Running
********************

Build and run the sample as follows, changing ``qemu_x86`` for your board:

.. zephyr-app-commands::
   :zephyr-app: samples/subsys/pm/device_pm
   :host-os: unix
   :board: qemu_x86
   :goals: build run
   :compact:

Sample Output
=============

When the sample runs successfully, the following output is displayed on the
console:

.. code-block:: console

   parent suspending..
   child suspending..
   *** Booting Zephyr OS build zephyr-vX.Y.Z ***
   Device PM sample app start
   parent resuming..
   child resuming..
   Dummy device resumed
   child suspending..
   parent suspending..
   Device PM sample app complete

The initial ``parent suspending..`` and ``child suspending..`` messages appear
because both devices start in an active state and are immediately suspended
when runtime PM is enabled during device initialization. The application then
resumes them, performs I/O, and suspends them again upon closing.

Exit QEMU by pressing :kbd:`CTRL+A` :kbd:`x`.

References
**********

* :ref:`Device Runtime Power Management <pm-device-runtime-pm>`
