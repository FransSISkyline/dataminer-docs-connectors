---
uid: Connector_help_EATON_9390_UPS
---

# EATON 9390 UPS

This connector is used to monitor the EATON 9390 UPS device.

The energy-efficient Eaton 9390 UPS (formerly Powerware 9390 UPS) provides backup power and scalable battery runtimes with a small footprint for mid-size data centers, medical equipment, and other critical systems.

## About

### Version Info

| Range              | Features        | Based on | System Impact |
|--------------------|-----------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version | -        | -             |

### Product Info

| Range   | Supported Model       | Supported Firmware |
|---------|-----------------------|--------------------|
| 1.0.0.x | PXGX UPS + EATON 9390 | 2.12               |

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
- **Set community string**: The community string used when setting values on the device (default: *public*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

### General

This page displays information about the device, such as the **System Description, System Up Time, System Location, UPS Manufacturer, UPS Software Version**, etc.

### Battery

This page displays monitoring information about the battery, such as the **Battery Status**, **Battery Time Remaining**, **Battery Voltage/Current**, etc.

The **Input** subpage contains important data regarding the inputs, such as the **Input Source**, **Input Frequency**, **Input Table**, etc.

The **Output** subpage displays information about the outputs, such as the state of the **Output Source**, **Output Frequency**, **Output Load**, **Output Table**, etc.

On the **Bypass** subpage, you can find the **Bypass Frequency** and the **Bypass Table**.

### Receptacles

This page displays information on the receptacles, such as the **Receptacle Table**.

### Environment

This page displays information on the environment of the device, such as the **Ambient Temp/Humidity**, **Remote Temp/Humidity**, **Contact Sense Table**, etc.

The **Environment Settings** subpage contains configuration parameters for temperature and humidity.

### Alarms

This page shows the number of alarms, the current number of active alarm conditions, and the **Alarm Table**, as well as the number of events, the number of entries in the UPS event history queue, and the **Event Table**.

### UPS Configuration

This page displays information on the configured parameters, such as **Configured Output Voltage**, **Configured Low Output Voltage Limit**, etc.

The **UPS Settings** page button displays configuration parameters for, among others, **shutdown**, **startup** or **reboot** operations.

On the **UPS Test** subpage, you can select a type of test procedure in the **Test Setup** section with the parameters **UPS Test Type**, **UPS Test ID**, and **UPS Test Spin Lock**. You can also review the results, such as **UPS Test Battery Status**, **UPS Test Duration**, etc.

The **UPS Topology** subpage displays information on the topology, such as **Topology Type**, **Topology Machine Code**, **Topology Unit Number**, and **Topology Power Strategy**.

The **UPS Traps** subpage contains information on the traps, such as **Max Trap Level**, **Send Trap Type**, and **Heartbeat Mins Interval**.

### Web Interface

This page displays the web interface of the device.

The client machine has to be able to access the device. If not, it will not be possible to open the web interface.
