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

		
   
