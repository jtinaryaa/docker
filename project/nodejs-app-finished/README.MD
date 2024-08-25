# nodejs-app-finished
- In this project, we are highlighting an important feature of Docker images and containers. 
- When writing a Dockerfile, Docker creates a separate layer for each step. 
- This allows Docker to take advantage of its cache when creating an image for the same project, as it can retrieve artifacts from the cache for unchanged steps.

## The following was the Dockerfile used in our previous project, which we have to analyzed and optimized:

1. FROM node
2. WORKDIR /app
3. COPY . /app
4. RUN npm install
5. EXPOSE 80
6. CMD [ "node", "server.js" ]


- As mentioned, Docker creates a separate layer for each step in the Dockerfile. 
- If a file, such as server.js or any .html file, is changed in the current project and the image is created again, steps #1 and #2 will not execute again, as Docker will retrieve them from its cache. 
- However, from step #3 onwards, Docker will execute the steps again as fresh. 
- This demonstrates that Docker recognizes changes in files and triggers the necessary actions, such as re-running the COPY command.

- Upon closer examination of the Dockerfile, it becomes clear that in step #4, the entire Node.js application is rebuilt every time a change is made to a .js or .html file. However, for a Node.js application, rebuilding the entire project is unnecessary when only .js and .html files are changed, unless there are changes in the dependencies mentioned in the package.json file. Therefore, it is important to optimize the Dockerfile to avoid unnecessary rebuilding.

- As a solution, we propose to first copy the package.json file and run the build command before copying the entire Node.js application code. 
- This way, if there are changes in the dependencies, the package.json file will be copied again, but if there are no changes in the dependencies, only the Node.js application code will be copied.

## The optimized Dockerfile for the current Node.js application is as follows:


1. FROM node
2. WORKDIR /app
3. COPY package.json /app
4. RUN npm install
5. COPY . /app
6. EXPOSE 80
7. CMD ["node", "server.js"]


- This optimization ensures that Docker only runs the npm install command when there are changes in the dependencies, leading to more efficient image creation for the Node.js application.

# STEPS TO CREATE DOKCER IMAGE AND RUN IMAGE as CONTAINER
## CREATE IMAGE 
- run below command in the same directory where docker compose file is there and file name must be 'Dockerfile'
- $ docker build . 

## RUN IMAGE as CONTAINER
- $ docker run -p 80:80 image_name  