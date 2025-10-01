---
uid: Connector_help_TDF_TNT_Rights_Management
---

# TDF TNT Rights Management

This connector is part of the views, services, and elements provisioning mechanism of TDF DVB-T monitoring platform.

Its goal is to manage the DMS permissions of multiple groups of users. This includes the write and config rights of the services.

## About

### Version Info

| Range                | Key Features                                                                           | Based on   | System Impact                       |
|----------------------|--------------------------------------------------------------------------------------- |------------|-------------------------------------|
| 1.0.0.x [Obsolete]   | Initial version.                                                                       | -          | -                                   |
| 1.0.1.x [SLC Main]   | Assign rights directly.<br>Group Profiles table only allows existing DMS user groups. | 1.0.0.5    | Loss of Group Profiles table data.  |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 1.0.1.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization (Range 1.0.0.x)

Configure the **Right Management Script Name** parameter with the name of the script responsible for changing the permissions of user groups.

This script is stored in Skyline's GitHub repository called **TDF-AS-TNTRightsManagement**.

Starting from version 1.0.1.1, this parameter is no longer available because the connector will perform the permission changes by itself, making the script unnecessary.

### Redundancy

There is no redundancy defined.

## How to use

In the Group Profiles table, located on the **Group Profiles** page, you can define the "service profile" each specific group can have access to. This profile is filtered based on the following information:

- Item De Catalogue
- PS State
- Operateur Diffusion
- Client
- Contrat
- SLA
- Segmentation
- Service Type
- CFS Statut

The **Rights Management** table is updated at startup and can be manually refreshed with the **Refresh Table** button.

When this table is refreshed, the column descriptions are also updated accordingly. They are ordered based on the order of the **Group Profiles** table

In range 1.0.0.x, when you change the group permissions for a specific service, the element will update the **Group List** property of that service and trigger the Automation script configured with the **Right Management Script Name** parameter. Starting from version 1.0.1.1, this connector no longer requires an Automation script, so the Group List property is no longer needed, and the element itself will be responsible for updating the group permissions.

The **Export to CSV** button exports the **Rights Management** table to a CSV file located in the *Documents \> Elements \> \[ElementName\]* folder. This file is automatically synced in the DMS after the export is completed.
