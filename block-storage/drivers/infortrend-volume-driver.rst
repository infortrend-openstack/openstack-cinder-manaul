========================
Infortrend volume driver
========================

The `Infortrend <http://www.infortrend.com/global>`__ volume driver is a Block Storage driver
providing iSCSI and Fibre Channel support for Infortrend storages.


Supported operations
~~~~~~~~~~~~~~~~~~~~

The Infortrend volume driver supports the following volume operations:

* Create, delete, attach, and detach volumes.

* Create and delete a snapshot.

* Create a volume from a snapshot.

* Copy an image to a volume.

* Copy a volume to an image.

* Clone a volume.

* Extend a volume

* Retype a volume.

* Manage and unmanage a volume.

* Migrate a volume with back-end assistance.

* Live migrate an instance with volumes hosted on an Infortrend backend.


System requirements
~~~~~~~~~~~~~~~~~~~

To use the Infortrend volume driver, the followings are required:

Set up Infortrend storage
-------------------------
* Create logical volumes in advance.

* Array setting ``Peripheral device type`` should be ``No Device Present (Type=0x7f)``.

Set up cinder-volume node
-------------------------
* Install Oracle Java 7 or later.

* Download the Infortrend storage CLI from our
  `release page <https://github.com/infortrend-openstack/infortrend-cinder-driver/releases>`__.


Driver configuration
~~~~~~~~~~~~~~~~~~~~

On cinder-volume nodes, set the ``/etc/cinder/cinder.conf`` configuration file, and follow below
examples, replacing the variables to fit your requirements:


iSCSI configuration example
---------------------------

.. code-block:: ini

   [DEFAULT]
   default_volume_type = IFT-ISCSI
   enabled_backends = IFT-ISCSI

   [IFT-ISCSI]
   volume_driver = cinder.volume.drivers.infortrend.infortrend_iscsi_cli.InfortrendCLIISCSIDriver
   volume_backend_name = IFT-ISCSI
   infortrend_pools_name = POOL-1,POOL-2
   san_ip = MANAGEMENT_PORT_IP
   infortrend_slots_a_channels_id = 0,1,2,3
   infortrend_slots_b_channels_id = 0,1,2,3


Fibre channel configuration
---------------------------

.. code-block:: ini

   [DEFAULT]
   default_volume_type = IFT-FC
   enabled_backends = IFT-FC

   [IFT-FC]
   volume_driver = cinder.volume.drivers.infortrend.infortrend_fc_cli.InfortrendCLIFCDriver
   volume_backend_name = IFT-FC
   infortrend_pools_name = POOL-1,POOL-2,POOL-3
   san_ip = MANAGEMENT_PORT_IP
   infortrend_slots_a_channels_id = 4,5


Configuration parameters
------------------------



Extra spec setting
~~~~~~~~~~~~~~~~~~


For more detailed, see `Infortrend documents <http://www.infortrend.com/ImageLoader/LoadDoc/715/True/True/Infortrend%20document>`_.

