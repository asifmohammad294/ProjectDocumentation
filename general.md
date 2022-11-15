# for giving read write execute permission to file or folder
sudo chmod a+rwx filename/foldername

# AWS - How to install java11 on an EC2 Linux machine?
    ```console
    sudo amazon-linux-extras install java-openjdk11
    ```

# h2 database in spring boot application.properties
```application.properties
spring.datasource.url=jdbc:h2:mem:books_data
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=
spring.jpa.database-platform=org.hibernate.dialect.H2Dialect

spring.h2.console.enabled=true
```