# SQL-Server-DTU-Calculation
This article is to show you how to use a PowerShell script to collect data from VM that hosts SQL server and then estimate the DTU (Data Trans. Unit) needed if all the DBs running in Azure SQL DB.
A popular web tool is provided by http://dtucalculator.azurewebsites.net/. In it, there is an executable (.exe) file and a PowerShell script that can collect data from a Windows server on it Microsoft SQL Server is running. The collected data are the following:

Processor - % Processor Time Logical Disk

Disk Reads/sec Logical Disk

Disk Writes/sec Database

Log Bytes Flushed/sec

The PowerShell script collects 3600 datapoints in an interval of one second and writes the result to a CSV file. Then this file can be uploaded to the web site with the info on how many core the server has for calculation of the DTU needed and visualization.

Sometimes, one may have difficulty to collect the data for SQLServer:Databases(_Total)\Log Bytes Flushed. To overcome this problem, we can skip this one and put a fixed value in the position, say 0, which is the case that there is no activity on the SQL Server. Or we can set this value to 480000 to reflect the upper limit per this article:
https://blogs.msdn.microsoft.com/sqlcat/2013/09/10/diagnosing-transaction-log-performance-issues-and-limits-of-the-log-manager/



