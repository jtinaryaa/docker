# python-app-starting-setup
- This python project we have created to show that what is intrective mode in docker and why it is used for.
- If we have a application in our image/container which requires input from console then we need intrective mode.
- we can go to the intrective mode of your application of docker official image by using below command.
- $docker run -it image_name
- Now above command will run the application in intrective mode.
- In the python-app-starting-setup, it ask you for some inputs of min and max numbers.

# Run this application
1. $ docker build .
2. $ docker run -it image_name

- if you want to start this application again via $docker START command then you have to take care of two things.
- first start the container as attached mode.
- second start the container in input mode as wel because in this application we have to provide the inputs also.
- so below is the command to do that.

3. $ docker START -a -i container_id/container_name

# Things to Remember
- you don't need to install python as it will download the python image from docker hub
- if you run $docker run image_name , it will through an error because this programme needs an input from console so this application must run via intrective mode only.
- In this type of application we don't need to define a port because this is not a web based application.
- Only web based applications which need port to run, only required to give port while running via docker.