---
uid: Connector_help_Calix_AXOS
---

# Calix AXOS

Calix AXOS (Access eXtensible Operating System) is a software-defined networking (SDN) platform designed for telecommunications networks. It provides a unified, modular, and scalable operating system for network services, enabling service providers to simplify operations, accelerate service delivery, and reduce costs. AXOS supports the deployment of fiber-to-the-home (FTTH), fixed wireless, and other broadband access technologies, allowing seamless upgrades and future-proofing of network infrastructure.

## About

### Version Info

| Range              | Features         | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware                     |
|---------|----------------------------------------|
| 1.0.0.x | Generic connector for the XGSPON cards |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

On the **General** page of this connector, you can find all general and Axos system information.

The **Alarms** page contains parameters displaying the Axos alarm count for all severities as well as an overview alarm table.

The **Cards** page contains a table displaying all available cards.

The **OLT** page contains a table displaying information about the OLT ODN ports.

The **ONT** page contains a table displaying information about ONT.
