```sql
@echo off
SETLOCAL ENABLEDELAYEDEXPANSION

:: ============================================
:: SQLCMD AUTOMATION SCRIPT
:: ============================================

:: ---------- VARIABLES ----------
set SERVER=localhost
set DATABASE=master
set USERNAME=sa
set PASSWORD=YourPassword

set OUTPUT_FILE=output.csv
set ERROR_LOG=error.log

:: ---------- CHECK SQLCMD INSTALLATION ----------
echo Checking sqlcmd installation...

sqlcmd -? >nul 2>&1

IF %ERRORLEVEL% NEQ 0 (
    echo ERROR: sqlcmd is not installed or not in PATH
    echo [%DATE% %TIME%] sqlcmd missing >> %ERROR_LOG%
    EXIT /B 1
)

echo sqlcmd found successfully.
echo.

:: ============================================
:: WINDOWS AUTHENTICATION CONNECTION TEST
:: ============================================

echo Testing Windows Authentication connection...

sqlcmd -S %SERVER% -E -Q "SELECT @@VERSION"

IF %ERRORLEVEL% NEQ 0 (
    echo ERROR: Windows Authentication failed
    echo [%DATE% %TIME%] Windows login failed >> %ERROR_LOG%
) ELSE (
    echo Windows Authentication successful
)

echo.

:: ============================================
:: SQL AUTHENTICATION CONNECTION TEST
:: ============================================

echo Testing SQL Authentication connection...

sqlcmd -S %SERVER% -U %USERNAME% -P %PASSWORD% -Q "SELECT DB_NAME()"

IF %ERRORLEVEL% NEQ 0 (
    echo ERROR: SQL Authentication failed
    echo [%DATE% %TIME%] SQL login failed >> %ERROR_LOG%
) ELSE (
    echo SQL Authentication successful
)

echo.

:: ============================================
:: LIST DATABASES
:: ============================================

echo Fetching database list...

sqlcmd -S %SERVER% -E ^
-Q "SELECT name FROM sys.databases" ^
-s "," -W -h -1 ^
-o %OUTPUT_FILE%

IF %ERRORLEVEL% NEQ 0 (
    echo ERROR: Failed to export database list
    echo [%DATE% %TIME%] Export failed >> %ERROR_LOG%
    EXIT /B 1
)

echo Database list exported to %OUTPUT_FILE%
echo.

:: ============================================
:: RUN QUERY FROM FILE
:: ============================================

IF EXIST script.sql (

    echo Running SQL script file...

    sqlcmd -S %SERVER% -E -i script.sql

    IF %ERRORLEVEL% NEQ 0 (
        echo ERROR: SQL file execution failed
        echo [%DATE% %TIME%] script.sql failed >> %ERROR_LOG%
    ) ELSE (
        echo SQL file executed successfully
    )

) ELSE (
    echo WARNING: script.sql not found
)

echo.

:: ============================================
:: INTERACTIVE MODE
:: ============================================

echo Opening interactive SQLCMD session...
echo Type EXIT to quit.
echo.

sqlcmd -S %SERVER% -E

:: ============================================
:: END
:: ============================================

echo Script execution completed.
ENDLOCAL
```