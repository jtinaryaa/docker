# MANAGE - IMAGES & CONTAINERS

## 1. Common Commands
  - this command gives you the list of running container
	> $docker ps 
  - this command gives you the list of all containers
	> $docker ps -a 
  - build an image via docker compose file. Run this command where Dockerfile is present.   
	> $docker build . 
  - Below is the command to run an container via image.
	> $docker run -p 4200:80 image_name 
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
	> $docker start container_name/container_id
  - docker start command will not take you to the console of your container like Run command or we can say that docker start command will start the container in background and docker run will start the container in foreground also create a new container of same image.
  - if we want to STOP the existing running container the you should use docker stop command.
	> $docker stop container_name/container_id
		
## 4. Attached and Detached Container
  - docker run command starts the container in Attached mode and docker start command starts the container in Detached  mode.
  - Attached Mode : Go inside a container terminal.
  - Detached Mode : Don't Go inside a container terminal.
  - Why these modes are important? because if your application is printing the logs on console and if you want to see  the logs then you need to attach with the container console otherwise it is not required.
  - So if you are starting a container with docker start commad and you want to go to the console of your container then you can use docker attach command.
	> $docker attach container_id/container_name
  - one thing is that docker attach will take you the container console that is fine but it will give you the future    logs. If you want to see all the logs then you 
  should use the docker log command on a running container. (this will give you the logs not attach to the container console)
	> $docker logs container_id/container_name
  - We also have one more option in logs which is -f , means follow the output so by this way also you can attach to the container.
	> $docker logs -f container_id/container_name.

## 5. Removing Images and Containers.
- We can not remove the images if that image is belongs to any container.
- First we have to remove the container then only we can remove the images.
- If we are removing any container then it should be in the stopped stage.

### 5.1 Remove Container
  - Below is the command by which we can remove the container.
	> $docker rm container_id/container_name
  - We can also remove multiple containers in a single shot by providing multiple container_id/container_name followed by whitespace in the above command.

### 5.2 Remove Images
  - Below is the command by which we can remove any image.
	> $docker rmi image_name
  - We can also remove multiple images in a single shot by providing multiple image_name followed by whitespace in the above command.
  - Note: By using '$docker images' command we can get the list of images.
  - By Using below command, We can also removed the unused images that includes those images which are used by stopped container.
	> $docker images prune -a
  - Same rule also applies here which is that container must be remove first to remove any image.

# Scenario
- If you have created docker compose file and everytime you are doing any changes then you have to build your image and then run your container.
- To build image , command will be:
	> $docker build . 
- TO Run that image as container 
	> $docker run -p 4200:80 image_name
- Now what will happen everytime[for any change in code] a new image will be created and a new container will be created for that image. 
- So for container what we can do we have a '--rm' flag by which if we start a container then it will automatically remove when it stops so container problem is resolved.
- For images as we also mentioned above we can use below command to delete unused images.
	> '$docker images prune'
- Below is the command which we can follow in this case. [taking an example of web based application]
	> $docker images prune
	> $docker build .
	> $docker run -p 4200:80 --rm image_name
- So by using above three steps we can prevent to create unwanted images and containers.
- This we can do if we dont want to have our old code as image or container.




		
   
