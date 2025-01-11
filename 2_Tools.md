<h1 align="center">Basic Changes</h1>

# 1. Change hostname
1. `sudo nano /etc/hostname`
2. `sudo nano /etc/hosts`
3. `sudo systemctl restart systemd-hostnamed`


# 2. Change Password

1. Change username

`passwd kali`

4. Change root password

`passwd root`



<h1 align="center">Install Tools</h1>


# 2. Initial
note - make sure you are careful what user you are running as. If you run as root, it will break the python tools. 

## Basic tool updates
```
apt-get update
apt-get dist-upgrade
```

## Tool Install
```
apt install docker-cli -y
apt-get install python3-poetry -y

```

## Golang
Golang is a massive pain to correctly install. Be extremely careful to set it up correctly. This is how to do it the apt-get install route. 
```
sudo apt install -y golang
echo "export GOROOT=/usr/lib/go" >> ~/.zshrc
echo "export GOPATH=$HOME/go" >> ~/.zshrc
echo "export PATH=$GOPATH/bin:$GOROOT/bin:$PATH" >> ~/.zshrc
```


# AWS Pentest Tools

1. Pacu
2. Prowler
3. Cloudsploit
4. Cloudfox
5. Scoutsuite

&nbsp;

## Tool Download

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
git clone https://github.com/RhinoSecurityLabs/pacu.git "/opt/$(basename -s .git https://github.com/RhinoSecurityLabs/pacu.git)"
```

2. Prowler
```
git clone  https://github.com/prowler-cloud/prowler "/opt/$(basename -s .git https://github.com/prowler-cloud/prowler)"
cd prowler
poetry install
poetry shell

```


3. cloudsploit

4. cloudfox


5. ScoutSuite
