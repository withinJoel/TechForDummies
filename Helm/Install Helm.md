## For Ubuntu
* `curl https://baltocdn.com/helm/signing.asc | sudo apt-key add -`
* `sudo apt-get install apt-transport-https --yes`
* `echo "deb https://baltocdn.com/helm/stable/debian/ all main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list`
* `sudo apt update`
* `sudo apt-get install helm`
