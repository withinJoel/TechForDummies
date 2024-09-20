* Create a database called "era_wanderer".
* In the xampp control panel go to config/my.ini file (which is next to the MySQL).
* And make the following changes
* innodb_lock_wait_timeout=9000
* Then locate php/php.ini (which is next to the apache).
* And make the following changes
* max_input_time=9000
* max_execution_time= 9000
* Go to the shell which is present at the right side of the xampp control panel.
* Then type the following code in the shell "mysql -u root -p mydatabase < /path/to/your_file.sql" - "root" is the default username and the password is "" (nothing) make sure to replace the "mydatabase" with the database name(era_wanderer) that you have already created and then the path to your database.
* (Only try if nothing works)
* If you have tried the shell and also changed the values and if still there is no hope then try this GUI method (which is slow and also make sure the above values are updated before using this method)
* Go to the import section and locate the db.sql, when you go down, you will find "Other options" under it disable "enable foreign key checks".
* (if in case the import is unsuccessful then increase innodb_lock_wait_timeout, max_input_time and max_execution_time until the import is successful)
* Enjoy