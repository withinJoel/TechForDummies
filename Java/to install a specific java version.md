## For Ubuntu
* `wget https://corretto.aws/downloads/latest/amazon-corretto-8-x64-linux-jdk.deb` (Here we are installing Amazon correto 1.8)
* `sudo dpkg -i amazon-corretto-8-x64-linux-jdk.deb`
* (If you get an error in step 2 like the below exception then go to step 3 else skip step 3.)
```
dpkg: dependency problems prevent configuration of java-1.8.0-amazon-corretto-jdk:amd64:
 java-1.8.0-amazon-corretto-jdk:amd64 depends on java-common; however:
  Package java-common is not installed.

dpkg: error processing package java-1.8.0-amazon-corretto-jdk:amd64 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 java-1.8.0-amazon-corretto-jdk:amd64
```
* `sudo apt install java-common`
* `sudo apt --fix-broken install` (Not mandatory but to be on the safer side)
* `sudo dpkg --configure -a`
* `java -version`
