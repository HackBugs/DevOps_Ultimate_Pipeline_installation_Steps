________________________________________________________________________________________________________________________________

## Start Services of these DevOps tools
```
- docker ps -a
```
```
- docker start sonar
```
```
- docker start Nexus
```

## Nexus and SonarQube Start docker container
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

## Nexus and SonarQube
```
- docker logs sonar
```
```
- docker logs Nexus
```

## jenkins
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

## Systemd:
#### Start Prometheus service
```
sudo systemctl start prometheus
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

## Docker:
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

## Start Localhost IP-address:Port
- http://192.168.43.72:8081/  Nexus
- http://192.168.43.72:9000/ SonarQube
- http://192.168.43.72:8080/ Jenkins
- http://192.168.43.72:9090/ Prometheus
- http://192.168.43.72:3000/ Grafana
__________________________________________________________________________________________________________________________________________________________
