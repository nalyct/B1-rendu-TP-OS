## 2. Mémoire et CPU
## a. 
```
PS C:\> Get-CimInstance -ClassName Win32_OperatingSystem | Select-Object TotalVisibleMemorySize, FreePhysicalMemory
>>

TotalVisibleMemorySize FreePhysicalMemory
---------------------- ------------------
               7914772            1014224
```
## b. 

```
PS C:\> Get-CimInstance -ClassName Win32_Processor | Select-Object -Property LoadPercentage
>>

LoadPercentage
--------------
             9
```
