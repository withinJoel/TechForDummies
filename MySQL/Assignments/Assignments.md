# Starship
Made with 💖 by Joel Jolly.

# About
* This Java Spring Boot application facilitates user registration and login processes. It prioritizes user data security with password hashing and validation. The intuitive interface streamlines account creation and login, while informative error messages guide users through potential issues.

# Project Current Progress
1. Install Required Tools: ✅
   * Java ✅
   * IntelliJ ✅
   * MySql ✅
3. Create a New Spring Boot Project: ✅ 
4. Set Up Version Control: ✅
   * Github ✅ (Files are uploaded via GitKraken (For linux users) (Github Desktop for windows users)) (Note: If your individual files are less than 25 mb you can use github website on your browser for file uploading)
6. Design the Database Schema: ✅  (Mentioned in the later part of this readme)
7. Configure MySQL Connection: ✅ 
8. Create JPA Entities: ✅
9. Create Repository Interfaces: ✅ 
10. Implement the Service Layer: ✅ 
11. Create REST Controllers: ✅ 
12. Handle Validation: ✅ 
13. Test with Postman: ✅ 
14. Implement Basic Security (Optional): ✅
15. Prepare Documentation: ✅ (Almost)
16. Code Review and Feedback: Pending

# Screenshots

* Home Page
![Screenshot from 2024-08-19 17-43-16](https://github.com/user-attachments/assets/fec6ee01-64f9-4e95-bd5f-5a4aae36ebcb)

* Login Page
![Screenshot from 2024-08-19 17-43-34](https://github.com/user-attachments/assets/6da30192-618b-4c89-9ca5-c4081d53374a)

* Feed Page
![Screenshot from 2024-08-19 17-45-05](https://github.com/user-attachments/assets/60e1220b-f7da-4a8c-8947-0697e90cf73a)

* About Page
![Screenshot from 2024-08-19 17-45-34](https://github.com/user-attachments/assets/bae3b683-6589-4912-bcbe-4073ec7ed31c)

# To get started
* Create a database

```
CREATE DATABASE teamsync;
```
* Enter inside the database

```
USE teamsync_db;
```
* Create a table called `user_details`
```
CREATE TABLE user_details (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    firstname VARCHAR(50) NOT NULL,
    lastname VARCHAR(50) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE,
    password VARCHAR(255) NOT NULL
);
```
* Update the `application.properties`
```
spring.application.name=starship
spring.datasource.url=jdbc:mysql://localhost:3306/users

//Starship port
server.port=8083
server.servlet.context-path=/starship

spring.datasource.username=root
spring.datasource.password=test123!
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.jpa.database-platform=org.hibernate.dialect.MySQLDialect
spring.jpa.hibernate.ddl-auto=update
```
* Paste the repo code inside the intellij project folder. (Before doing this create a new project using intellij and then close the intellij app and then paste the code from this repo)
* Run the `build.gradle` (To install the packages)
* Run the code.

# Want help, Use my Java & Springboot basics course (It's free)
* https://github.com/withinJoel/TechForDummies

# Support Me
If you love TeamSync and want to keep me caffeinated for more awesome updates, consider buying me a coffee!

[![Buy Me a Coffee](https://img.shields.io/badge/Buy%20Me%20a%20Coffee-Donate-orange?style=for-the-badge&logo=buy-me-a-coffee)](https://www.buymeacoffee.com/withinjoel)

Made with 💖 by Joel Jolly.
