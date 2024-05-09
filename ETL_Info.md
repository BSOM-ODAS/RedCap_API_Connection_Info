# ETL Process Info
### Author: Tyler Simerson
The ETL process leverages a robust platform known as SSIS (SQL Server Integration Services), which specializes in the transfer of massive amounts of data between various database systems.  Packages are scheduled to run on a daily frequency, orchestrated through the creation of a SQL Server Agent job. This job is tasked with the coordination of executing one or more SSIS packages as needed.  In this case, just one step/package.

Within the SSIS package, a component known as a Script Task is utilized.

A Script Task extends the functionality of SSIS packages by allowing the execution of functions that are not in the built-in tasks and transformations.

This script, written in C#, is executed to perform specific tasks. In this instance, it is used to initiate an API call to the REDCap system. The purpose of this call is to retrieve data and subsequently load it into the operational data store.

More specifically, the Script Task does this…

Iterates through each REDCap project to get data for and does the following for each:
* Creates an HttpClient instance to make HTTP POST requests to the REDCap API using a token.
* Prepares two sets of request parameters for different API endpoints, one for fetching forms and another for records.
* Sends two sequential API requests. The first request fetches form data and determines a mandatory form. The second request fetches record data for the form.
* Converts the CSV response from the API into a DataTable object.
* Connects to an Oracle database and performs a bulk copy operation to insert data into Oracle tables.

In the Operational Data Store (ODS), each project/form is associated with a unique staging table.  These tables are named by merging the project and form names, replacing any spaces with underscores.  This approach ensures a consistent naming convention across the system.  To keep the data up-to-date, these tables are truncated and reloaded daily.  The data is then made available to end users through a series of materialized views, with additional reporting views layered on top.  Users can access this data using Power BI data connectors, providing a straightforward interface for data interaction.