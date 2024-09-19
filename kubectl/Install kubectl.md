## For Ubuntu

* `sudo apt update`
* `sudo apt -y install curl apt-transport-https`
* `curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.28/deb/Release.key | sudo gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg`
* `echo 'deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.28/deb/ /' | sudo tee /etc/apt/sources.list.d/kubernetes.list`
* `deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.28/deb/`
* `sudo apt update`

# ![Screenshot from 2024-09-19 16-19-50](https://github.com/user-attachments/assets/ef959e80-710c-426f-89cd-0e956700216f)
