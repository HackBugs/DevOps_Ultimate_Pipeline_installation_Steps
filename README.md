
## 🛠️ After Reboot Virtul Machine or Reboot Your System use these CMD to run Service Again.

> Author : ✍️ HackBugs

<hr>

Check Port and update ports

```sh
Check which program is running this port
sudo lsof -i :9043
sudo netstat -tulnp | grep 9043
sudo ss -tulnp | grep 9043
sudo fuser 9043/tcp

sudo ufw allow 9090/tcp - allows firewall traffic on port 9090:
cmd - netstat and ss and
cmd - sudo ethtool enp0s3
./prometheus --web.listen-address=":9043" &

sudo ufw status
sudo ufw enable
sudo ufw allow 9043/tcp
sudo ufw allow 9043/udp
sudo ufw deny 9043/tcp
```
```sh
#!/bin/bash

echo "Listing all active services:"
systemctl list-units --type=service

echo ""
echo "Listing all services including inactive ones:"
systemctl list-unit-files --type=service

echo ""
echo "Checking the status of a specific service (e.g., nginx):"
systemctl status nginx

echo ""
echo "Listing all services with their state (including stopped services):"
systemctl list-units --type=service --all

echo ""
echo "Listing all services and their dependencies:"
systemctl list-dependencies
```

> If you are running any script if you want to run backgrong use & like - `./blackbox_exporter &` and `./prometheus &`

<details><summary><b>✔️ Start Services of these DevOps tools</b></summary>
 
```
- docker ps -a
```
```
- docker start sonar
```
```
- docker start Nexus
```

## ✔️ Nexus and SonarQube Start docker container
```
- docker rm sonar
```
```
- docker rm Nexus
```
```
- docker run -d --name sonar -p 9000:9000 sonarqube:lts-community
```
```
- docker run -d --name Nexus -p 8081:8081 sonatype/nexus3
```

## ✔️ Nexus and SonarQube
```
- docker logs sonar
```
```
- docker logs Nexus
```

