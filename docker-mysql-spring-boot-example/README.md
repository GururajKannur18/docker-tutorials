# Spring Boot on Docker connecting to MySQL Docker container

1. Use MySQL Image published by Docker Hub (https://hub.docker.com/_/mysql/)
Command to run the mysql container
`docker run --name mysql-standalone -e MYSQL_ROOT_PASSWORD=password -e MYSQL_DATABASE=test -e MYSQL_USER=sa -e MYSQL_PASSWORD=password -d mysql:5.6`

2. In the Spring Boot Application, use the same container name of the mysql instance in the application.properties
`spring.datasource.url = jdbc:mysql://mysql-standalone:3306/test`

3. Create a `Dockerfile` for creating a docker image from the Spring Boot Application
`FROM openjdk:8
ADD target/users-mysql.jar users-mysql.jar
EXPOSE 8086
ENTRYPOINT ["java", "-jar", "users-mysql.jar"]`

4. Using the Dockerfile create the Docker image.
From the directory of Dockerfile - `docker build . -t users-mysql`

5. Run the Docker image (users-mysql) created in #4.
`docker build . -t users-mysql`

## Useful Docker commands
- `docker images`
- `docker container ls`
- `docker logs <container_name>`
- `docker container rm <container_name`
- `docker image rm <image_name`

Here is the more details:

[user@10.157.138.7 docker-mysql-spring-boot-example]$ docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
users-mysql         latest              438ac24389ba        3 minutes ago       654MB
openjdk             8                   81f83aac57d6        2 days ago          624MB
mysql               5.6                 1f47fade220d        2 days ago          256MB
hello-world         latest              c54a2cc56cbb        2 years ago         1.85kB

[user@10.157.138.7 docker-mysql-spring-boot-example]$ docker container ls
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS               NAMES
7cef4b7f2bd8        mysql:5.6           "docker-entrypoint..."   11 minutes ago      Up 11 minutes       3306/tcp            mysql-standalone


