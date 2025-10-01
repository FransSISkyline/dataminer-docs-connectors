---
uid: Connector_help_CPI_KHPA_Gen_IV_Series_Binary_Version
---

# CPI KHPA Gen IV Series Binary Version

CPI's GEN IV klystron power amplifier (KPA) is used by Direct-to-Home service providers for uplink services and other broadcasting applications. It uses multi-stage depressed collector (MSDC) technology and offers a combination of high power, high efficiency, small size, low heat dissipation, and low acoustic noise.

## About

### Version Info

| Range              | Key Features                               | Based on  | System Impact                                                                                    |
|--------------------|--------------------------------------------|-----------|--------------------------------------------------------------------------------------------------|
| 1.0.0.1            | Reviewed connector based on the CPI K4U74. | CPI K4U74 | -                                                                                                |
| 1.1.0.1 [SLC Main] | Supports new firmware versions.            | 1.0.0.1   | Devices running a different firmware version will not be compatible with this connector version. |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | Gen IV                 |
| 1.1.0.x   | Front Panel Main Program Software Version: 03.01.72<br>Front Panel Boot Kernel Software Version:03.00.14<br>Power Supply Main Program Software Version: 03.01.35<br>Power Supply Boot Kernel Software Version: 03.00.03<br>RF Controller Main Program Software Version: 03.01.42<br>RF Controller Boot Kernel Software Version: 03.00.03<br>Ext Interface Boot Kernel Software Version: 03.00.03<br>Ext Interface Main Program Software Version: 03.01.54<br>CAN Communication Level Key: 03.01.22<br>ID Version: GEN4 2033 |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 1.1.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### Serial Connection - Main

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Direct connection:

  - **Baudrate**: Baudrate specified in the manual of the device, e.g. *9600* (default: *9600*).
  - **Databits**: Databits specified in the manual of the device, e.g. *7*.
  - **Stopbits**: Stopbits specified in the manual of the device, e.g. *1*.
  - **Parity**: Parity specified in the manual of the device, e.g. *No*.
  - **FlowControl**: FlowControl specified in the manual of the device, e.g. *No*.

- Interface connection:

  - **IP address/host**: The polling IP or URL of the destination.
  - **IP port**: The IP port of the destination (default: *50000*).
  - **Bus address**: The bus address of the device (default: *48*). Range: *17* - *255*.

## How to use

On the **General** page, basic device configuration and version info is displayed.

More detailed information parameters can be found on the **System** page.

Details about the current, voltage, temperature, etc. can be found on the **Measurements** page.

In case of alarms or faults on the device, this status information will be displayed on the **Alarms** and **Faults** page, respectively.

Trip points can be set and monitored on the **Trip Points** page.

## Notes

To be able to perform **Set commands**, the control point of the device needs to be set to **CIF (Computer Interface)**. Otherwise, sending a command to the device will result in a response with a error code (0x22).
