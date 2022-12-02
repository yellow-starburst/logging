
1.	from Administrator PowerShellsession – disable PowerShellexecution policy

`set-executionpolicy bypass`

2.	Create a profile 

`New-Item –Path $Profile –Type File –Force`

3. Make directory


`mkdir ~\Documents\1_logs\`

4.	Edit the powershell file to act as a persistent startup commands 

Location = C:\Users\xyz\Documents\WindowsPowerShell

5. Next make desired changes to the text file which will automatically run the profile every time PowerShell is started. -

```
function prompt { "PS " + "$env:UserName" + "@$env:COMPUTERNAME\" + (Get-Item -Path ".\" -Verbose).name + " " + ($(Get-Date).toString("MM/dd/yyyy hh:mm:ss")) + ">" }
Start-Transcript -OutputDirectory ~\Documents\1_logs\
```


If you are lazy:

```
mkdir ~\Documents\1_logs\
echo ""function prompt { "PS " + "$env:UserName" + "@$env:COMPUTERNAME\" + (Get-Item -Path ".\" -Verbose).name + " " + ($(Get-Date).toString("MM/dd/yyyy hh:mm:ss")) + ">" }"" > ~\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1
echo "Start-Transcript -OutputDirectory ~\Documents\1_logs\" >> ~\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1


```
