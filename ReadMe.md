<h1 align="center">Linux Logging</h1>

&nbsp;
&nbsp;
# 1. Time Stamping the Terminal
## Option 1. Modify ZSH - great for kali
Note - Keep in mind you would have to run this works for 1 specific user. So you likely want to set it up for the desired user and for the root user.
Step 1. Edit zhrc file
`nano ~/.zshrc`

Step 2. Find this part of the file 
![image](https://github.com/user-attachments/assets/5c556dc6-cc0f-46b7-a02e-9a7235e0453c)

Look for `PROMPT=$'%F{` 
Replace with
```
PROMPT=$'%F{%(#.blue.green)}┌──${debian_chroot:+($debian_chroot)─}${VIRTUAL_ENV:+($(basename $VIRTUAL_ENV))─}(%B%F{%(#.red.blue)}%n'$prompt_symbol$'%m%b%F{%(#.blue.green)})-[%B%F{reset}%(6~.%-1~/…/%4~.%5~)%b%F{%(#.blue.green)}] [%F{yellow}%D{%m-%d-%Y} %T%F{%(#.blue.green)}]\n└─%B%(#.%F{red}#.%F{blue}$)%b%F{reset} '
```

Step 3. sync terminal
```
source ~/.zshrc
```

## Option 2.Modify bashrc 
Step 1. Modify bashrc
```
nano ~/.bashrc 
```
Step 2. Find the last PS1 text file and replace it with this: 

```
PS1='[`date  +"%b-%d-%y %T"`] > '
```

&nbsp;
&nbsp;

# 2. Logging terminal input/output

## Option 1. Script 
Problem - It needs a program like "aha" to convert the log files to readable text. 

Step 1. Either edit the bashrc or zshrc

Step 2. Add this to the last line
```
test "$(ps -ocommand= -p $PPID | awk '{print $1}')" == 'script' || (script -f $HOME/$(date +"%d-%b-%y_%H-%M-%S")_shell.log)
```

Step 3. Install this tool - it is useful to convert the log file to readable text
```
apt-get install aha -y
```


## Option 2. Putty Logging

![image](https://github.com/user-attachments/assets/cc9b2663-d49e-409b-ab8a-6c7492563f44)

Step 0. Edit the correct profile
Step 1. Go to Session > Logging
Step 2. Select all session output
Step 3. Select desired folder and file name
Step 4. Select Always append to end of it
Step 5. Deselect flush log file frequently and Omit fields. Select "Include Header"

&nbsp;
&nbsp;
# 3. Specific tool logging - Metasploit

Step 1. Check if this folder exists.
`ls ~/.msf4` 

Step 2. If folder does not exist run this command 
`mkdir ~/.msf4` 


Step 3. Create msfconsole run file
```
echo "spool /root/metasploit.log" > ~/.msf4/msfconsole.rc

echo "setg prompt [%T] %L" >> ~/.msf4/msfconsole.rc

echo "setg PromptTimeFormat %m/%d/%Y %H:%M" >> ~/.msf4/msfconsole.rc

echo "setg ConsoleLogging true" >> ~/.msf4/msfconsole.rc

echo "setg LogLevel 5" >> ~/.msf4/msfconsole.rc

echo "setg SessionLogging true" >> ~/.msf4/msfconsole.rc

echo "setg TimestampOutput true" >> ~/.msf4/msfconsole.rc

```


<h1 align="center">Windows Logging</h1>

## 1. Setup Timestamp and Logging (AKA "Transcript")  
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
Start-Transcript -OutputDirectory $HOME\Documents\1_logs\
```


If you are lazy:

```
New-Item –Path $Profile –Type File –Force
mkdir $HOME\Documents\1_logs\
echo 'function prompt { "PS " + "$env:UserName" + "@$env:COMPUTERNAME\" + (Get-Item -Path ".\" -Verbose).name + " " + ($(Get-Date).toString("MM/dd/yyyy hh:mm:ss")) + ">" }' > ~\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1
echo "Start-Transcript -OutputDirectory $HOME\Documents\1_logs\" >> ~\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1


```

