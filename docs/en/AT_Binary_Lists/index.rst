AT Binary Lists
=================

:link_to_translation:`zh_CN:[中文]`

.. toctree::
  :hidden:
  :maxdepth: 1

  {IDF_TARGET_NAME} AT Released Firmware <esp_at_binaries>

This document covers the following sections:

.. list::

  - :doc:`Download {IDF_TARGET_NAME} AT Released Firmware <esp_at_binaries>`
  - :ref:`brief-intro-firmware`: What binary files the AT firmware contains and their functions.

.. note::
  To download AT firmware for other chip series, please go to the drop-down list on the upper left corner of this page and select a chip series to navigate to the documentation of that chip for downloading.

  Currently, there is no AT firmware available for the ESP32-H series, ESP32-P series, and ESP32-S3 series. It is recommended to use the ESP32-C series.

.. _brief-intro-firmware:

Brief Introduction to AT Firmware
----------------------------------

The ESP-AT firmware package contains several binary files for specific functionalities:

.. code-block:: none

  build
  ├── at_customize.bin        // Secondary partition table (user partition table, listing the start address and size of the mfg_nvs partition and fs_storage partition)
  ├── bootloader
  │   └── bootloader.bin      // Bootloader
  ├── customized_partitions
  │   └── mfg_nvs.bin         // Factory configuration parameters, parameter values are listed in the mfg_nvs.csv file in the same directory
  ├── esp-at.bin              // AT application firmware
  ├── factory
  │   ├── factory_xxx.bin            // Combined factory bin filled through the end of ota_1
  │   └── factory_xxx_unfilled.bin   // Combined factory bin filled through the end of the AT application (recommended)
  ├── partition_table
  │   └── partition-table.bin // Primary partition table (system partition table)
  └── ota_data_initial.bin    // OTA data initialization file

You can either flash a combined factory bin to address 0 (``factory_xxx_unfilled.bin`` is recommended), or flash several binary files to different addresses according to ``download.config``. For the difference between the two factory bins, see :doc:`../Get_Started/Downloading_guide`.
