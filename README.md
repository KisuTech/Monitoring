## Docker container and Virutal machine Monitoring using Prometheus

**This project sets up two Virtual Machines (VMs) with Ubuntu using VMware or VirtualBox.One VM will have Docker installed for running sample containers,while the other will be used for monitoring system resources using Grafana and Prometheus exporters**

## Prerequisites
- VMware or VirtualBox installed
- Ubuntu ISO files for creating VMs(VM-2)
- Internet connection for downloading software and dependencies

## VM-1 Setup (With Docker)   
1. Install Docker on VM-1:(Windows)
   ```bash
   $ "Docker Desktop Installer.exe" install
   $ Start-Process 'Docker Desktop Installer.exe' -Wait install
   $ start /w "" "Docker Desktop Installer.exe" install
   $ Start Docker Desktop
   
## Program Setup   
1.<b> Write the yaml file for the prometheus with cadvisor and grafana</b>
   - cadvisor is running on port:"write your ip address here":8081
   - Prometheus is running on port:"write your ip address here":9090
   - grafana is running on the port:"write your ip address here":3000
   
2.<b> Write Docker Compose file for the grafana,prometheus,cadviser</b>
   - Here the Prometheus is depend upon the cadvidor(Cadviser helps to analyze the docker container Resources)

3.<b>Run containers using the `docker compose up` command.</b>
   
4.<b>Grafana Dashboard Monitoring</b>
   - Go to Grafana Dashboard on the port:3000(`localhost:3000`)
   - Add the data Source as the Prometheus and give the Port as(`http://"your ip":9090`)
   - After Adding the data Source iport the dashboard(cadvisor Exporter ID:14282)
   - Analyze the Docker Conatainer Resources.
   
## Set up  alerts for Docker
   1.If Container is down
      $ Save the file
      $ Goto The alert
      $ Go the code section
      $ write the "Query(time()-timestamp(container_last_seen{name="task-node_exporter-1"}))"
      $Go to the 
   2.If Cpu uses is More Than 60%
      $ Save the file
      $ Go to the Three dot of Cpu Analyzer
      $ Goto more Section Add Altering Run the Query and set the threshold value above 60%

## VM-2 Setup (With Docker)   
1. Install Docker on VM-2:(ubuntu)
   # Add Docker's official GPG key:
       ``` Terminal
       $ sudo apt-get update
       $ sudo apt-get install ca-certificates curl
       $ sudo install -m 0755 -d /etc/apt/keyrings
       $ sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
       $ sudo chmod a+r /etc/apt/keyrings/docker.asc
      
   # Add the repository to Apt sources:
       $ echo \
       "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
       $ (. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
       $ sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
       $ sudo apt-get update
      
   # Install Docker
       $ sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
      
   # Verify that the Docker Engine installation
       $ sudo docker run hello-world
   
## Program Setup   
1.<b>Write the yaml file for the prometheus with Node-exporter and grafana</b>
   - Node is running on port:"write your ip address here":9100
   - Prometheus is running on port:"write your ip address here":9090
   - grafana is running on the port:"write your ip address here":3000
   
2.<b>Write Docker Compose file for the grafana,prometheus,cadviser</b>
   - Here the Prometheus is depend upon the Node-exporter(Node-exporter helps to analyze the VM Resources{cpu,memory})

3.<b>Run containers using the `docker compose up` command.</b>
   
4.<b>Grafana Dashboard Monitoring</b>
   - Go to Grafana Dashboard on the port:3000(localhost:3000)
   - Add the data Source as the Prometheus and give the Port as(http://"your ip":9090)
   - After Adding the data Source import the dashboard(Node-Exporter ID:1860)
   - Analyze the VM Resources.
   
## Set up  alerts for Docker
   1.If Container is down
      $ Save the file->Goto The alert->Go the code section->write the Query(time()-timestamp(container_last_seen{name="task-node_exporter-1"}))
        ->
      $Go to the 
   2.If Cpu uses is More Than 60%
      $ Save the file->Go to the Three dot of Cpu Analyzer->Goto more Section Add Altering Run the Query and set the threshold value above 60%
   
      
   




