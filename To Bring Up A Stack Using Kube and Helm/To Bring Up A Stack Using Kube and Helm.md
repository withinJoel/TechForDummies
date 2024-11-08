## To Bring Up A Stack Using Kube and Helm
* Login into the server (If you are using a server to login and to bring up the stack)
* Go to the yaml file that you want to create or have created for example `idau-stage.yml`. Location: `home/yaml/joel/`
* Edit the .yml file based on your requirements.
* Save it then in the same folder where the .yml file is present enter this command `helm repo add helm-repo https://<git secert>@raw.githubusercontent.com/formsdirect/helm-repo/master/` (This will install the `helm-repo` to your directory)
* Then start the stack by entering this command `helm install age-fix-idau helm-repo/fd-site -f idau-stage.yml` (Since we are in the same folder we say `idau-stage.yml` if we are in a another folder modify accordingly.
* Once it is started you can see the staging site (the link will be given after the command itself)
* 
