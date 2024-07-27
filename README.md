---
Created: 2024-07-27T19:51:17+05:30
Updated: 2024-07-27T20:02:09+05:30
Maintainer: Ibrar Ansari
---
# 1. Installing Jenkins

First, update the default Ubuntu packages lists for upgrades with the following command:
```bash
sudo apt-get update
```
Then, run the following command to install JDK 11:
```bash
sudo apt-get install openjdk-11-jdk
```
Now, we will install Jenkins itself. Issue the following four commands in sequence to initiate the installation from the Jenkins repository:
```bash
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null

echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null

sudo apt-get update

sudo apt-get install jenkins
```
Once that’s done, start the Jenkins service with the following command:
```bash
sudo systemctl start jenkins.service
```
To confirm its status, use:
```bash
sudo systemctl status jenkins
```
With Jenkins installed, we can proceed with adjusting the firewall settings. By default, Jenkins will run on port 8080.

In order to ensure that this port is accessible, we will need to configure the built-in Ubuntu firewall (ufw). To open the 8080 port and enable the firewall, use the following commands:
```bash
sudo ufw allow 8080
```
```bash
sudo ufw enable
```
Once done, test whether the firewall is active using this command:
```bash
sudo ufw status
```

To check the initial password, use the cat command as indicated below:
```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

Login to Jenkins using the your IP with above token:
```
http://<Public_IP>:8080 
```

All Set! You can now start automating...


### 💼 Connect with me 👇👇 😊

- 🔥 [**Youtube**](https://www.youtube.com/@DevOpsinAction?sub_confirmation=1)
- ✍ [**Blog**](https://ibraransari.blogspot.com/)
- 💼 [**LinkedIn**](https://www.linkedin.com/in/ansariibrar/)
- 👨‍💻 [**Github**](https://github.com/meibraransari?tab=repositories)
- 💬 [**Telegram**](https://t.me/DevOpsinActionTelegram)
- 🐳 [**Docker**](https://hub.docker.com/u/ibraransaridocker)