list of the Docker commands I used for each step (pulling, running, checking, stopping, etc.).

pulling => 
1. docker pull nginx:stable-perl
2. docker images

run a container => 
1. docker run --name nginx -d -p 80:80 nginx:stable-perl
2. docker ps
3. docker run --name nginx-2 -d -p 81:80 nginx:stable-perl
4. docker ps

Explore the container => 
1. docker logs + id
2. docker stop
3. docker rm

_______________________________________________________________________________________________________________________________________________________________________________________________________________________________

Reflection Questions 

1. What is the difference between a Docker image and a Docker container? Explain in your own words.

    docker image is simply our application (ex: website) which has transferred into another format in order to be kept in containers.
    What exactly is a container?! 
	  As I mentioned its the place where our image would be kept to be isolated from side effects witch might effect the way our application works.


3. Why might you see an error like “port already in use” when running a container, and how can you fix it?

    Personally I come across with a situation which indicated that the desired port (80) is being used by another program on my computer, however I didn't see any error, but I suppose that would be similar to mentioned         circumstances.
	  I ran my container; 'docker ps' showed its up and everything seems alright but when I opened localhost:80 there was something else showing up instead of Nginx default html page. I searched and I realized the app which      is using 	this port is Apache. 

   How I fixed it:
   
1 => I used the command "netstat" to figure out which app is using the port I want, the command output is a PID which refers to the app. 
2 => I went to task manager, found the PID section which showd the app name and some other information and then I pressed the 'End Task' to stop the app.



5.  How does the docker logs command help you when working with containers?

    docker logs shows what process is being done or maybe have been done and what issues exist on the container. Indeed I don't understand anything about the process 
	  docker logs shows me; for example 'getrlimit(RLIMIT_NOFILE): 1048576:1048576', but the errors helped me to find out what's about the issue. For instance when I checked 	logs I catch that there's an error:
	172.17.0.1 - - [12/Jul/2025:14:49:39 +0000] "GET /favicon.ico HTTP/1.1" 404 555 "http://localhost:81/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 	(KHTML, like Gecko) Chrome/138.0.0.0 Safari/537.36" "-"
	
    At first I didn't understand what exactly is the issue, so I searched the error and I found out the browser looks for a favicon automatically and there isn't such a file in Nginx default html page. Therefore docker         logs helped me check how's the container running situation and helped me check if there are any errors in this process or not.

_______________________________________________________________________________________________________________________________________________________________________________________________________________________________

Challenges faced 

Error => 
'getrlimit(RLIMIT_NOFILE): 1048576:1048576', but the errors helped me to find out what's about the issue. For instance when I checked 	logs I catch that there's an error:
172.17.0.1 - - [12/Jul/2025:14:49:39 +0000] "GET /favicon.ico HTTP/1.1" 404 555 "http://localhost:81/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 	(KHTML, like Gecko) Chrome/138.0.0.0 Safari/537.36" "-"
How I resolve it => Actually I didn't resolve it as far as I knew, that the problem was not made by me. However I could have replace the nginx default html page with a custom file and include a favicon in the html header tag and the problem would be resolved, but I don't think that was necessary for this assignment.

_______________________________________________________________________________________________________________________________________________________________________________________________________________________________

Sorry for my poor english grammar :)
