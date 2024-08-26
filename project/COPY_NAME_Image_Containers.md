# COPY and RENAME - IMAGES & CONTAINERS

## 1. Inspect Image
  ### $docker image inspect image_id 
  - By this command you can inspect your image.
  - Inspecting an image means , you can get the lot of information about image in json format.

## 2. COPY 
- We can copy the files inside the container and vice-versa.
- We can do this operation when the container is running.
- this feature allow us to copying some files without restarting the container and without rebuild the image.
- We can not copy/replace the files inside a running container which used to run the application inside container.
- this is also not a good approach to copy/replace the file inside a running container because this can be error prone.
- But we can see this feature as docker provides the 'cp' tag to copy files inside a container.
- This can be used in certain scenrios like you want to copy/replace some configuration file inside the container which your application can be used.
- If you application inside the container is generating the logs then also we can copy the logs to our local.

  ### $docker cp dummy/. container_name:/tests
  - We can copy any file inside the container.
  - The above command use one 'cp' option which means COPY the file or folder.
  - after 'cp' command we have to give the path of your local and then container_name/container_id followed by path of inside container as per above syntax.
  - We can also copy the files in the running container also. 

  ### $docker cp container_name:/tests dummy/
  - we can also copy any file from the container to our local.
  - In the above command we can provide the path of container and local along with 'cp' tag.
  - If the container is running then also we can copy the files inside container to local.

## 3. NAMING and TAGGING
- We can also provide the name to an image and container as wel.
- if we are building any image via $docker build command then we observed that docker is providing the name and tag of that image as 'none' .
- So we can provide an name to images and container as per choice so that we don't need to copy the name and id everytime.

## Containers -  NAMING
- We can change the name of the container or while creating a container we can tel the docker to set the custom name.
- $docker run -p 4200:80 -d --rm image_id
- The above command is used to run a container in detached mode and with --rm tag which means docker will delete the container when it stops.
- So now we can provide the name of the container by modifying above command as below:
- $docker run -p 4200:80 -d --rm --name my-app image_id
- So now we can check via <$docker ps> command to check the container name , it should be my-app.
- In further processing like stop the container we don't need to copy the container_name because now we know the name
so we can use it directly like to stop the container , we can use <$docker stop my-app>
- Note : you can use $docker --help to explore other commands and features of containers.

## Images -  NAMING
- We are building the images via compose file , via command <$docker build .>
- So that time docker is creating the image with some image id but image name/repository and tag doesn't have any name.
- We have to two things in images one is name/repository and second is tag. <docker images> - to see list of images
- So name is the image name/repository and tag is the image version.[image tag can be latest or some version number or anything]
- docker also treat its own images like that, if you remember the docker compose file first statement which is 
  <FROM node:12>
- In that also the syntax of image is image:tag . So same we can use for our cutome images also.
- Below is the command by which we can define an image name and tag.
- $docker build -t my-image:latest .
- Now docker will create an image with 'my-image' name and tag will be 'latest' .
- Note : you can use $docker images --help to explore other commands and features of images.

  