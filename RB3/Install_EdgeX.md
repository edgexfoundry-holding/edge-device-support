# Install EdgeX on the Raspberry PI Device

[![README](https://img.shields.io/badge/%E4%B8%AD%E6%96%87-brightgreen)](./Install_EdgeX_CN.md)
[![README](https://img.shields.io/badge/Contents-blue)](./README.md)

## Introduction to Installation Method
Edgex can be installed in two ways.<br>
1. Compile from source code  <br>
2. Deployment based on container  <br>

Reference from:<br>
https://github.com/edgexfoundry <br>
https://docs.edgexfoundry.org/1.2/getting-started/quick-start/ <br>

The following is a quick installation guide based on the container.<br>

## Install the Docker
Reference resources: https://docs.docker.com/get-docker/ <br>
Choose the installation scheme of Arm64 architecture.  <br>
 ![image](./images/1.png)

### Uninstall Old Versions
```
$ sudo apt-get remove docker docker-engine docker.io containerd runc
```
### Set Up the Repository
1. Update the apt package index and install packages to allow apt to use a repository over HTTPS: <br>
```
$ sudo apt-get update
$ sudo apt-get install \
	apt-transport-https \
	ca-certificates \
	curl \
	gnupg-agent \
	software-properties-common
```
2. Add Docker’s official GPG key:
```
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```
Verify that you now have the key with the fingerprint 9DC8 5822 9FC7 DD38 854A E2D8 8D81 803C 0EBF CD88, by searching for the last 8 characters of the fingerprint. <br>
```
$ sudo apt-key fingerprint 0EBFCD88
"""
pub  rsa4096 2017-02-22 [SCEA]
9DC8 5822 9FC7 DD38 854A E2D8 8D81 803C 0EBF CD88
uid      [ unknown] Docker Release (CE deb) <docker@docker.com>
sub  rsa4096 2017-02-22 [S]
"""
```
3. Use the following command to set up the stable repository.  <br>
```
$ sudo add-apt-repository \
	"deb [arch=arm64] https://download.docker.com/linux/ubuntu \
	$(lsb_release -cs) \
	stable"
```
### Install Docker Engine
1. Update the apt package index, and install the latest version of Docker Engine, or go to the next step to install a specific version:
```
$ sudo apt-get update
$ sudo apt-get install docker-ce docker-ce-cli containerd.io
```
2. Verify that Docker Engine is installed correctly by running the hello-world image.
```
$ sudo docker run hello-world
```
This command downloads a test image and runs it in a container. When the container runs, it prints an informational message and exits.<br>
## Install docker-compose
Open the terminal and execute the following command
```
$ sudo apt install docker-compose
```
If the system version is below ubuntu20.04, the version of docker-compose that installed by apt might be too old to deploy EdgeX. <br>
Install pip3.<br>
```
$ sudo apt install python3-pip libffi-dev
```
Install the docker - compose.<br>
```
$ sudo pip3 install docker-compose
```
 Show docker-compose version.<br>
```
$ docker-compose -v
"""
docker-compose version 1.xx.x, build unknown
"""
```

## Running EdgeX
Once Docker and Docker Compose are installed.<br>
Download the yaml file of the Geneva version for EdgeX deployment.<br>
You can get all versions of the deployment script here: https://raw.githubusercontent.com/edgexfoundry/developer-scripts/master/releases/geneva/compose-files/docker-compose-geneva-redis-no-secty.yml <br>

```buildoutcfg
$ curl https://raw.githubusercontent.com/edgexfoundry/developer-scripts/master/releases/geneva/compose-files/docker-compose-geneva-redis-no-secty.yml -o docker-compose.yml; 
```

Open the file and modify it after downloading.<br>
1.Release comments of device-mqtt.<br>
2.Add mount: ./device/mqtt:/res/docker under volumes.<br>
3.Add the mqtt-broker module as follows.<br>

```buildoutcfg
  mqtt-broker:
    image: eclipse-mosquitto
    ports:
      - "1883:1883"
    container_name: mqtt-broker
    hostname: mqtt-broker
    networks:
      edgex-network:
        aliases:
            - mqtt-broker
```

The final overall modification results are shown in the figure below.<br>

![image](./images/5.png)

Start the EdgeX container.<br>

```buildoutcfg
$ sudo docker-compose up -d
```

 ![image](./images/2.png)
 
Verify that the EdgeX container is activated.<br>
 
 ```buildoutcfg
$sudo docker-compose ps
```

![image](./images/3.png)

[![README](https://img.shields.io/badge/Deploy_and_start_the_program_Device_on_Rb3-yellow)](./Run_Device.md)