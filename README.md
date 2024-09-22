# new-jenkins

pipeline test

[![Build Status](http://ec2-34-244-30-52.eu-west-1.compute.amazonaws.com:8080/buildStatus/icon?job=new-pipeline-test-01)](http://ec2-3-255-233-100.eu-west-1.compute.amazonaws.com:8080/job/new-pipeline-test-01/) 
## step by step guide for install docker on ubuntu

ssh -i "docker-jenkins-controller_02.pem" ubuntu@ec2-79-125-62-60.eu-west-1.compute.amazonaws.com


```
sudo apt update
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io
sudo docker --version
sudo systemctl start docker
sudo systemctl enable docker

# to run docker without sudo
sudo usermod -aG docker $USER
logout and log back in fot the changes to take effect
newgrp docker

# test the docker installation by running this image
docker run hello-world
# to delete this docker image
docker rmi -f hello-world

# Install Docker Compose
sudo curl -L "https://github.com/docker/compose/releases/download/v2.22.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose --version

# to install jenkins docker container image
docker build -t myjenkins-blueocean:2.462.2 .
docker network create jenkins

docker run --name jenkins-blueocean --restart=on-failure --detach \
  --network jenkins --env DOCKER_HOST=tcp://docker:2376 \
  --env DOCKER_CERT_PATH=/certs/client --env DOCKER_TLS_VERIFY=1 \
  --publish 8080:8080 --publish 50000:50000 \
  --volume jenkins-data:/var/jenkins_home \
  --volume jenkins-docker-certs:/certs/client:ro \
  myjenkins-blueocean:2.462.2


# get jenkins admin password 

```
# increase the size of the swapfile
```
 sudo fallocate -l 1G /var/swapfile
 sudo chmod 600 /var/swapfile
 sudo mkswap /var/swapfile
 sudo swapon /var/swapfile
 echo '/var/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab
 sudo sysctl -p
```
