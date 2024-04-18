**Docker container monitoring usig Prometheus Exporter**

# This project sets up two Virtual Machines (VMs) with Ubuntu using VMware or VirtualBox.One VM will have Docker installed for running sample containers,while the other will be used for monitoring resources using Grafana and Prometheus exporters

## Prerequisites
- VMware or VirtualBox installed
- Ubuntu ISO files for creating VMs
- Internet connection for downloading software and dependencies

## VM-1 Setup (With Docker)

1. Create VM-1 using VMware or VirtualBox with Ubuntu OS.
   
2. Install Docker on VM-1:
   ```bash
   $ "Docker Desktop Installer.exe" install
   $ Start-Process 'Docker Desktop Installer.exe' -Wait install
   $ start /w "" "Docker Desktop Installer.exe" install
   $ Start Docker Desktop
   
3. Write the yaml file for the prometheus with cadvisor and prometheus
   $ cadvisor is running on port:"write your ip addres here":8081
   $ Prometheus is running 



