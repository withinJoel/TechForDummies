## Tips to debug an issue in your code
* Check the application flow. example: `register.html` submits the data to `register.php` and `register.php` stores the data in the mysql under `dbname.tablename`   
* Check the logs. example: `server.log` or `application.log` (if the logs are irrevelant then add statements like `JS:console.log` or `JAVA:System.out.println` to debug where itis causing an issue.
* Check if all the required applications are up and running. example: If you are working with php then check if php is installed and if you are using mysql check if it is installed and running.
* Check if the resources for your project exists in the path that your code is pointing towards.
