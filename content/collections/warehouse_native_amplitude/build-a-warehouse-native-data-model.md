---
id: e4734233-911d-4b24-bea6-570c05955b05
blueprint: warehouse_native_amplitude
title: 'Build a warehouse-native data model'
source: 'https://help.amplitude.com/hc/en-us/articles/26004068419995-Build-a-warehouse-native-data-model'
exclude_from_sitemap: false
updated_by: 0c3a318b-936a-4cbd-8fdf-771a90c297f0
updated_at: 1717541636
---
In Warehouse-native Amplitude, data models are the building blocks of analyses. A data model in Amplitude is a table or view in your Snowflake instance that you can use to create queries and reports. You can use multiple data models when creating an analysis in Amplitude. 

While the following data types are like those used by traditional Amplitude, think of Warehouse-native events as a [fact table](https://en.wikipedia.org/wiki/Fact_table) and Warehouse-native properties (user, group, and event) as [dimensional tables](https://en.wikipedia.org/wiki/Dimension_(data_warehouse)).

Warehouse-native Amplitude currently supports the following data model types:

| Type   | Mandatory fields                             | Description                                                                                                                                                                                                                |
| ------ | -------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Events | Unique ID <br /> Timestamp (`TIMESTAMP_NTZ`) | A specific action or interaction that is recorded and associated with a timestamp. This ID will be used to understand the project and organization’s MTU count as well as how Amplitude will count uniques in Analytics. |
| User properties (current) | Unique ID | 	These are current traits and attributes associated with an individual user at the present moment, such as their current preferences or recent interactions. |
| User properties (historical) | Unique ID <br /> Start time <br /> End time | These are traits and attributes associated with an individual user over time, such as historical preferences or past interactions. |
| Group properties (current) | Unique ID | 	Current characteristics and attributes of a group at the present moment, such as name, description, or membership composition. |
| Group properties (historical) |  Unique ID <br /> Start time <br /> End time | Past characteristics and attributes of a group or organization over time, such as previous name, description, or past membership composition. |
| Event properties | Event ID | Current traits and attributes associated with a specific action or interaction that is recorded. | 

## Create a data model

1. In a Warehouse-native project, navigate to Amplitude Data and click *Add Models*.
2. Select **Table Selection** or **SQL Query** as the base table option.
   * Table selection provides selectable options based on the contents of your Snowflake instance. The available values reflect the access you granted to the set of credentials used for Warehouse-native Amplitude.
   * SQL Query provides more flexibility for base table creation. Join tables, filter rows and use any level of SQL you need to create the base table.

3. When the table is finished, complete the required fields. Supported data types are listed in the data types table at the top of this article.
4. Map the columns in the table or view you select.
5. Select or deselect any columns in the table.

    {{partial:admonition type="note" heading=""}}
    You can update this configuration post-set up. You can also use [Snowflake’s functions](https://docs.snowflake.com/en/sql-reference-functions) in the Source Column field to convert the value in the table into the desired value within Amplitude.
    {{/partial:admonition}}

6. Click Save to name your model.