## ✔️ jenkins
```
- sudo systemctl start jenkins
```
```
- sudo systemctl enable jenkins
```
```
- sudo systemctl status jenkins
```
```
- sudo systemctl restart jenkins
```
```
- sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

## ✔️ Systemd:
#### Start Prometheus service

```
tar -xvf prometheus-2.54.0-rc.0.linux-amd64.tar.gz
cd > prometheus-2.54.0-rc.0.linux-amd64
./prometheus &
```
- After reboot Machine run only `./prometheus &`

- Blackbox Exporter same like Prometheus `./blackbox_exporter &`
```
tar -xvf blackbox_exporter-0.25.0.linux-amd64.tar.gz
cd > blackbox_exporter-0.25.0.linux-amd64 
./prometheus &
```
```
sudo systemctl stop prometheus
sudo systemctl start prometheus
sudo systemctl daemon-reload
```

#### Start Grafana service
```
sudo systemctl start grafana-server
```
### OR
```
sudo /bin/systemctl start grafana-server
```

### If BlackBox_exporter is not running on prot 9115 than we can use other PORT  as you want of BlackBox_exporter
```
./consul_exporter --web.listen-address=":9108" &
```


#### Check status
```
sudo systemctl status prometheus
sudo systemctl status grafana-server
```

#### Enable services to start on boot
```
sudo systemctl enable prometheus
sudo systemctl enable grafana-server
```

#### Logs Check:
```
sudo journalctl -u prometheus
sudo journalctl -u grafana-server
```

## ✔️ Docker Start docker container of - Prometheus, Grafana, Sonar, Nexus

```
#### Check running containers
docker ps -a
```

```
docker start prometheus
```
```
docker start grafana
```
```
docker start sonar
```
```
docker start Nexus
```
#### Logs Check:
```
docker logs prometheus
docker logs grafana
```
</details>
<details><summary><b>✔️ (Minikube) - Kubernetes Orchestration</b></summary>

- Minikube > Kubeadm > kubelet > kubectl
 
1. Restart Minikube
 
 ```sh
 minikube stop
 minikube start --driver=docker
 ```
2. Restart kubeadm
 ```
 kubeadm reset
 kubeadm init
 ```
3. Restart kubelet
 ```
 sudo systemctl restart kubelet
 ```
4. Restart kubectl
 ```sh
 kubectl config view
 kubectl config use-context <context-name>
  
 ```
 ```sh
 # For Linux
 curl -LO "https://dl.k8s.io/release/v1.27.1/bin/linux/amd64/kubectl"
 chmod +x ./kubectl
 sudo mv ./kubectl /usr/local/bin/kubectl

 # Verify installation
 kubectl version --client
 ```
</details>

<details><summary><b>✔️ After Restart your Ubuntu machine and run `minikube start --force`. If unable to start , try the command.</b></summary>
 
The error message indicates multiple issues when Minikube attempts to start with the Docker driver. Here’s a breakdown of the errors and how to address them:

### 1. **Root Privileges Issue**

You’re running Minikube with root privileges, which is not recommended for the Docker driver. Minikube should be run as a regular user. If you’re currently logged in as root, switch to a non-root user and try starting Minikube again.

### 2. **Docker Container Missing**

Minikube is trying to create a Docker container but is encountering issues. Ensure Docker is correctly set up and running on your system.

### 3. **Certificates Issue**

The error message about certificates (`certificate apiserver-kubelet-client not signed by CA certificate ca`) suggests a problem with Kubernetes certificate generation. This is often due to issues with the Minikube setup or conflicts with existing files.

### Steps to Resolve:

1. **Switch to Non-Root User:**
   - Log out from the root user and log in with your regular user account. Ensure that your user is part of the `docker` group.
     ```bash
     sudo usermod -aG docker $USER
     ```
   - After adding your user to the `docker` group, log out and log back in.

2. **Clean Up Existing Minikube Data:**
   - Sometimes, cleaning up existing Minikube data can resolve issues:
     ```bash
     minikube delete
     sudo rm -rf /var/lib/minikube
     ```

3. **Start Minikube with the Docker Driver:**
   - Start Minikube using the Docker driver as a non-root user:
     ```bash
     minikube start --driver=docker
     ```

4. **Check System Requirements:**
   - Make sure your system meets the necessary requirements. Verify the kernel version and system configurations:
     ```bash
     uname -r
     ```

5. **Verify Docker and Kubernetes Setup:**
   - Ensure Docker is correctly installed and running. You can restart Docker if needed:
     ```bash
     sudo systemctl restart docker
     ```

6. **Check Minikube Logs for More Details:**
   - If problems persist, check Minikube logs for more details:
     ```bash
     minikube logs --file=logs.txt
     ```

7. **Consider Using the `none` Driver:**
   - If running Minikube within a VM, you might need to use the `none` driver:
     ```bash
     minikube start --driver=none
     ```

### Additional Resources

If you continue facing issues, consider checking the Minikube documentation or filing an issue on the [Minikube GitHub page](https://github.com/kubernetes/minikube/issues). 
</details>

<details><summary><b>✔️ After a reboot, you'll need to start Minikube again to get your Kubernetes cluster up and running.</b></summary>


### 1. **Start Minikube**

Run the following command to start Minikube:
```bash
minikube start
```

This will start the Minikube cluster with the previously used configuration.

### 2. **Check Minikube Status**

After starting Minikube, check the status to ensure everything is running correctly:
```bash
minikube status
```

### 3. **If Minikube Does Not Start**

If Minikube does not start properly, you might need to troubleshoot or reinitialize it:

#### **Delete and Recreate Minikube Cluster**
If you encounter persistent issues, you can delete the existing Minikube cluster and start a new one:

1. **Delete Minikube Cluster:**
   ```bash
   minikube delete
   ```

2. **Start a New Minikube Cluster:**
   ```bash
   minikube start
   ```

### Additional Tips

- **Check Docker Status**: Ensure that Docker is running properly as Minikube relies on Docker for its operation:
  ```bash
  sudo systemctl status docker
  ```

- **Check Minikube Logs**: If you encounter issues starting Minikube, you can check the logs for more information:
  ```bash
  minikube logs
  ```

- **Configure Minikube to Start on Boot**: If you want Minikube to start automatically after a reboot, you can create a systemd service. This requires creating a service file in `/etc/systemd/system/` and configuring it to run Minikube start commands.

### Example Systemd Service File

1. **Create a Service File**:
   ```bash
   sudo nano /etc/systemd/system/minikube.service
   ```

2. **Add the Following Content**:
   ```ini
   [Unit]
   Description=Minikube Service
   After=docker.service
   Requires=docker.service

   [Service]
   User=$USER
   ExecStart=/usr/local/bin/minikube start --driver=docker
   ExecStop=/usr/local/bin/minikube stop
   Restart=always

   [Install]
   WantedBy=multi-user.target
   ```

   Replace `$USER` with your actual username.

3. **Reload systemd and Enable the Service**:
   ```bash
   sudo systemctl daemon-reload
   sudo systemctl enable minikube
   ```

4. **Start Minikube Service**:
   ```bash
   sudo systemctl start minikube
   ```

By following these steps, you should be able to manage Minikube effectively after a reboot.

</details>

<details><summary><b>✔️ Start Localhost IP-address:Port - Use your IP</b></summary>
 
- http://192.168.43.72:8081/  Nexus
- http://192.168.43.72:9000/ SonarQube
- http://192.168.43.72:8080/ Jenkins
- http://192.168.43.72:9090/ Prometheus
- http://192.168.43.72:3000/ Grafana
- http://192.168.43.72:9115/ Blackbox Exporter

</details>

<details><summary><b> ✍️ Installation Setups Process DevOps Project</b></summary>

## AWS - VPC 
## AWS Network Environment setup
EC2 > Security Groups > launch-wizard-2 > Edit inbound rules
  - Private
  - Isolated environment
  - Deployment will secure
  - ![inbound rules](https://github.com/jaiswaladi246/DevOps_Shack_Ultimate_Pipeline_12_march/blob/main/PHASE-1/Screenshot%202024-03-13%20002123.png)

#### Create this all EC2 Instances

**EC2 > Number of instances - 3 > Ubuntu Server 22.4 > t2.medium > Configure storage 25 GB**
- [Insatll kubernetes orchestration](https://github.com/HackBugs/DevOps_Shack_Ultimate_Pipeline_12_march/blob/main/PHASE-1/2.%20K8-Setup.md)
 - Master - EC2-1
 - Slave1 - EC2-2
 - Slave2 - EC2-3

**EC2 > Number of instances - 2 > Ubuntu Server 22.4 > t2.medium > Configure storage 20 GB**
- SonarQube - EC2-5
- Nexus - EC2-6

**EC2 > Number of instances - 1 > Ubuntu Server 22.4 > t2.large > Configure storage 30 GB**
- Jenkins - EC2-4

**EC2 > Number of instances - 1 > Ubuntu Server 22.4 > t2.large > Configure storage 20 GB**
- For Monitoring - EC2-7
    - [Prometheus](https://prometheus.io/download/)
        - [Blackbox-exporter](https://prometheus.io/download/)
    - [Grafana](https://grafana.com/grafana/download)
 
## Downlaod Packeges use with script
```sh
vi 1.sh > Paste inside if have more installation pkg
chmod +x 1sh - Change permissions to executable 
./1.sh - execute run script
```
      
## Install Plugins in Jenkins for this Project
####  After Installation And configure inside | Jenkins > Tools
  - JDK - Eclipse Temurin installer
  - Maven Integration
  - Maven - Config File Provider
  - Maven - Pipeline Maven Integration
  - Sonar - SonarQube Scanner - This is tool
  - Sonar - sonarQube server
  - Docker
  - Docker Pipeline
  - Docker-Build-step
  - Kubernetes
  - Kubernetes CLI
  - Kubernetes Client API
  - Kubernetes Credentials
</details>
<details><summary><b> ✍️ Requred EC2 Instance installtion cmd of SonarQube & Nexus</b></summary>
 
### [Kubernetes install](https://github.com/HackBugs/DevOps_Shack_Ultimate_Pipeline_12_march-2/blob/main/PHASE-1/2.%20K8-Setup.md)
  - Master - EC2-1
  - Slave - EC2-2
  - Slave - EC2-3
### [Docker install on both](https://docs.docker.com/engine/install/ubuntu/)
- SonarQube - EC2-4
  ```sh
  docker run -d --name sonar -p 9000:9000 sonarqube:lts-community
  ```
- Nexus - EC2-5
  ```sh
  docker run -d --name Nexus -p 8081:8081 sonatype/nexus3
  ```
- jenkins - EC2-6
  - JDK
  - run installtion script of jenkins
  - install docker
### Install one EC2-7 machine all three tools
- Prometheus
- Blackbox-exporter
- Grafana
</details>
