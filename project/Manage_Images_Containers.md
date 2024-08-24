# MANAGE - IMAGES & CONTAINERS

## 1. Common Commands
  ### $ docker ps 
    - this command gives you the list of running container
  ### $ docker ps -a 
    - this command gives you the list of all containers   
  ### $ docker build . 
    - build an image via docker compose file. Run this command where Dockerfile is present.
  ### $ docker run -p 4200:80 image_name 
    - to run an image and if image having web based application then you need to provide the port.
    - 80 port is your application port which is running inside a container and your localhost doesn't have any connection with local machine.
		-	So 4200 port is that port which we can hit via our local machine and it will hit the 80 port inside the container.
		- Make sure that this port is helpfull when your image is hvaing the web based application.			

   
## 2. Docker Run and Docker Build 
  - Docker Run command is used to run the image and Docker build command is used to build an image from Docker compose   file.
  - After Ruuning the Docker Run command it will take you to the terminal of your container console.
  - Docker Run command will create another container of same image.  
  
## 3. Container START and STOP
  - if we want to start some existing container then you should use docker start command.
		# $docker start container_name/container_id
  - docker start command will not take you to the console of your container like Run command or we can say that docker start command will start the container in background and docker run will start the container in foreground also create a new container of same image.
  - if we want to STOP the existing running container the you should use docker stop command.
      ### $ docker stop container_name/container_id
		
## 4. Attached and Detached Container
  - docker run command starts the container in Attached mode and docker start command starts the container in Detached  mode.
  - Attached Mode : Go inside a container terminal.
  - Detached Mode : Don't Go inside a container terminal.
  - Why these modes are important? because if your application is printing the logs on console and if you want to see  the logs then you need to attach with the container console otherwise it is not required.
  - So if you are starting a container with docker start commad and you want to go to the console of your container then you can use docker attach command.
    ### $ docker attach container_id/container_name
  - one thing is that docker attach will take you the container console that is fine but it will give you the future    logs. If you want to see all the logs then you 
  should use the docker log command on a running container. (this will give you the logs not attach to the container console)
    ### $ docker logs container_id/container_name
  - We also have one more option in logs which is -f , means follow the output so by this way also you can attach to the container.
    ### $ docker logs -f container_id/container_name.
		
   
