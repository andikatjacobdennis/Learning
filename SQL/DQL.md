Select example:

```sql
SELECT DISTINCT TOP 10 PERCENT
    T1.ChassisSeries + T1.ChassisNumber AS Chasis
    -- COUNT(*) AS TotalRows,
    -- COUNT(column1) AS ColumnCount
    -- Other Examples: SUM(column1), AVG(column1), MIN(column1)
FROM dbo.Product AS T1
LEFT OUTER JOIN Variant AS T2
    ON T1.Id = T2.Id

-- WHERE
--     <row filter>
--     AND | OR | NOT
--     BETWEEN a AND b
--     IN (...)
--     LIKE '%value%'
--     IS NULL | IS NOT NULL
--     = | <> | < | <= | > | >=

-- GROUP BY
--     GroupColumnList

HAVING
    COUNT(*) > 5

ORDER BY
    col1 DESC,
    col2 ASC;
```

Variable declaration example:

```sql
DECLARE @ChassisNumber DECIMAL(10, 2);
DECLARE @VehicleID NVARCHAR(50);

SET @ChassisNumber = 50000.04;
SET @VehicleID = 'C102';

SELECT *
FROM TableName
WHERE VehicleID = @VehicleID;
GO
```

Stored procedure example:

```sql
CREATE OR ALTER PROCEDURE ProcedureName
    @DepartmentName NVARCHAR(50)
AS
BEGIN
    SET NOCOUNT ON;

    SELECT 'Zero';
END;
GO

EXEC ProcedureName @DepartmentName = 'One';
```
