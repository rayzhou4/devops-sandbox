# Hello Docker
Made a simple nodejs app to deploy using Docker

### Learning Objectives
- Docker

### How to use
Install Docker and clone repo locally. Then, run the following commands in the path of where you installed the repo:
<blockquote>
  docker build -t node-app:1.0 .
  
  docker run -d -p 3000:3000 node-app:1.0
</blockquote>
The app should now be available on http://localhost:3000/. To stop the docker container from running and to delete it from your images run the following commands:
<blockquote>
  docker stop &lt;container ID or name&gt;

  docker rm &lt;container ID or name&gt;
</blockquote>
Use these two commands to check the currently running Docker containers and the Docker containers that are currently running or stopped, respectively (you can also find the Docker container's container ID and names here):
<blockquote>
  docker ps

  docker ps -a
</blockquote>