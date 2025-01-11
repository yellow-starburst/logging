
# Time Stamping the Terminal
## Option 1. Modify ZSH - great for kali
Step 1. Edit zhrc file
`nano ~/.zshrc`

Step 2. Find this part of the file 
![image](https://github.com/user-attachments/assets/5c556dc6-cc0f-46b7-a02e-9a7235e0453c)

Look for `PROMPT=$'%F{` 
Replace with
`PROMPT=$'%F{%(#.blue.green)}┌──${debian_chroot:+($debian_chroot)─}${VIRTUAL_ENV:+($(basename $VIRTUAL_ENV))─}(%B%F{%(#.red.blue)}%n'$prompt_symbol$'%m%b%F{%(#.blue.green)})-[%B%F{reset}%(6~.%-1~/…/%4~.%5~)%b%F{%(#.blue.green)}] [%F{yellow}%D{%m-%d-%Y} %T%F{%(#.blue.green)}]\n└─%B%(#.%F{red}#.%F{blue}$)%b%F{reset} '`


## Option 2.Modify bashrc 
nano ~/.bashrc
PS1='[`date  +"%b-%d-%y %T"`] > '


test "$(ps -ocommand= -p $PPID | awk '{print $1}')" == 'script' || (script -f $HOME/$(date +"%d-%b-%y_%H-%M-%S")_shell.log)

apt-get install aha -y
ls ~/.msf4
mkdir ~/.msf4

echo "spool /root/metasploit.log" > ~/.msf4/msfconsole.rc

echo "setg prompt [%T] %L" >> ~/.msf4/msfconsole.rc

echo setg PromptTimeFormat %m/%d/%Y %H:%M >> ~/.msf4/msfconsole.rc

echo "setg ConsoleLogging true" >> ~/.msf4/msfconsole.rc

echo "setg LogLevel 5" >> ~/.msf4/msfconsole.rc

echo "setg SessionLogging true" >> ~/.msf4/msfconsole.rc

echo "setg TimestampOutput true" >> ~/.msf4/msfconsole.rc
