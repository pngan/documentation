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
            , TABLE_SCHEMA AS 'TableSchema'
            ,TABLE_NAME AS  'TableName'
FROM        INFORMATION_SCHEMA.COLUMNS
WHERE       COLUMN_NAME LIKE '%user_id%'
ORDER BY    TableSchema,
            TableName
            ,ColumnName;
GO


-- List Foreign Keys referencing a table
EXEC sp_fkeys 'TableName'
GO

-- List Foreign Keys in database
SELECT C.TABLE_CATALOG [PKTABLE_QUALIFIER], 
       C.TABLE_SCHEMA [PKTABLE_OWNER], 
       C.TABLE_NAME [PKTABLE_NAME], 
       KCU.COLUMN_NAME [PKCOLUMN_NAME], 
       C2.TABLE_CATALOG [FKTABLE_QUALIFIER], 
       C2.TABLE_SCHEMA [FKTABLE_OWNER], 
       C2.TABLE_NAME [FKTABLE_NAME], 
       KCU2.COLUMN_NAME [FKCOLUMN_NAME], 
       RC.UPDATE_RULE, 
       RC.DELETE_RULE, 
       C.CONSTRAINT_NAME [FK_NAME], 
       C2.CONSTRAINT_NAME [PK_NAME], 
       CAST(7 AS SMALLINT) [DEFERRABILITY] 
FROM   INFORMATION_SCHEMA.TABLE_CONSTRAINTS C 
       INNER JOIN INFORMATION_SCHEMA.KEY_COLUMN_USAGE KCU 
         ON C.CONSTRAINT_SCHEMA = KCU.CONSTRAINT_SCHEMA 
            AND C.CONSTRAINT_NAME = KCU.CONSTRAINT_NAME 
       INNER JOIN INFORMATION_SCHEMA.REFERENTIAL_CONSTRAINTS RC 
         ON C.CONSTRAINT_SCHEMA = RC.CONSTRAINT_SCHEMA 
            AND C.CONSTRAINT_NAME = RC.CONSTRAINT_NAME 
       INNER JOIN INFORMATION_SCHEMA.TABLE_CONSTRAINTS C2 
         ON RC.UNIQUE_CONSTRAINT_SCHEMA = C2.CONSTRAINT_SCHEMA 
            AND RC.UNIQUE_CONSTRAINT_NAME = C2.CONSTRAINT_NAME 
       INNER JOIN INFORMATION_SCHEMA.KEY_COLUMN_USAGE KCU2 
         ON C2.CONSTRAINT_SCHEMA = KCU2.CONSTRAINT_SCHEMA 
            AND C2.CONSTRAINT_NAME = KCU2.CONSTRAINT_NAME 
            AND KCU.ORDINAL_POSITION = KCU2.ORDINAL_POSITION 
WHERE  C.CONSTRAINT_TYPE = 'FOREIGN KEY'
GO





```

