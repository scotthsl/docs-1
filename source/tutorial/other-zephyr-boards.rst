.. _tutorial-basic-other-zephyr:

Using Other Zephyr Boards
=========================

.. warning:: Content in this section is provided on a best-effort basis.

This document contains additional information related to using the
system on other boards.

FRDM-K64F
---------

.. toggle-header::
   :header: Click to show/hide

   .. include:: pyocd.include

   .. |frdm-k64f-net-file| replace::
      ``zmp-samples/dm-lwm2m/boards/frdm_k64f-local.conf``

   .. include:: frdm-k64f-net.include

   In addition, |frdm-k64f-net-file| must contain a line which specifies
   the IP address of the COAP proxy. In this case, that's just the IP
   address of your gateway device. To use IP address L.M.N.O, add a line
   like this after the other networking configuration:

   .. code-block:: kconfig

      CONFIG_LWM2M_FIRMWARE_UPDATE_PULL_COAP_PROXY_ADDR="L.M.N.O"

   To build and flash::

     west build -s zmp-samples/dm-lwm2m -d build-dm-lwm2m -b frdm_k64f
     west sign -t imgtool -d build-dm-lwm2m -- --key mcuboot/root-rsa-2048.pem
     west flash -d build-dm-lwm2m --hex-file zephyr.signed.hex

96Boards Nitrogen
-----------------

.. toggle-header::
   :header: Click to show/hide

   .. include:: pyocd.include

   To build and flash::

     west build -s zmp-samples/dm-lwm2m -d build-dm-lwm2m -b 96b_nitrogen
     west sign -t imgtool -d build-dm-lwm2m -- --key mcuboot/root-rsa-2048.pem
     west flash -d build-dm-lwm2m --hex-file zephyr.signed.hex

BLE Nano 2
----------

.. toggle-header::
   :header: Click to show/hide

   .. include:: pyocd.include

   To build and flash::

     west build -s zmp-samples/dm-lwm2m -d build-dm-lwm2m -b nrf52_blenano2
     west sign -t imgtool -d build-dm-lwm2m -- --key mcuboot/root-rsa-2048.pem
     west flash -d build-dm-lwm2m --hex-file zephyr.signed.hex
