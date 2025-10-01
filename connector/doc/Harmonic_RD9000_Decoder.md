---
uid: Connector_help_Harmonic_RD9000_Decoder
---

# Harmonic RD9000 Decoder

The Harmonic RD9000 is a multiformat professional **single or multi-slice UHD decoder that is HDR ready**.

This SNMP connector contains different tables that allow the user to monitor and configure both the input and output.

## About

### Version Info

| Range              | Key Features                                                                                                                 | Based on | System Impact                                          |
|--------------------|------------------------------------------------------------------------------------------------------------------------------|----------|--------------------------------------------------------|
| 1.0.0.x            | - Monitoring. <br>- Configuration of both inputs and outputs.                                                                | -        | -                                                      |
| 1.0.1.x [SLC Main] | - Renamed "Primary SRC" to "Primary Source" (same change applied to "Backup SRC"). <br>- Updated "Ts Bitrate" from bps to Mbps. <br>- Modified "Ts Sync" from "Lock Locked" to "Locked" and from "Lock Unlock" to "Unlock". <br>- Made "Primary Source" a dropdown box, dependent on the "Label" column in the "Input Source" table. <br>- Updated display keys in the "Input Source" and "MPEG IP Receive" tables. <br>- DCF interfaces added.               | 1.0.0.4  | Display key updates and parameter name/value changes. |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | -                      |
| 1.0.1.x   | -                      |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 1.0.1.x   | Yes                 | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Bus address**: The bus address of the device (default: *ByPassProxy*).

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the device.

## How to use

The element created with this connector consists of the following data pages:

- **General**: Contains basic device information such as **Alias**, **Serial Number**, and **Status**. Also contains the **CPU Core** and **Network Adapter** tables.
- **Input**: Contains multiple tables with information related to inputs, such as **Input Source**, **PAT Entry**, and **MPEG IP Receive**.
- **Output**: Contains multiple tables with information related to outputs, such as **Display Format**, **Video Output**, **SDI Link Mode**, and **Genlock**. Via page buttons, you can access subpages with **SDI** and **Ancillary** information.
- **ASI/SDI**: Displays the ASI/SDI module and Module Port, with information such as the **Genlock Format**, **Genlock Source**, and **Quad Link State**.
- **Decode**: Contains information about decoder-related tables, such as **Video** and **Audio Service**.
- **Service**: Contains the **Service Selection**, **Selected Service**, **Service Lock**, and **Selected Audio** tables.
- **Alarms**: Displays the Alarms table.
- **Events**: Contains the **System Events** and **Events Log** tables, which display information about past events.
- **System Conditions**: Contains multiple configurable tables regarding **Logs**, **Traps**, **Relay**, and **Alarms**.
