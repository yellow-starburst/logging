
1.	from Administrator PowerShellsession – disable PowerShellexecution policy

`set-executionpolicy bypass`

2.	Create a profile 

`New-Item –Path $Profile –Type File –Force`

3.	Edit the powershell file to act as a persistent startup commands 

Location = C:\Users\xyz\Documents\WindowsPowerShell

4. Next make desired changes to the text file which will automatically run the profile every time PowerShell is started. -

```
function prompt { "PS " + "$env:UserName" + "@$env:COMPUTERNAME\" + (Get-Item -Path ".\" -Verbose).name + " " + ($(Get-Date).toString("MM/dd/yyyy hh:mm:ss")) + ">" }
Start-Transcript -OutputDirectory C:\Users\xyz\Desktop\logs\
```
