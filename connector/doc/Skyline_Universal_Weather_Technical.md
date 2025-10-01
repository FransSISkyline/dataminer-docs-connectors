---
uid: Connector_help_Skyline_Universal_Weather_Technical
---

# Skyline Universal Weather

## About

The Skyline Universal Weather connector is designed to retrieve weather conditions from a **weather API** source of the user's choice for selected locations specified by the user. It is currently compatible with three distinct weather APIs: **OpenWeather OneCall 2.5**, **OpenWeather OneCall 3.0**, and **Windy Point-Forecast API v4**.

This connector uses an **HTTPS** connection to communicate with the selected API. The weather information is then retrieved for the locations specified by the user.

The connector can retrieve current weather data from OpenWeather either manually via the ad hoc console or automatically through the InterApp framework, which enables external elements to trigger requests as needed. This reduces unnecessary API calls, helps manage usage quotas efficiently, and supports ticketing and diagnostics through response messages.

## Configuration

### Connections

#### HTTP Main Connection

This connector uses an HTTPS connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP of the API.

  - For OpenWeather OneCall: [https://api.openweathermap.org](https://api.openweathermap.org/)

- **IP port**: The IP port of the device. By default: *443*.

### Initialization

On the **Configuration** page, select the API using the **Service Source** parameter. Then set the API key for the selected API.

To add a location to be monitored, right-click the **Locations Overview** table and select **Add item**.

## Usage

### General

The General page, which is the **default** landing page, provides an overview of the system.

This page contains parameters such as:

- **Service Status**: The status of communication with the API.

- **Number of Requests**: The number of requests made to the weather API. **This may be important as some source APIs charge based on the number of calls**.

  Note that the **OpenWeather** API does not reply with the number of calls made, so the number of calls is counted for this specific element only.

- **Number of Locations**: The number of locations for which weather conditions will be requested.

- **Number of Quick Locations**: The number of locations requested using the **ad hoc feature**.

### Forecast

This page contains the information that is retrieved **from the API for each location** in the **Current Conditions** table. This table among others includes the following parameters:

- **Name**: The name of the location.
- **Latitude**: The latitude of the location.
- **Longitude**: The longitude of the location.
- **Precipitation Type**: The type of precipitation.
- **Humidity**: The humidity level.
- **Temperature**: The temperature.

This page also contains a page button that opens the Locations subpage, where locations can be configured.

#### Windy API Forecast Tables (Range 1.0.3.x, 1.0.4.x, and 1.1.0.x)

This page contains forecast information retrieved from the Windy Point-Forecast API. It contains the following parameters:

- **Windy Forecast Last Polled**: Time when the last Windy API request was made.
- **Windy Forecast Table**: Table that stores the API response. It returns predictions in fixed 3-hour intervals for at least the next 7-10 days. Returned forecast parameters are all recorded at surface level.
- **Windy Forecast History Table**: When a prediction expires, it is sent to the history table. History entries can be deleted through the context menu.

#### Locations

On this subpage, **by right-clicking** in the table, you can **add**, **edit**, and **delete** locations that will be used to gather weather condition information from the API.

The table contains among others the following fields:

- **Name**: A meaningful name for the location **must be specified** here.
- **Description**: Allows you to add an optional description with additional meaningful information on the location.
- **Latitude**: The latitude of the location **must be specified** here.
- **Longitude**: The longitude of the location **must be specified** here.
- **Masked**: Allows you to mask a location. If this feature is enabled, the location's weather conditions will not be requested. **By default, this is disabled.**

You can also import a CSV file with the columns **Name**, **Description**, **Latitude**, and **Longitude**, in this order. **For Latitude and Longitude, do not use commas as decimal separators.**

### Ad-Hoc Forecast

This page is divided into two sections, **Ad-Hoc Console** and **Ad-Hoc Current Conditions**.

In the **Ad-Hoc Console** section, you can make a **quick request** to the API for a specific location by filling in a **few configuration parameters**.

- **Request Type**: Allows you to select which type of request will be made to the API.
- **Request Parameters**: Allows you to enter the **query parameters** that will be used in the request selected in **Request Type**.
- **Location Name**: Allows you to enter a name.
- **Location Description**: Allows you to enter a description of the location.
- **Request Status**: Displays the status of the request that is sent.
- **Apply button**: Allows you to send the request to the API.

The section below this contains a table, **Ad-Hoc Current Conditions**, which contains the weather information requested by any call made in the section above. The table in this section is similar to the table on the **Forecast page**, containing among others the following parameters:

- **Name**: The name of the location.
- **Latitude**: The latitude of the location.
- **Longitude**: The longitude of the location.
- **Precipitation Type**: The type of precipitation.
- **Humidity**: The humidity level.
- **Temperature**: The temperature.

### Configuration

This page contains **configuration parameters** that allow you to modify **how the connector operates**:

- **Service Source**: Allows you to select the **Service Source API** of your choice.
- **Powered By**: Displays by which provider the API is powered once the service source is selected. Some service source providers require this to be present.
- **Auto Processing Time**: Allows you to specify how often a request is sent to the API for the locations that are entered in the **Locations Table**.

This page also contains several page buttons. You can find more information about these below.

#### Ad Hoc

This subpage contains configuration parameters specific to the **ad hoc functionality** of the connector:

- **Console Status**: If this parameter is set to *Enabled*, you will be able to make calls to the API via the ad hoc console. This parameter is **enabled by default**.

- **Inter Element Service**: If this parameter is set to *Enabled*, this allows **other elements** within the DMS to make calls to the element running this connector to **retrieve weather information**. This parameter is **enabled by default**.

  **Prior to range 1.0.2.x**, this feature uses a **listener parameter** that will retrieve the required information, such as **Request Type**, **Request Parameters (Query Parameters)**, **Location Name**, and **Location Description**, in JSON format. **From range 1.0.2.x onwards, the listener parameter is no longer used**, because the element communication uses InterApp calls instead. In either case, a call will be made to the API next, and then the ad hoc table will be updated, and the response from the API will be sent back to the element that requested the weather information.

- **Auto Delete**: If this parameter is set to *Enabled*, the **Ad-Hoc Current Conditions** table is automatically **cleaned up every hour**. This parameter is **enabled by default.**

- **Auto Delete Delay**: Allows you to specify when entries in the table should be cleaned up **when the Auto Delete functionality runs**. This parameter is set to ***Real Time*** by default.

- **Clear All**: Allows you to clear all entries from the Ad-Hoc Current Conditions table.

#### OpenWeather

This subpage contains parameters that allow you to configure the communication with **OpenWeather 2.5** and **OpenWeather 3.0**:

- **API Key**: The API key that will allow the connector to communicate with the API.
- **Max Number of Request (24 Hours)**: The maximum number of calls that can be made to the API.

  Note: **1000 calls daily are free**, but there will be charges after the initial 1000.

#### Windy (Range 1.0.3.x)

This subpage contains parameters to configure the communication with the **Windy Point-Forecast API v4**.

- **Windy API Key**: The Point-Forecast API key that is used to obtain forecast information from the Windy API.

- **Windy Max Number of Request (24 Hours)**: The maximum number of calls that can be made to the API each day. Configure this based on your account to avoid incurring unnecessary charges.

- **Windy Forecast Model**: The forecast model that will be used to obtain information. The following models are currently supported:

  - *arome*: Covers France and surrounding areas.
  - *iconEu*: Covers Europe and surrounding areas.
  - *gfs*: Global model.
  - *namConus*: Covers the USA and surrounding areas (Canada, Mexico).
  - *namHawaii*: Covers Hawaii.
  - *namAlaska*: Covers Alaska and surrounding areas.

For more information about the Windy API, see [Point Forecast API](https://api.windy.com/point-forecast/docs).

#### Windy (Range 1.0.4.x)

This subpage contains parameters to configure the communication with the **Windy Point-Forecast API v4**.

- **Windy API Polling Status**: Enable/disable polling of the Windy API.

- **Windy API Key**: The Point-Forecast API key that is used to obtain forecast information from the Windy API.

- **Windy Max Number of Request (24 Hours)**: The maximum number of calls that can be made to the API each day. Configure this based on your account to avoid incurring unnecessary charges.

- **Windy Forecast Model**: The forecast model that will be used to obtain information. The following models are currently supported:

  - *arome*: Covers France and surrounding areas.
  - *iconEu*: Covers Europe and surrounding areas.
  - *gfs*: Global model.
  - *namConus*: Covers the USA and surrounding areas (Canada, Mexico).
  - *namHawaii*: Covers Hawaii.
  - *namAlaska*: Covers Alaska and surrounding areas.

- **Number of Windy API Requests Made (24 Hours)**: The number of Windy API requests made by the connector. This parameter resets every 24 hours.

- **Windy API Polling Frequency**: The frequency at which the connector makes API requests.

For more information about the Windy API, refer to the [Windy documentation](https://api.windy.com/point-forecast/docs).

## Notes

- **Listener PID**: 283

  Note: **From range 1.0.2.x onwards, the listener parameter is no longer used**, because the element communication uses InterApp calls instead.

- **APIs integrated**: OpenWeather OneCall and Windy Point-Forecast.

- The Windy API URL is built-in and uses the same proxy server as the OpenWeather OneCall APIs.
