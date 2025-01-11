<h1 align="center">Basic Changes</h1>

# 1. Change hostname
1. `sudo nano /etc/hostname`
2. `sudo nano /etc/hosts`
3. `sudo systemctl restart systemd-hostnamed`


# 2. Change Password

1. Change username

`passwd kali`

2. Change root password

`passwd root`



<h1 align="center">Install Tools</h1>


# 1. Initial

Notes
1. Make sure you are careful what user you are running as. If you run as root, it will break the python tools.
2. Be careful installing python based tools. Ideally you should install in a sandbox.  


## Basic tool updates
```
sudo apt-get update
sudo apt-get dist-upgrade
```

## Tool Install
```
apt install docker-cli -y
apt-get install python3-poetry -y
apt-get install pipx

```

## Golang
Golang is a massive pain to correctly install. Be extremely careful to set it up correctly. This is how to do it the apt-get install route. 
```
sudo apt install -y golang
echo "export GOROOT=/usr/lib/go" >> ~/.zshrc
echo "export GOPATH=$HOME/go" >> ~/.zshrc
echo "export PATH=$GOPATH/bin:$GOROOT/bin:$PATH" >> ~/.zshrc
```


## Virtual Enviornment Knowledge
3 methods - virtualenv and poetry

1. VirtualEnv

```
virtualenv venv
source venv/bin/activate
```

2. Poetry
To run python files prepend `poetry run` to the command
```
poetry install
poetry shell
```


3. Pipx - easiest
Keep in mind that you should keep track of the command to run the tool. Like for scoutsuite its "scout".
```
pipx install toolxyz
```

# AWS Pentest Tools

1. Pacu
2. Prowler
3. Cloudsploit
4. Cloudfox
5. Scoutsuite

&nbsp;


## New Way

Step 1. Install Tools
```
pipx install pacu
pipx install prowler
pipx install cloudsploit
pipx install ScoutSuite
pipx install trufflehog
```





Step 2. Activate Tools 

Step 3. Intall missing tools

<h2 align="center">Step 3. Intall missing tools</h2>

1. CloudFox
2. Gitleaks
3. Microburst
4. Azure_hound and bloodhound
5. roadrecon - I'm not a big fan
6. o365enum
7. Scubagear - from cisa
8. CrowdStrike Reporting Tool for Azure (CRT)


CloudFox

```
git clone  https://github.com/BishopFox/cloudfox.git "/opt/$(basename -s .git https://github.com/BishopFox/cloudfox.git)"
cd cloudfox
go build .
```

Trivy
```
apt-get install trivy
```

<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>


## Old-way Tool Download

```
git clone https://github.com/RhinoSecurityLabs/pacu.git "/opt/$(basename -s .git https://github.com/RhinoSecurityLabs/pacu.git)"
git clone  https://github.com/prowler-cloud/prowler.git "/opt/$(basename -s .git https://github.com/prowler-cloud/prowler.git)"
git clone  https://github.com/aquasecurity/cloudsploit.git "/opt/$(basename -s .git https://github.com/aquasecurity/cloudsploit.git)"
git clone  https://github.com/BishopFox/cloudfox.git "/opt/$(basename -s .git https://github.com/BishopFox/cloudfox.git)"
git clone  https://github.com/nccgroup/ScoutSuite.git "/opt/$(basename -s .git https://github.com/nccgroup/ScoutSuite.git)"

```


1. Pacu 

```
apt-get install pacu
cd pacu
python3 -m venv venv && source venv/bin/activate
pip install -U pacu
```

2. Prowler
```
git clone  https://github.com/prowler-cloud/prowler "/opt/$(basename -s .git https://github.com/prowler-cloud/prowler)"
cd prowler
sudo poetry install
poetry shell
poetry run python prowler.py -v
```

3. Etc. 
