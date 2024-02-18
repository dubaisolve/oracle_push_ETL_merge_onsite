# Oracle Batch Job Scheduler for Data Upserts

## Overview
This Oracle-based solution schedules batch jobs for pushing delta batches, simulating upserts. It's designed for scenarios where transformations are done server-side, pushing only essential CSV data to data warehouses.

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
[Demo Video Link](#) - Video demonstration of the setup and execution. - https://youtu.be/5AJbZExEN50

## Code Snippet
```sql
CREATE OR REPLACE PROCEDURE BI_TRAVELBOX_USER."MERGE_EXPORT_ALL" AS
  -- [Procedure details...]
BEGIN
  -- [Procedure logic...]
END merge_export_all;

## 
