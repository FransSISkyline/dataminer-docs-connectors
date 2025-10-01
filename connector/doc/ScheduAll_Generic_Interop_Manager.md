---
uid: Connector_help_ScheduAll_Generic_Interop_Manager
---

# ScheduAll Generic Interop Manager

This connector is designed to interact with the **ScheduAll** platform, a Windows-based application for managing bookings (also referred to as work orders). Through the **ScheduAll Interop Service**, the connector receives notifications regarding new, updated, or canceled work orders, enabling their use in orchestration within a DataMiner System. Using the **ScheduAll Interop Listener**, it sends status updates back to ScheduAll, providing real-time feedback on the orchestration processes tied to these work orders.

## About

### Version Info

| Range              | Features        | Based on | System Impact |
|--------------------|-----------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | N/A                |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

### DataMiner Compliancy

| Range   | Minimum required DataMiner version |
|---------|------------------------------------|
| 1.0.0.x | 10.2.0.0 - 12603                   |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *80*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

#### Smart-Serial Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Direct connection:

  - **Baudrate**: Baudrate specified in the manual of the device, e.g. *9600*.
  - **Databits**: Databits specified in the manual of the device, e.g. *7*.
  - **Stopbits**: Stopbits specified in the manual of the device, e.g. *1*.
  - **Parity**: Parity specified in the manual of the device, e.g. *No*.
  - **FlowControl**: FlowControl specified in the manual of the device, e.g. *No*.

- Interface connection:

  - **IP address/host**: The polling IP or URL of the destination.
  - **IP port**: The IP port of the destination.
  
### Initialization

To begin using the **ScheduAll Generic Interop Manager**, some initial configuration is required. The settings detailed below ensure proper communication with the ScheduAll platform and can define how work order updates are handled for orchestration within the DataMiner System.

#### Interop Listener Settings

To enable communication with ScheduAll through the ScheduAll Interop Listener, the corresponding user credentials must be configured:

1. On the **Configuration** page, go to the **Interop Listener Settings** section.
1. Enter the required user and password.
1. Test the credentials by clicking the **Log In** button to ensure successful authentication.

#### Work Order Settings

Work order updates received from the ScheduAll platform are typically intended for orchestration within the DataMiner System. When new updates are detected, an Automation script can be triggered to initiate the orchestration process:

1. On the **Configuration** page, go to the **Work Order Settings** section.
1. In the **Script Name** parameter, specify the name of the Automation script.

   This script will be executed whenever work order updates are received, enabling seamless orchestration.

   > [!NOTE]
   > This Automation script must be developed according to the orchestration needs.

With this configuration, the ScheduAll Generic Interop Manager will be able to efficiently process work orders and execute orchestration workflows within the DataMiner ecosystem.

#### Field Mapping

The **ScheduAll Interop Service** sends work order updates to the connector in the form of XML messages. These messages can be customized in ScheduAll to include unique XML tags. To ensure the connector can correctly process and save these updates, the **Field Mapping Table** must be configured:

1. Go to the **Configuration** > **Field Mapping** page.

   In the **Field Mapping Table**, you will see the list of the columns available in the Work Orders Table.

1. For each item in the **Map** column, specify the corresponding custom XML tag from the ScheduAll updates.

## How to use

Once the initial configuration of the ScheduAll Generic Interop Manager is complete, the element will be ready to:

- Receive work order updates from the ScheduAll platform.
- Send orchestration updates back to ScheduAll, if required.

### Orchestration Script Execution

You can define when the orchestration script should be executed by configuring the following parameters:

- **Maximum Work Order Messages**: This parameter specifies the maximum number of work order messages to accumulate before activating the orchestration script. When the threshold is reached, the script will be triggered.

- **Maximum Work Order Wait Time**: This parameter defines the maximum time to wait for updates from ScheduAll. If no new updates are received within this period, the orchestration script will be activated.
