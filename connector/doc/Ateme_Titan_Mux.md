---
uid: Connector_help_Ateme_Titan_Mux
---

# Ateme Titan Mux

## About

Ateme Titan Mux is used to interface with the Multiplexer Processing API and Alarm API to access and manage TitanMux's processing features and Alarms.

### Version Info

| Range     | Key Features     | Based on     | System Impact     |
|-----------|------------------|--------------|-------------------|
| 1.0.0.x [Obsolete]  | Initial version  | -            | -                 |
| 1.0.1.x [SLC Main] | Converted the History Alarms table to a partial one and added a configurable maximum number of alarms history to get.  | 1.0.0.7 | Existing custom reports and Automation scripts that use the History Alarms table may no longer work as expected. |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 1.5.11.3-0             |
| 1.0.1.x   | 1.5.11.3-0             |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 1.0.1.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### HTTP Main Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination, e.g. `http://127.0.0.1:8002/api/v1/mux/inputs`
- **IP port**: The IP port of the destination.
- **Bus address**: *ByPassProxy*

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

On the **General** page of this connector, you can configure the username and password to access the device.

The **Inputs** page contains basic information about the existing inputs as well as the redundancy and bit rate information. It also has a toggle button and dropdown to automatically/manually remove the obsolete inputs based on the Row Status column.

The **Inputs Redundancy** page displays the redundancy state for all the inputs of the MUX and more details of the primary and secondary IP network source configuration parameters.

The **Inputs Programs** page contains detailed program-specific information and bit rates for each program ID and PID.

The same applies for the **Outputs** and **Outputs Programs** page.

The **Active Alarms** page contains a list of active alarms and the alarm count, and the **History Alarms** page lists the alarm history and displays the full history alarm count. The number of alarms polled in the alarm history is limited to the **History Alarms Maximum Amount**.
