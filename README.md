# How to add Prometheus and Grafana to Jenkins

**Step 1 : Add the Prometheus pluggin in Jenkins and configure it.**

![Prometheus_config](https://github.com/gakengabinatsume/DevOps2023/assets/141765846/ad2b35e7-eb6c-4c3f-8e8e-04f76863c9c3)

**Step 2 : Create the stack using Docker in the monitoring folder**

Files needed:
- docker-compose.yaml
- prometheus.yaml

```
mkdir monitoring
mv docker-compose.yaml monitoring
mkdir prometheus
mv prometheus.yaml prometheus
```
```
sudo docker-compose up -d
```
```
sudo docker-compose ps
```
![docker compose up](https://github.com/gakengabinatsume/DevOps2023/assets/141765846/ddb127e7-2b8e-4f6a-8283-070c004cfc21)

**Step 3 : Configure Prometheus on the localhost**

-Modify the IP address on the prometheus.yml file for jenkins_job with the global dynamic one 
```
sudo ip addr | inet
```
![IP addr](https://github.com/gakengabinatsume/DevOps2023/assets/141765846/31db5b46-2393-469e-906a-2266bb9d22cf)

-Restart docker compose and make sure the Targets are up in Prometheus (localhost:9090/targets)
```
sudo docker-compose restart
```
![Targets](https://github.com/gakengabinatsume/DevOps2023/assets/141765846/1cce0bd9-c3b3-4c5a-a4a5-dd0905a3ec84)

**Step 4 : Configure Grafana on the localhost**

-Log into Grafana (localhost:3000) using admin as initial user and password

![log in](https://github.com/gakengabinatsume/DevOps2023/assets/141765846/78a9a91b-6285-443d-a1e8-0c52d4c5a164)

-Add data source from Prometheus in Grafana

![Data source](https://github.com/gakengabinatsume/DevOps2023/assets/141765846/6b673e73-273d-486a-8443-bb9721e5a140)

-Search for a grafana dashbord model and import it

![Import dashbord](https://github.com/gakengabinatsume/DevOps2023/assets/141765846/5dc877ab-7c7d-4e96-8f85-87e54e597797)

![Dashbord](https://github.com/gakengabinatsume/DevOps2023/assets/141765846/a6b5a143-a9d2-4e17-9a59-04c5964880f7)

**Step 5 : Close Prometheus and Grafana**

`sudo docker-compose down`

