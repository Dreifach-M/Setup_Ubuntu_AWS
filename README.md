# **Setup Ubuntu AWS**
Setup + add swap and instal Docker &amp; docker-compose

## _01 - Add Swap:_

- check if your instance already has a swap file or partition:

``` bash
sudo swapon --show
```

- Create 1GB swap file called `/swapfile`. You can adjust the size of the file by changing the number after `-l`.
``` bash
sudo fallocate -l 1G /swapfile
```
``` bash
sudo chmod 600 /swapfile
```
``` bash
sudo mkswap /swapfile
```

- Enable the swap file
``` bash
sudo swapon /swapfile
```

-  Add an entry to the `/etc/fstab` file to ensure that the swap file is automatically enabled after every reboot
``` Bash
/swapfile swap swap defaults 0 0
```
- Verify the swap file
```bash
sudo swapon --show
free -h
```

## _02 - Docker Installation:_

- Update your existing packages
``` bash
sudo apt update
```

- Install a prerequisite packages which let apt utilize HTTPS:
``` bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```
- Add GPG key for the official Docker repo to the Ubuntu system:
``` bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```
- Add the Docker repo to APT sources:
``` bash
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
```
- Update the  database with the Docker packages from the added repo:
``` bash
sudo apt update
```
- install Docker and Docker compose + `Docker CE command line interface` + `containerd`
``` bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

- Test verify the docker setup:
``` bash
sudo docker --version
docker compose version
sudo docker run hello-world
sudo docker images
sudo docker ps -a
```
- To avoid using sudo for docker activities, add your username to the Docker Group:
``` bash
sudo usermod -aG docker {your_username}
```

























