Oracle Batch Job Scheduler for Data Upserts
Overview
This Oracle-based solution efficiently schedules batch jobs for pushing delta batches (only changed rows from the last run), simulating upserts. It's designed for scenarios where transformations are done on the server, ensuring that only essential data (in CSV format) is pushed out. This is particularly useful for data warehouses where data is merged without requiring additional transformations.

Key Features
Delta Batch Processing: Focuses on changed rows for efficient data syncing.
Server-Side Transformation: All data transformations occur on the Oracle server.
Structured Data Export: Data is exported in CSV format for easy integration with various systems.
Automated Data Loading Order: Ensures correct loading sequences (e.g., master tables before fact tables) to maintain data integrity.
System Requirements
Oracle Database with UTL_FILE and DBMS_SQL capabilities.
Schema grants to write to a designated tablespace.
Scheduling rights and execution permissions for procedures.
OS-level write permissions on the Oracle system server.
Components
DDL for Tables: For creating the necessary tables for the batch process.
Merge Procedures: Custom procedures for merging data from source to destination tables.
CSV Package: A set of procedures for organizing data load order and exporting to CSV.
Usage
Initialization: Set up the environment and allocate storage as required.
Data Loading: Follow the predefined order of table loading to avoid PK/FK issues.
Batch Processing: Utilize the merge_export_all procedure to perform data merges and trigger CSV exports.
Log Management: Automatically generate log files to track exported data.
Demo
A video demonstration of the setup and execution can be found here: Demo Video Link
Code Snippet
Here's a glimpse of the core procedure MERGE_EXPORT_ALL used in this solution:

sql
Copy code
CREATE OR REPLACE PROCEDURE BI_TRAVELBOX_USER."MERGE_EXPORT_ALL" AS
  -- [Procedure details and initialization...]
BEGIN
  -- [Logic for executing procedures from loading order table...]
  -- [Export logic for changed/merged tables...]
  -- [Log file creation and additional procedure calls...]
END merge_export_all;
Installation & Configuration
Ensure all prerequisites are met and Oracle environment is properly configured.
Execute the provided SQL scripts to set up the necessary database objects.
Adjust configurations (e.g., export directory, file formats) as per your environment.
Contributing
Feel free to fork this repository and submit pull requests for any enhancements or fixes.

License
[Specify License Here]
