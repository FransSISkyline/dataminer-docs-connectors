---
uid: Connector_help_Pebble_Beach_EMS
---

# Pebble Beach EMS

Pebble Beach EMS is a centralized ingest, content management, and multi-channel automation solution for systems from one to hundreds of channels.

This connector communicates with this data source through the HTTP REST and SNMP APIs (depending on the version). It allows you to monitor the available nodes and components.

## About

### Version Info

| Range | Key Features | Based on | System Impact |
|--|--|--|--|
| 1.0.0.x [Obsolete] | Initial version with SNMP interface only. | - | - |
| 2.0.0.x [Obsolete] | Adapted SNMP integration to support new firmware. | 1.0.0.x | Different display keys and columns removed on some tables. Existing DMS filters, Automation scripts, visual overviews and reports may need to be adapted. |
| 2.0.1.x [Obsolete] | - SNMP and HTTP integration. <br>- SNMP is used to track nodes and component health and status. | 2.0.0.x | Changed parameter descriptions on Node and Component Tables. Existing DMS filters, Automation scripts, visual overviews and reports may need to be adapted. |
| 2.0.2.x [Obsolete] | Added possibility to monitor channels data. | 2.0.1.x | New HTTP connection added to the connector to support Channel Monitoring API. |
| 2.0.3.x [Obsolete] | - Corrected the State discreets for Channel Health. <br>- Implemented child event processing. <br>- Changed column descriptions of Events Table. <br>- Added Media Name to Events Table. | 2.0.2.x | - The updated parameter descriptions can affect the following DMS filters, Automation scripts, visual overviews, reports, and web API implementations. <br>- Column order changed: table information will be reordered if requested externally. |
| 2.0.4.x | Primary key of Channel Items table updated to a combination of the channel ID and the channel item ID. | 2.0.3.x | All saved alarm and trend data in the Channel Items table will be lost. |
| 2.1.0.x [SLC Main] | - Initial version with HTTP only. <br>- SNMP support has been decommissioned. <br>- HTTP notifications have been implemented. | - | The connector now uses only an HTTP connection. |
| 2.1.1.x | - Primary key of events table updated to combination of playlist ID and UID. | 2.1.0.x | - Automatic poll frequency slowed to once per hour because of updated OnEventUsageTimeChanged notification handling.<br>- Custom start and end triggers are now used. |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 2.0.1.x   | \> 2.8                 |
| 2.0.2.x   | \> 2.8                 |
| 2.0.3.x   | \> 2.8                 |
| 2.0.4.x   | \> 2.8                 |
| 2.1.0.x   | \> 2.8                 |
| 2.1.1.x   | \> 2.8                 |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 2.0.1.x   | No                  | Yes                     | -                     | -                       |
| 2.0.2.x   | No                  | Yes                     | -                     | -                       |
| 2.0.3.x   | No                  | Yes                     | -                     | -                       |
| 2.0.4.x   | No                  | Yes                     | -                     | -                       |
| 2.1.0.x   | No                  | Yes                     | -                     | -                       |
| 2.1.1.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Connection (prior to 2.1.0.x only)

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (fixed value: *161*).
- **Bus address**: The bus address of the device (fixed value: *ByPassProxy*).

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

#### HTTP Connection

This connector uses two HTTP connections that require the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *18083*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

HTTP CONNECTION 2:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *8080*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

## How to use

### Version - 2.0.1.x

This version shows the **Nodes** and **Components** **table**, both containing the status information of its elements.

The events for a TxList and a channel component are also shown.

The deleted events are shown in the **Deleted Events** table. You can define for how long deleted events continue be shown in the table before they are removed.

This version also keeps track of the available **Jobs** and respective **Media Instances** and **Media Instances Usage**. Like for the Deleted Events table, you can configure a time limit for the Jobs and Media Instances Usage table items.

### Version - 2.0.2.x

This version displays two new tables:

- **Channel Table**: The main channel information.
- **Channel Items Table**: The channel items related to a single channel present in the Channel Table.

### Version - 2.1.0.x

This version shows the **playlist components**, which correspond to the TxList component type and their related events.

You can also enable a callback web service to receive notifications from the data source.

## Notes

### SNMP Usage

Support for the **SNMP interface** has been **removed** **in** **recent** **firmware versions**.

Version 2.0.1.x was developed because it was not possible to get the nodes' and components' health status with the firmware versions. However, as the SNMP interface will be removed in the future, if version 2.1.0.x meets user requirements, it should be preferred over version 2.0.1.x.
