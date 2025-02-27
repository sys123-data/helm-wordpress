# install ssh
sudo apt update 
sudo apt install openssh-server

# get ip 
ip a

# generate ssh key
ssh-keygen -t rsa -b 4096
# copy ssh key into slave
ssh-copy-id hack@92.168.0.131

# remove from host (if error  WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED! then try again)
ssh-keygen -R 192.168.0.131

# ssh into slave machine
ssh hack@192.168.0.131
# swich to root
sudo su - 
# install jenkins
```sh
sudo apt update
sudo apt install fontconfig openjdk-17-jre openjdk-17-jdk
java -version


sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
systemctl status jenkins
# get password
8feeec003e594c32b859bd80fe6de2ef
# install def plugins
# create account admin/admin
```
# intall docker engine
https://docs.docker.com/engine/install/ubuntu/
```sh
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
sudo docker run hello-world
docker ps -a
# add jenkins user to docker group
sudo usermod -aG docker jenkins
sudo usermod -aG docker hack
sudo systemctl restart jenkins
sudo systemctl restart docker

```
# install minikube
```sh
apt install snapd
snap install kubectl --classic
kubectl version --client


curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube_latest_amd64.deb
sudo dpkg -i minikube_latest_amd64.deb

```
# systemctl reboot

# minikube start from !!! non-root-user
```sh
minikube start
```
# !! back to root
# install helm using apt a
```sh
curl https://baltocdn.com/helm/signing.asc | gpg --dearmor | sudo tee /usr/share/keyrings/helm.gpg > /dev/null
sudo apt-get install apt-transport-https --yes
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/helm.gpg] https://baltocdn.com/helm/stable/debian/ all main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list
sudo apt-get update
sudo apt-get install helm
```
# or
```sh
sudo snap install helm --classic
```
# add bitnami repo
```sh
helm repo add bitnami https://charts.bitnami.com/bitnami
```
# add jenkins user to hack group | change file perm for authorization to k8s
```sh
sudo usermod -aG hack jenkins
sudo systemctl restart jenkins
sudo chmod g+r /home/hack/.kube/config
sudo chmod g+r /home/hack/.minikube/profiles/minikube/client.key
```

helm uninstall my-wordpress -n wordpress-ns
