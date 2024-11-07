## For Ubuntu

* `sudo apt update`
* `cd /usr/local/src/`
* `ls`
* `sudo apt -y install curl apt-transport-https`
* `curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.28/deb/Release.key | sudo gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg`
* `echo 'deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.28/deb/ /' | sudo tee /etc/apt/sources.list.d/kubernetes.list`
* `sudo apt update`
* `sudo apt install kubectl`
* `kubectl version`
