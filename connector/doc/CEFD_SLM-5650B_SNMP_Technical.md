---
uid: Connector_help_CEFD_SLM-5650B_SNMP_Technical
---

# CEFD SLM-5650B SNMP

## About

This connector can be used to monitor and control a CEFD SLM-5650B satellite modem through SNMP.

## Configuration

### Connections

#### SNMP Main connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device. The default value is *public*.
- **Set community string**: The community string used when setting values on the device. The default value is *public*.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

### General

This page displays general information about the device, such as the **Model Number**, **Serial Number**, **Firmware Version**, **Time**, and **Installed Options**.

### Admin - Access

If you have the required security level, on this page you can view and configure different administration parameters, including **Modem Maintenance**, **Network Processor**, **Front Panel**, and the **Hosts Access List.**

### Admin - SNMP

If you have the required security level, on this page you can view and configure different SNMP connection parameters, including **SNMP Version**, **Trap IP Address**, **Community String**, etc.

### Admin - Firmware

If you have the required security level, on this page you can view and configure different firmware parameters, including **Firmware Revision**, **Active Image**, **Next Reboot Image**, and the **Firmware Information Table**.

### Config - Modem

If you have the required security level, on this page you can view and configure different modem parameters, including **Mode**, **Data Interface**, **Reference Clock**, **Frequency Band**, and **Transmit** and **Receive** parameters.

This page also includes page buttons that provide access to the **Receive** and **Transmit Waveform Mask** subpages. These subpages display a Waveform Mask Table for the receiver and transmitter, respectively.

### Config - Spreading

If you have the required security level, on this page you can view and configure different modulator and demodulator parameters, including **Data Rate**, **Symbol Rate** and **Chip Rate**, **Overhead**, **FEC Type**, **Modulation**, **Spreading Factor**, etc.

This page also includes two buttons that provide access to **Calculation** subpages, where you can configure parameters and then predict the result of this configuration without actually changing the parameters on the device.

### Config - ODU

If you have the required security level, on this page you can view and configure different BUC and LNB parameters, including **BUC Reference**, **LNB Reference**, **DC Power**, **Current Thresholds**, etc.

### Utility - Test Modes

If you have the required security level, on this page you can view and configure different test parameters, including **Test Modes**, **BERT Configuration** and **BERT Status**.

### Utility - Load & Save

On this page, you can **Save** or **Load** the modem configuration to or from the device internal memory.

### Status - Modem

This page displays the modem status parameters, including **Eb/No**, **Es/No**, **Frequency Offset**, **Symbol Rate**, **Chip Rate**, **MODCOD**, **Redundancy State**, **Temperature**, and the **Events Log Table**.

### Status - Statistics

This page displays the modem statistics, including the **Minimum** and **Average Eb/No** and the **Timestamps** when the values were collected.

### Status - Alarms

This page displays the modem alarms, including **Unit Alarms**, **Transmit Alarms**, **Receive Alarms**, and **Interface Alarms**.

### Web Interface

This page provides access to the user interface of the device itself. However, note that the client machine has to be able to access the device, as otherwise it will not be possible to open the web interface.

## Notes

Depending on the security level of the user, the connector can display a different set of parameters.
