---
uid: Connector_help_TDF_BIP_Collector
---

# TDF BIP Collector

This connector is used to collect data from the **BIP (Production Incident Database)** system, responsible for interfacing all the collector subsystems, the storage subsystem, and all potential customers using the collected and correlated data.

## About

### Version Info

| Range              | Key Features     | Based on | System Impact                                                               |
|--------------------|------------------|----------|-----------------------------------------------------------------------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -                                                                           |
| 2.0.0.x            | Initial version. | 1.0.0.1  | This version impacts the UX and functionality. It is intended for EPM only. |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | 4.58               |
| 2.0.0.x | 4.58               |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |
| 2.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### HTTP Main Connection

This connector uses an HTTPS connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination. Should always start with `https://`.
- **IP port**: Default: *8443*.

##### Initialization

In order to perform requests, first the **Domains List** parameter needs to be configured. You can define only one domain or define multiple domains separated by semicolons (";").

## How to use - Range 1.0.0.x

The connector contains the following data pages:

- **General**: Contains the **Domains List** parameter, which allows you to define from which domain requests should be directed. If this parameter is not defined, the connector cannot request any data.

- **Resources**: Contains the **Resources Table**, with all the information obtained from the get resources request.

- **Alarms**: Contains the **Event Types Table**, with all the possible event types, and the **Event Table**, with the active events, limited to the last 15 minutes.

  On this page, you can also define the display key of the Events Table, by means of the parameter **Events Table Display Key Selection**. If *Internal Description* is selected, the display key will have the following format: `Event ID/Event Internal Description/Resource Internal Description`. If *External Description* is selected, the format will be `Event ID/Event External Description/Resource External Description`.

- **Polling Configuration**: On this page, you can select which of the available requests is polled and when. You can also poll the requests on demand with the **Poll** button for each entry in the table. With the **Poll All** button, you can poll all requests on demand at once.

## How to use - Range 2.0.0.x

In range 2.0.0.x, the user interface has been redesigned to have the same look and feel as other EPM collectors. Its **General** page now functions as a landing page with an overview of entities in the connector. All relevant settings have been moved to the **Configuration** section of the connector. In addition, the contents of the former Alarms page are now available on the **Events** page, and a new **Normalized Alarms** page is available that streamlines the alarms for the EPM solution.

In the **Configuration** section, you can configure all the essential settings for the functionality of the connector:

- **Entity Export/Import Settings**: These sections allow the exporting of the configuration files and importing of the provisioning files.

  - **Entity Export** and **Entity Import**: These parameters allow you to enable/disable the exporting and importing feature.
  - **Export Directory** and **Entity Import Directory**: It is necessary to specify the paths where the files will be exported and imported.
  - **Entity Export Directory Type** and **Entity Import Directory Type**: Specify whether the export/import paths are **local or remote**. For the remote file handling to work, you must enter the credentials for the system in the System Credentials section and enter the path to the remote directory in the Export Directory or Import Directory parameter. The path must be shared/accessible, or this feature will not work.
  - **Apply Button**: This button allows you to manually export/import the files.

- **System Credentials**: This section is used if the element is configured to a remote file location.

  - **System Username**: The username of the user with access to the directory. If no domain is specified, the domain from the element's DMA location will be used.
  - **System Password**: The password of the user to access the remote directory.

- **Event Configuration**: This section contains parameters that are on the General page in range 1.0.0.x.

  - **Domains List**: Allows you to define from which domain requests should be directed. If this parameter is not defined, the connector cannot request any data.
  - **Event Nature List**: Allows you to define the nature of the events to be requested.

- The **Polling Configuration** section is available on a subpage in the Configuration section. Here, you can select which of the available requests is polled and when. You can also poll the requests on demand with the **Poll** button for each entry in the table. With the **Poll All** button, you can poll all requests on demand at once.

- The **Other Settings** section allows you to access the **Debug** page, which contains a button that clears the Normalized Alarms tables.

  > [!IMPORTANT]
  > Do not clear the normalized alarms unless you have been instructed to do so by someone from Skyline.
