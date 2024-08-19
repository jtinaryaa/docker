In this project, we have also created one Dockerfile and lets understand concept:

1. If we want to build an image via Docker compose then we have to create a "Dockerfile" and docker will automatically recognised it.
2. Lets understand that what we can write inside a Dockerfile :
	--> First we have to tel Docker that which in-built image we can use from DockerHub to run our application.
	--> Our application is node.js application and we need Node from DOckerHub . So first we write :
    
	    FROM node
  			
	--> After using the node js image from DockerHub we have to copy our code inside the container and we have to build out code with npm so first we will
	    set/create working directory inside Node JS container.
		
		WORKDIR /app
	
	--> after creating a app folder inside the Node JS container we will copy all the code inside that /app folder.

	   COPY . /app

	--> after copying all the code inside /app folder then we will run the command npm install.

       RUN npm install

    --> now we have to run the code but here we have to do one more thing. In the Node JS application we have mentioned the PORT 80 that means it will use this port
        to run but this application will run inside the container and our local machine doesn't have any connection with docker container so we have to tel docker
        container to expose one port by which we can connect to our application so here we can use same port.

		EXPOSE 80

	--> Now we have give the RUN node server.js to run the application but if we use the RUN keyword that means this command will executed when image is being built.
        So we have to make sure that if IMAGE is built successfullt then only we have to run the application started command so for that Docker has given one keyword
        which is CMD and below is the syntax how we can use CMD.

		CMD ["node" , "server.js"]

3. Now our docker file is complete and we can open any command prompt or any terminal and go to the application path where Dockerfile is present and we can run the
   below command.
      
    $ docker build .

4. The above command will create an docker image and we can copy the name and run the image as container with given port number.	
    
	$ docker run -p 80:80 #image_name# 
	
###### THINGS TO KNOW ######
In the above steps, we started a container which also exposed a port (port 80).

I just want to clarify again, that EXPOSE 80 in the Dockerfile in the end is optional. It documents that a process in the container will expose this port. But you still need to then actually expose the port with -p when running docker run. So technically, -p is the only required part when it comes to listening on a port. Still, it is a best practice to also add EXPOSE in the Dockerfile to document this behavior.

As an additional quick side-note: For all docker commands where an ID can be used, you don't always have to copy / write out the full id.

You can also just use the first (few) character(s) - just enough to have a unique identifier.

So instead of

docker run abcdefg
you could also run

docker run abc
or, if there's no other image ID starting with "a", you could even run just:

docker run a
This applies to ALL Docker commands where IDs are needed.	
	