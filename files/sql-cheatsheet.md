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

```

