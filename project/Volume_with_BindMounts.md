# Volumes & Bind Mounts

## 1. Introduction
  - What is Volumes and Bind Mounts in Docker ? Lets understand that first .
  - Volumes and Bind Mounts in Docker are used to address the challenge of persisting data and files that are created or updated within a running  container.
  - Consider an application that runs within a container and continuously update or create files.
  - And that application is running via container and many users are using our application and those files are updating day by day or new files
	  are getting created day by day.
  - To illustrate this scenario, let's consider an example where we need to develop an application that includes a web page serving as a 
	  feedback   form. Users should be able to provide a title and description, and upon submitting the form, a new file should be created. The file should be named after the provided title, and the description should be saved within that file. Before saving the feedback our application should check if same file name exists or not , if exists then it should give error.	
  - Many users are providing the feedback so multiple files are getting created.	
  - Considering that application is running via container.
  - So the problem is if that container gets deleted/removed then we will lost those updated feedback files in which all the data was 
	  getting stored.
  - And big problem is that if we have to do some changes in the code in future then we will have to create new image and that new images 
	  will create a new container everytime. So those all feebdack data files would lost and will not be able to recover them.
  - Docker introduced Volumes and Bind Mounts as solutions to this problem.
  - Volumes involve keeping the file outside the container, ensuring that it is accessible and preserved even if the container is recreated.
  - There are two ways to keep the file outside the container: within Docker (Volumes) or in a repository/folder managed by the user (Bind Mounts). 
  - Volumes refer to keeping the file within Docker but outside the container, while Bind Mounts involve keeping the file in a user-managed repository or folder.
  - Let's start by examining the concept of Volumes.
	
## 2. Volumes
  - Volumes are the part of docker like images and containers.
	- Below is the command by which we can see the list of volumes same as images and containers.
	 > $docker volume ls
  - When creating volumes in Docker, it's important to specify a name, as Docker will otherwise assign a default name to the volume, which is referred to as an anonymous volume.
  - It's important to remember that anonymous volumes are destroyed when the container is removed or when a new container is created.
  - While there are other advantages of anonymous volumes that we will discuss later, for now, our focus will be on named volumes, as they are the only solution to the problem mentioned earlier.
  - To gain a better understanding of named volumes, we have created a Node.js application named 'data-volumes-01-adj-node-code', as mentioned in the example above.
  - This application includes a webpage with fields for title and description, allowing users to input any title and its corresponding description. Upon submitting the feedback form, the application will generate a new file inside feedback folder with the title provided, containing the inputted description. Additionally, the application includes a feature to check if the file already exists before creating it, and if it does, an error will be thrown.
  - First, we can build the image using the following command:
   > $docker build -t volume-app-image .
  - Two important points to note here:
  - With named volumes, no changes are required in the docker-compose file; named volumes can be created by adding additional commands to the docker run command.
  - In the application, the feedback folder is where files are created/updated, so this folder needs to be considered as a volume.
  - We can run the image along with volumes using the following command:
   > $docker run -d -p 3000:80 --rm --name volume-app 	-v feedback:/app/feedback volume-app-image
  - Let's break down the above command:
  - '-d' is used to run the container in detached mode.
  - '--rm' is used to automatically remove the container when it stops.
  - '--name' is used to provide a name for the container.
  - Now, let's focus on the volume-related command:
   > -v feedback:/app/feedback
  - '-v' is used to instruct Docker to create a volume.
  - 'feedback:' this is the volume name and it can be anything.
  - '/app/feedback' is the path that tells Docker to treat any files created under this path as part of the volume. If you see the docker compose
	  file of 'data-volumes-01-adj-node-code' application where we set /app as working directory and inside that we are copying the full application.
	- So now you can check the volume list by using below command.
   > $docker volume ls
  - We can also stop the container and create a new container and we can see that the file inside /feedback folder are same as it is.
  - So how we can check that ? simply after running the container we can access localhost:3000/feedback/filename.txt and filename should
   be same as title you have provided in feedback form.
	 
   
