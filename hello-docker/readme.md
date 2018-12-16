# Create Docker Image

Now use maven command `mvn clean install dockerfile:build` to create docker image.

# Deploy and Run Docker Image
So we have created the Docker Image (i.e. `hello-docker-0.0.1-SNAPSHOT-docker-info.jar`). We also have a installed docker container running in our local machine.

Now, to run the docker image inside installed docker container, we will use below command.

```
docker run -p 8080:9080 -t hello-howtodoinjava/hello-docker  --name hello-docker-image
```

Here the option `-p 8080:9080` is important. It says that expose port `8080` for internal port `9080`. Remember our application is running in port `9080` inside docker image and we will access that in port `8080` from outside Docker container.

Now access the application with URL `http://192.168.99.100:8080/hello/sajal`. 

Notice that the browser output is same as output of standalone REST API on localhost.

```
Hello sajal Response received on : Sun Dec 16 16:06:42 GMT 2018
```