# runAs administrator command cheatsheet

-Verb to run a command as administrator in windows powershell

## Command Description
Start-Process command can be used to launch powershell or another process with administrator access.

only available in powershell v4.0+ and Windows 8.1+

see [get-help](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.management/Start-Process) for details

## Usage
Basic usage with Start-Process command:

    c:> Start-Process powershell -Verb runAs

To run a script without entering the -Verb switch you can add the following if statement to prompt to run as administrator:

    if (!([Security.Principal.WindowsPrincipal][Security.Principal.WindowsIdentity]::GetCurrent()).IsInRole([Security.Principal.WindowsBuiltInRole] "Administrator")) { Start-Process powershell.exe "-NoProfile -ExecutionPolicy Bypass -File `"$PSCommandPath`"" -Verb RunAs; exit }

    # enter rest of your script now.
