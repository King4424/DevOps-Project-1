![svg xmlns=httpwww w3 org2000svg x=0px y=0px width=100 height=100 viewBox=0 0 48 48 path fill=#424242 d=M44,24c0,11 045-8 955,20-20,20S4,35 045,4,24S12 955,4,24,4S44,12 955,44,24zpathpath fill=#fff](https://github.com/user-attachments/assets/10734933-7c0f-4df2-a0b3-d7f96f58f1e5)


# AIM: 
## *Cloning HTML file from GitHub to Jenkins-server building job using Ansible and deploying HTML file to remote web-server, A Complete CI/CD Automation Project. *

## STEPS:
**1. Launch 3 Servers (Linux)**
   1) Jenkins-server - t2.small
   2) Ansible-server - t2.micro
   3) Web-server (Apache) - t2.micro

**2. Connect all 3 servers with terminal**

 Change hostname of all three servers unsing for easy identification of servers. as following = 
```
hostnamectl set-hostname jenkins-server
bash
```
**3. Enable Password Authentication on all 3 servers and set password**
```
passwd root
```
**now enable password authentication on all 3 servers**
**uncomment permit root login to yes and Passwordauthentication yes (save file)**
```
nano /etc/ssh/sshd_config
```
**4. Now to connect all 3 servers with ssh, generate key**
**generate key on Jenkins-server and on Ansible-server so Jenkins server will connected to Ansible-server and Ansible-server will be connected to Web-server**
```
#do this on jenkins-server
ssh-keygen
```
```
#do this on Jenkins server
ssh-copy-id root@private ip of Ansible-server
```
```
#do this on ansible-server
ssh-keygen
```
```
#do this on ansible server
ssh-copy-id root@private ip of web-server
```
**5. Install Java-17, Git and jenkins on jenkins-server**
```
sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
```

```
yum install fontconfig java-17-openjdk
```

```
yum install jenkins -y
```

```
yum install git -y
```
**6. On Ansible Server install epel (package manager) and Ansible**

```
amazon-linux-extras install epel -y
```

```
yum install ansible -y
```
**7. on web server install apache (httpd)**
```
yum install httpd -y
```
**8. start services of Jenkins and Apache on their servers**
```
systemctl start jenkins
systemctl enable jenkins
systemctl status jenkins
```

```
systemctl start httpd
systemctl enable httpd
systemctl status httpd
```

**9. Launch Jenkins Dashboard on browser using their public ip on port number 8080 and configure it and install publish over ssh plugin**

**10. Login to GitHub account and create one repository and create one Index.html file**


