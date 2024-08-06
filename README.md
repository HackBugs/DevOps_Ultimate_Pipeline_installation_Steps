
# 🛠️ After Reboot Virtul Machine or Reboot Your System use these CMD to run Service Again.
- ## Author : ✍️ HackBugs
________________________________________________________________________________________________________________________________

## ✔️ Start Services of these DevOps tools
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
sudo systemctl start prometheus
sudo systemctl daemon-reload
```

#### Start Grafana service
```
sudo systemctl start grafana-server
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

## ✔️ Docker Start docker container
#### Start Prometheus container
```
docker start prometheus
```

#### Start Grafana container
```
docker start grafana
```

#### Check running containers
```
docker ps -a
```

#### Logs Check:
```
docker logs prometheus
docker logs grafana
```

## ✔️ kubernetes orchestration
- Minikube > Kubeadm > kubelet > kubectl
1. Restart Minikube
 ```
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
 ```
 kubectl config view
 kubectl config use-context <context-name>

 ```
 ```
 # For Linux
 curl -LO "https://dl.k8s.io/release/v1.27.1/bin/linux/amd64/kubectl"
 chmod +x ./kubectl
 sudo mv ./kubectl /usr/local/bin/kubectl

 # Verify installation
 kubectl version --client

   ```
## ✔️ Start Localhost IP-address:Port - Use your IP
- http://192.168.43.72:8081/  Nexus
- http://192.168.43.72:9000/ SonarQube
- http://192.168.43.72:8080/ Jenkins
- http://192.168.43.72:9090/ Prometheus
- http://192.168.43.72:3000/ Grafana
- http://192.168.43.72:9115/ Blackbox Exporter
__________________________________________________________________________________________________________________________________________________________

# ✍️ Installation Setups Process DevOps Project

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
______________________________________________________________________________________________________________________________________

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
______________________________________________________________________________________________________________________________________________

