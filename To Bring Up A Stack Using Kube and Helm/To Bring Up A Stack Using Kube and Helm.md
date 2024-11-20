## To Bring Up A Stack Using Kube and Helm
* Login into the server (If you are using a server to login and to bring up the stack).
* Most common way is `ssh -v 54.189.106.70` (To use this install ssh, `-v` - Is to verbose all the details, and then the IP address that you want to connect to)
* Go to the yaml file that you want to create or have created for example `idau-stage.yml`. Location: `home/yaml/joel/`
* Edit the .yml file based on your requirements.
* Save it then in the same folder where the .yml file is present enter this command `helm repo add helm-repo https://<git secert>@raw.githubusercontent.com/formsdirect/helm-repo/master/` (This will install the `helm-repo` to your directory)
* Then start the stack by entering this command `helm install age-fix-idau helm-repo/fd-site -f idau-stage.yml` (Since we are in the same folder we say `idau-stage.yml` if we are in a another folder modify accordingly.
* Once it is started you can see the staging site (the link will be given after the command itself)

## To execute a pod/ To enter inside a pod
* `kubectl exec -it uscisupdates-i485principalpremium-deployment-5ffcb96d-qw9mm -- bash` here `uscisupdates-i485principalpremium-deployment-5ffcb96d-qw9mm` is the deployment name.

## To delete a pod
* `kubectl delete pod formupdatesi485-i485beneficiarypremium-deployment-556f79ccjj6zf` here `formupdatesi485-i485beneficiarypremium-deployment-556f79ccjj6zf` is the pod name.

## To delete a pod service
* `helm delete i485formupdates`  here `i485formupdates` is the service name.

## Lets say you want to copy some file to the deployment(Place where all your static files like html, css are placed)
* `kubectl cp idau-8.zip idau-stage-web-depeloyment-65d5b5b447-zwbs5:/tmp` here `idau-stage-web-depeloyment-65d5b5b447-zwbs5` could be anything based on your requirement and tmp is the temporary folder to avoid any clutter.
* Then based on what server you are using lets `Nginx` then go to `usr/share/nginx/html` and your project folder that you are using to server your html files.
