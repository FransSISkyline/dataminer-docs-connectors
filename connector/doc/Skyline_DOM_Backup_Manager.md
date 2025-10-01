---
uid: Connector_help_Skyline_DOM_Backup_Manager
---

# Skyline DOM Backup Manager

This is a generic connector that ingests all of the available **DOM modules in the DMS** and takes a backup of each module based on user requirements.

It is intended for users that depend a lot on DOM for their day-to-day operations, so they can have the peace of mind of knowing that if something goes wrong with their system, all their DOM modules will be backed up. This connector offers the ability to include DOM instances in the backups along with some quality-of-life configuration for e.g. frequency of backups, maximum backups, etc.

Furthermore, it is possible to restore previous backups. This gives the user the possibility to easily go back to an earlier point in time.

> [!WARNING]
> Only use this connector in production systems after evaluating internally within Skyline. Whether using this connector is recommended depends on the size of a certain module, its instances, and the DMS to which you want to deploy it.

## About

### Version Info

| Range              | Features         | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

## How to use

### Backups Schedule Page

The **Backups Schedule** page lists all the **available DOM modules** in a table. The table also contains a number of configuration parameters to help with the backup functionality of this connector:

- **Automatic Backups**: This will take a backup automatically based on the frequency you define. If this is disabled, no backups will be created.
- **Frequency**: You can choose between **every hour**, **every 12 hours**, **every day**, **every week**, and **every month** for automatic backups.
- **Maximum Amount of Backups**: This will limit the number of backups that are made, to prevent taking up too much disk space. Once the limit is reached, the connector will **delete the oldest backup file** for the new backup file.
- **Instances State**: This will include or exclude the **DOM instances** in the backup file.
- **Backup button**: With this button, you can manually back up a particular DOM module.

There are also two standalone configuration parameters on this page:

- **Backup File Path**: The path where the backup will be stored. Default: `C:\Skyline DataMiner\Documents\DMA_COMMON_DOCUMENTS\DOM Backups`.
- **Sync button**: This allows you to manually **update the table** with all DOM modules in the DMS.

### Restorables Page

The **Restorables** page of this connector contains two tables: the **DOM Module Overview Table**, listing all the DOM modules inside a specified folder, and the **Restorables Overview Table**, listing the zip files that can be restored.

There are also several standalone configuration parameters on this page:

- **Restore Folder Path**: Syncs the modules across the zip files at the specified path. Default: `C:\Skyline DataMiner\Documents\DMA_COMMON_DOCUMENTS\DOM Backups`.
- **Update Folder Path**: Updates the **DOM Module Overview** table with the modules found inside the folder specified with the Restore Folder Path parameter.
- **Update Path**: Updates the **Restorables Overview** table with the zip files found inside the folder specified with the Restore Folder Path parameter.

#### DOM Module Overview Table

This table shows all the different modules inside the specified folder. It allows you to control the inclusion or exclusion of zip files associated with each module in the **Restorables Overview** table:

- **ID**: The name of the module.
- **State**: You can choose between *Included* or *Excluded* for the module. This will determine whether the associated rows are shown in the **Restorables Overview** table.

#### Restorables Overview Table

This table allows you to select a zip file to restore the information for the desired module:

- **Last Modification**: The latest modification in the JSON within the zip file.
- **Zip File Name**: The name of the zip file.
- **Module ID**: The name of the module in the zip file.
- **DOM Definition Count**: The number of DOM definitions.
- **Section Definition Count**: The number of section definitions.
- **DOM Instances Count**: The number of DOM instances.
- **Restore State**: Displays the current state of the row. Possible values are **Not Restored**, **Processing**, **Failed**, and **Restored**.
- **Restore Button**: Allows the connector to restore the desired row.

> [!NOTE]
> The restorables displayed in this table are **unique**. They are determined by comparing the Last Modification parameter of each created backup. This comparison process runs in the background. The advantage of this approach is that when the user sorts the table by the Last Modification column, it effectively creates a version history of DOM backups, showing only the distinct backup moments that are meaningful for restoration. It is normal not to see all backups of the backup folder in this table, especially if multiple backups were taken without any changes made in between.

> [!WARNING]
> In the background, when a previous backup is restored, the system first checks if the module already exists. If it does, an automatic backup is created before the existing module is deleted and the old backup is imported. Although this approach ensures safety, it can be time-consuming depending on your system's computing power and the read/write speed of your indexing engine.

### Configuration Page

On the **Configuration** page of this connector, you can configure the following parameters:

- **DMS Sync State**: Allows the connector to sync the backup files across the DMS if the **Backup File Path** contains `C:\Skyline DataMiner\Documents`.
- **DOM Module Sync Frequency**: Determines how often the connector will check for DOM modules in the system. **Minimum**: 1 Hour. **Maximum**: 24 Hours.
