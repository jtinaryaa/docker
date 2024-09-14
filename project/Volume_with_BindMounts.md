# Volumes & Bind Mounts

## 1. Introduction
  - What is Volumes and Bind Mounts in Docker ? Lets understand that first .
  - Volumes and Bind Mounts in Docker are used to address the challenge of persisting data and files that are created or updated within a running  container.
  - Consider an application that runs within a container and continuously updates or creates files, such as a feedback file for user input.
  - Now this application is running via container and users are using our application and that file is updating day by day or new files
	  are getting created day by day.
  - Lets understand this scenario by one example , we are creating one application which is asking fro feedback and all the feeback we are saving
    in one file and that application is running via container.
  - So the problem is if that container gets deleted/removed then we will also lost that updated files where all the data was there.
  - And big problem is that if we are done some changes in the code and creating a new image and that images is creating a new container
    then we will not get the latest feedback file. Got it.
  - Docker introduced Volumes and Bind Mounts as solutions to this problem.
  - Volumes involve keeping the file outside the container, ensuring that it is accessible and preserved even if the container is recreated.
  - There are two ways to keep the file outside the container: within Docker (Volumes) or in a repository/folder managed by the user (Bind Mounts). 
  - Volumes refer to keeping the file within Docker but outside the container, while Bind Mounts involve keeping the file in a user-managed repository or folder.
  - Let's start by examining the concept of Volumes.
	
## 2. Volumes

		
   
