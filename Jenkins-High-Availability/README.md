---
Created: 2024-07-27T20:04:28+05:30
Updated: 2024-07-27T20:08:16+05:30
Maintainer: Ibrar Ansari
---
# Step 1: Install Jenkins on two node

> Follow setup guide already provided.

# Step 2: Set Up Shared Storage
```
sudo apt-get install nfs-kernel-server
sudo mkdir -p /srv/nfs/jenkins
sudo chown nobody:nogroup /srv/nfs/jenkins
sudo chmod 777 /srv/nfs/jenkins
/srv/nfs/jenkins 192.168.1.0/24(rw,sync,no_subtree_check)
sudo exportfs -a
sudo apt-get install nfs-common
sudo mkdir -p /mnt/jenkins
sudo mount -t nfs <NFS_SERVER_IP>:/srv/nfs/jenkins /mnt/jenkins
<NFS_SERVER_IP>:/srv/nfs/jenkins /mnt/jenkins nfs defaults 0 0
JENKINS_HOME=/mnt/jenkins
```

# Step 3: Install and Configure HAProxy

```
sudo apt-get install haproxy
sudo systemctl enable haproxy
sudo systemctl start haproxy

sudo vim /etc/haproxy/haproxy.cfg
frontend jenkins_front
	bind *:8080
	default_backend jenkins_back

backend jenkins_back
	balance roundrobin
	server jenkins_master1 <JENKINS_MASTER1_IP>:8080 check
	server jenkins_master2 <JENKINS_MASTER2_IP>:8080 check
```
# Step 4: Test the Setup
- *Access Jenkins:* Open your web browser and go to http://<HAPROXY_SERVER_IP>:8080. You should be routed to one of the Jenkins master instances.
- *Failover Test:* Stop one of the Jenkins master servers and verify that HAProxy correctly routes requests to the remaining active Jenkins master.
# Step 5: Monitoring and Logging
- Set up monitoring for HAProxy using tools like Prometheus and Grafana or other logging solutions like ELK (Elasticsearch, Logstash, Kibana) for better insights into the performance and health of your Jenkins HA setup.


### 💼 Connect with me 👇👇 😊

- 🔥 [**Youtube**](https://www.youtube.com/@DevOpsinAction?sub_confirmation=1)
- ✍ [**Blog**](https://ibraransari.blogspot.com/)
- 💼 [**LinkedIn**](https://www.linkedin.com/in/ansariibrar/)
- 👨‍💻 [**Github**](https://github.com/meibraransari?tab=repositories)
- 💬 [**Telegram**](https://t.me/DevOpsinActionTelegram)
- 🐳 [**Docker**](https://hub.docker.com/u/ibraransaridocker)