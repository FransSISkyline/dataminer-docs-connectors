---
uid: Connector_help_Skyline_Service_Definition_Basic
---

# Skyline Service Definition Basic

The basic connector for enhanced services.

## About

This connector is the basic service definition used to create enhanced services. Other enhanced services are derived from this connector.

The connector makes active alarms and subscribed elements available in the service.

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | DataMiner 9.0.3.0         |

### System Info

| Range   | DCF Integration | Cassandra Compliant        | Linked Components | Exported Components |
|---------|-----------------|----------------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes (from 1.0.0.6 onwards) | -                 | -                   |

## Installation and configuration

### Creation

When editing a service, open the **Advanced** section and select the desired **Protocol**, in this case *Skyline Service Definition Basic*. Also select the desired **Version**.

### Configuration

To monitor the individual alarms in the **Active Service Alarms** table, set **Monitor Active Alarms** to *Enabled*.

## Usage

### General

The **Service Severity** displays the current alarm state of the service.

### Alarms

The **Active Service Alarms** table lists the alarms involved in this service. To enable this table, please set **Monitor Active Alarms** to *Enabled*.

### Elements

The **Service Element Status** table lists the child elements of the service and their alarm state.
