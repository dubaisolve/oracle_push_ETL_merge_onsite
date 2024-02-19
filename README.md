# Oracle Push ETL Solution with Batch Merge All ( delta rows only) to CSV files

## Overview
This Oracle-based solution schedules batch jobs for pushing delta batches, simulating upserts. It's designed for scenarios where transformations are done server-side, pushing only essential CSV data to data warehouses.

![image](https://github.com/dubaisolve/oracle_push_ETL_merge_onsite/assets/130452748/721493c2-d750-4e4a-8e16-ca05491fbd99)

## Features
- **Delta Batch Processing**: Efficiently processes only the changed rows.
- **Server-Side Transformation**: Reduces the complexity of data pushed out.
- **CSV Data Export**: Structured export format for easy integration.
- **Automated Data Loading**: Ensures correct loading sequences to maintain data integrity.

## System Requirements
- Oracle Database with UTL_FILE and DBMS_SQL.
- Schema grants for a designated tablespace.
- Scheduling and execution permissions for procedures. (don't forget to create your schedule to kick off the procedure! )
- OS-level write permissions on the Oracle server.

## Components
- **DDL for Tables**: Create necessary tables for batch processing.
- **Merge Procedures**: Custom procedures for data merging.
- **CSV Package**: Procedures for data load organization and CSV export.

## Usage
1. **Initialization**: Set up the environment and storage.
2. **Data Loading**: Follow the predefined loading order.
3. **Batch Processing**: Use `merge_export_all` for merging and CSV exports.
4. **Log Management**: Generate logs for exported data.

## Demo
[Demo Video Link] - https://youtu.be/5AJbZExEN50  - Video demonstration of the setup and execution. - 

## Snippet

CREATE OR REPLACE PROCEDURE BI_TRAVELBOX_USER."MERGE_EXPORT_ALL" AS
  -- [Procedure details...]
BEGIN
  -- [Procedure logic...]
END merge_export_all;

## MORE in-depth description :

- This repository presents a method for scheduling batch jobs in Oracle databases, emphasizing on efficiently handling delta batches (upserts). The core functionality involves pushing batch files containing only the rows that have changed since the last run. This approach is particularly advantageous in scenarios where on-server data transformation is preferred, ensuring that only the necessary data is extracted and sent in CSV format.

- The solution requires setting up a pagefile and allocating adequate storage on the server. All data transformations are executed on the server, reducing the need for external processing and simplifying the data pushed out. This method is especially beneficial for cases where there is a ready-to-use model in the data warehouse, allowing for direct merging without additional data manipulation. On-the-fly transformations become a streamlined process.

  -- Key aspects of the solution include:

- DDL Creation: Establishing the required database schema for the tables intended for batch processing.
Merge Procedures: Developing specific procedures for each table to manage the merging of data from source to destination tables, ensuring that only necessary changes are applied.
Loading Package and Order Management: Implementing a set of procedures within a CSV package to organize the loading sequence of data. This order is critical to maintain the integrity of relationships between master and fact tables. The solution includes a 'loading order' table that dictates this sequence, ensuring a smooth and error-free data integration process.
Upon execution, the merge_export_all procedure initiates the process, checking the list of tables for merging. Post-merging, it triggers the CSV package, which then selects and exports only the marked rows based on a 'flag' timestamp column in the destination tables. The process also generates a log file for each batch, providing a detailed record of the operations and changes made.

  -- While the solution is designed to minimize risks and is particularly useful where direct server connections are not feasible, it requires specific permissions and setups:

- Schema grants for writing to the designated storage (tablespace).
- Scheduled rights and execution permissions for the procedures.
- Permissions to write to the storage of the operating system where the Oracle system resides.
  -- Initially developed in a non-production environment, this solution has been successfully deployed in production settings, proving its efficacy and reliability over several years. It represents a robust and secure method for managing data upserts in Oracle databases, catering to environments with stringent security and connectivity constraints.
