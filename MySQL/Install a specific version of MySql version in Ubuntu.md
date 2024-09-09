# Install MySql (This is only if you wanted to install a specific version and not the latest version)

**Make sure to uninstall the mysql. (If any is previously installed)**
* download the version that you neede from this site `https://downloads.mysql.com/archives/community/`
* extract it and rename it to `mysql`
* then type `sudo mv mysql /usr/local/mysql`
```
sudo groupadd mysql
sudo useradd -r -g mysql mysql
```
```
sudo chown -R mysql:mysql /usr/local/mysql
```
```
sudo apt-get install libaio1
```
```
cd /usr/local/mysql
sudo scripts/mysql_install_db --user=mysql
```
```
sudo chown -R mysql:mysql /usr/local/mysql/data
```
```
sudo cp support-files/mysql.server /etc/init.d/mysql
sudo chmod +x /etc/init.d/mysql
sudo update-rc.d mysql defaults
```
```
sudo service mysql start
```
```
echo 'export PATH=/usr/local/mysql/bin:$PATH' >> ~/.bashrc
source ~/.bashrc
```
```
sudo /usr/local/mysql/bin/mysqladmin -u root password 'new-password'
```
```
mysql -version
```
