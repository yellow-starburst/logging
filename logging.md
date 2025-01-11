
# Time Stamping the Terminal
## Option 1. Modify ZSH - great for kali
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
`source ~/.zshrc`

## Option 2.Modify bashrc 
`nano ~/.bashrc` 
Find the last PS1 text file and replace it with this: 
```
PS1='[`date  +"%b-%d-%y %T"`] > '
```

# Logging terminal input/output

## Option 1. Script 
Problem - It needs a program like "aha" to convert the log files to readable text. 

Step 1. Either edit the bashrc or zshrc

Step 2. Add this to the last line
```
test "$(ps -ocommand= -p $PPID | awk '{print $1}')" == 'script' || (script -f $HOME/$(date +"%d-%b-%y_%H-%M-%S")_shell.log)
```

Step 3. Install this tool - it is useful to convert the log file to readable text
`apt-get install aha -y`


## Option 2. Putty Logging


## Specific tool logging - Metasploit

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
