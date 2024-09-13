# IMAGES - SHARE & PUSH

## 1. Share Images
  - There are two ways to share the images. 
  - The first method involves sharing the full code along with the Dockerfile, allowing the other person to build the image on their machine and run  the application as a container. However, this approach is not ideal as it requires sharing everything and the other user to build the image.
  - The second, more efficient method involves sharing the image to Docker Hub or a private repository, from which colleagues can pull the image and  run it as a container. While Docker Hub is free and suitable for individual use, organizations often prefer to use their private repository for  added security.
   
## 2. Push Images to Docker Hub 
  - First, sign up for a Docker Hub account, which is free to use. Note that with the free account, only one private repository can be created, but multiple public repositories are allowed.
  - After signing up on Docker Hub, create the repository, ensuring that the repository name will be treated as the image name to be pushed to Docker Hub.
  - For example, if creating a repository with the name 'my-demo-app', the image name should be docker_username/my-demo-app, where docker_username is the name assigned by Docker during signup. Upon creating the repository on Docker Hub, the page will display the command to pull the repository.
  - Next, build the image with the same name. Assuming the Docker username is 'jtinarya', the command to create an image using a Docker Compose file would be:
	> $docker build -t jtinarya/my-demo-app 
  - Note: If the tag name is not defined, Docker will assign the default tag as 'latest'.
  - If an image already exists, it can be cloned with a different name using the following command:
	> $docker tag old_image_name jtinarya/my-demo-app
  - Subsequently, the image can be pushed with the following command:
	> $docker push jtinarya/my-demo-app
  - Note: If pushing the image to a private repository, the hostname and username must be provided with the above command, as will be discussed in the following sections.
  - Now other user can pull this image with the below command.
	> $docker pull jtinarya/my-demo-app
  - Then we can run this image as container
	
## 3. Run the image as container
	
  - If the image contains an application that needs to run on a specific port, or if it's a web application, the syntax to run the container is as follows:
  > $docker run -p access_port:app_port image_name 
  - To run the container in detach mode, the command would be:
  > $docker run -d -p access_port:app_port image_name
  - If there is a need to attach the running container again to view future logs, the command is:
  > $docker attach container_name/container_id
  - To view past logs of a container, the command is:
  > $docker logs container_name/container_id
  - If there is a requirement to attach the container and view past logs as well, the following command can be used:
  > $docker logs -f container_name/container_id


		
   
