```sql
-- List Tables
SELECT [t].* 
FROM [sys].[tables] AS [t];
GO

-- Review table definition and indexes
EXEC [sp_help] '[dbo].[Employee]';
GO

-- Show Disk Usage
SET STATISTICS IO ON;
GO


-- Show table dependencies
SELECT referencing_schema_name, referencing_entity_name,
referencing_id, referencing_class_desc, is_caller_dependent
FROM sys.dm_sql_referencing_entities ('app.user', 'OBJECT');
GO
-- OR

sp_depends 'app.inventory'
go

-- Find tables by name
SELECT * FROM sys.tables WHERE name LIKE '%inve%'
GO

-- Find columns by name
SELECT      COLUMN_NAME AS 'ColumnName'
            ,TABLE_NAME AS  'TableName'
FROM        INFORMATION_SCHEMA.COLUMNS
WHERE       COLUMN_NAME LIKE '%contact%'
ORDER BY    TableName
            ,ColumnName;
GO



```

