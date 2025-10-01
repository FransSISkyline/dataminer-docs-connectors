---
uid: Connector_help_Generic_DOCSIS_CM_Collector
---

# Generic DOCSIS CM Collector

This connector uses SNMP on the standard DOCSIS MIBs to collect info from CMs and a CMTS/OLT. Multi-threaded polling is used for this. The data are intended to be aggregated and displayed by a CPE Manager. As the data are not intended to be viewed directly, the data pages of the element using this connector are not displayed.

## About

### Version Info

| Range              | Key Features                                                 | Based on | System Impact |
|--------------------|--------------------------------------------------------------|----------|---------------|
| 1.0.0.x            | Initial version.                                             | -        | -             |
| 2.0.0.x            | TDC custom version.                                          | -        | -             |
| 3.0.0.x            | EPM I-DOCSIS Solution version.                               | -        | -             |
| 3.0.1.x            | Adjustment to the PNM logic, Channel Contextuality.          | -        | -             |
| 3.0.2.x            | CCAP logic decoupled.                                        | -        | -             |
| 3.0.3.x            | CM QAM DS/US logic adjusted for better aggregation accuracy. | -        | -             |
| 3.0.4.x            | Added minimum DMA version for NuGet Packages.                | -        | -             |
| 3.0.5.x            | Modifications to improve performance.                        | -        | -             |
| 3.0.6.x            | New threshold logic.                                         | -        | -             |
| 3.0.7.x [SLC Main] | Removed hyphens from threshold settings.                     | -        | -             |

### Product Info

| Range     | Supported Firmware                 |
|-----------|------------------------------------|
| 1.0.0.x   | DOCSIS 2.0, DOCSIS 3.0, DOCSIS 3.1 |
| 2.0.0.x   | DOCSIS 2.0, DOCSIS 3.0, DOCSIS 3.1 |
| 3.0.0.x   | DOCSIS 2.0, DOCSIS 3.0, DOCSIS 3.1 |
| 3.0.1.x   | DOCSIS 2.0, DOCSIS 3.0, DOCSIS 3.1 |
| 3.0.2.x   | DOCSIS 2.0, DOCSIS 3.0, DOCSIS 3.1 |
| 3.0.3.x   | DOCSIS 2.0, DOCSIS 3.0, DOCSIS 3.1 |
| 3.0.4.x   | DOCSIS 2.0, DOCSIS 3.0, DOCSIS 3.1 |
| 3.0.5.x   | DOCSIS 2.0, DOCSIS 3.0, DOCSIS 3.1 |
| 3.0.6.x   | DOCSIS 2.0, DOCSIS 3.0, DOCSIS 3.1 |
| 3.0.7.x   | DOCSIS 2.0, DOCSIS 3.0, DOCSIS 3.1 |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 2.0.0.x   | No                  | Yes                     | -                     | -                       |
| 3.0.0.x   | No                  | Yes                     | -                     | -                       |
| 3.0.1.x   | No                  | Yes                     | -                     | -                       |
| 3.0.2.x   | No                  | Yes                     | -                     | -                       |
| 3.0.3.x   | No                  | Yes                     | -                     | -                       |
| 3.0.4.x   | No                  | Yes                     | -                     | -                       |
| 3.0.5.x   | No                  | Yes                     | -                     | -                       |
| 3.0.6.x   | No                  | Yes                     | -                     | -                       |
| 3.0.7.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Main connection

This connector uses a Simple Network Management Protocol (SNMP) connection to connect to the CMs and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: 127.0.0.1 (random)

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device. Default value: *public*.
- **Set community string**: The community string used when setting values on the device. Currently no sets are done from the connector. Default value: *private*.

#### SNMP CMTS connection

This connector uses a Simple Network Management Protocol (SNMP) connection to connect to the CMTS and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: 127.0.0.1 (random)

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device. Default value: *public*.
- **Set community string**: The community string used when setting values on the device. Currently no sets are done from the connector. Default value: **private*.*

### Configuration of Provisioning

After the collector element is created, all configuration should be done via the CPE Manager element.

### Thresholds Tables

In the threshold tables, you can define limits for each polled modulation. Two threshold tables are available, one for upstream and one for downstream.

The QAM thresholds tables are located under **DOCSIS thresholds settings** > **upstream/downstream QAM channels**.

These are the available Key Performance Indicators (KPIs) for setting upstream thresholds:

- **Minimum Tx Power Level**: Range from 25 to 55 dBmV.
- **Maximum Tx Power Level**: Range from 25 to 55 dBmV.

These are the available KPIs for setting downstream thresholds:

- **Minimum Rx Power Level**: Range from -16 to 20 dBmV.
- **Maximum Rx Power Level**: Range from -16 to 20 dBmV.
- **Minimum SNR Level**: Range from 0 to 100 dB.
- **Post-FEC Maximum Uncorrectable Error Ratio Level**: Range from 0 to 30000 ppm.

When you click the **Apply** button, the status of the specified KPIs in the CM table will be updated.

The minimum value for the Rx and Tx thresholds cannot exceed the maximum boundary; the connector will restrict attempts to set such values.

Under **DOCSIS thresholds settings** > **upstream/downstream QAM channels**, you will also find the PNM threshold parameters.<!-- RN 39603 -->

These are the available PNM parameters that can be modified:

- **Velocity Factor (VF) for Coax Cable**: Range from 0 to 1.
- **Non-Main Tap Energy Ratio (NMTER) Threshold**: Range from -50 to 0 dB.
- **Post-Main Tap to Total Energy Ratio (PostMTTER) Threshold**: Range from -50 to 0 dB.
- **Pre-Main Tap to Total Energy Ratio (PreMTTER) Threshold**: Range from -50 to 0 dB.

When you click the **Apply** button, the status of the specified PNM KPIs in the CM table will be updated.

## Usage

The data of this element are not intended to be viewed directly, so no data pages are displayed. Instead, a CPE Manager element should be used to view the data.
