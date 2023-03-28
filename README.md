# LaravelApplicationHostwithDocker
To set up the Laravel application with Nginx and Mysql using Docker Compose:
Here are the steps I performed to set up the Laravel application with Nginx and Mysql using Docker Compose:

1.	I installed Docker and Docker Compose on my local machine by downloading and installing them from the official Docker website: https://www.docker.com/.

2.	I created a new Laravel application using the Laravel installer or composer by running the following command in the terminal:

![image](https://user-images.githubusercontent.com/99163931/228209430-af80a964-40b6-42dc-9711-80f544dc5899.png)


3.	I created an nginx directory with a conf.d subdirectory and a default.conf file containing the following configuration:

![image](https://user-images.githubusercontent.com/99163931/228209482-03ddee81-c9f7-47c1-be4d-ea4f8e344bbf.png)


4.	I created a Dockerfile inside a php directory with the following content:

![image](https://user-images.githubusercontent.com/99163931/228209526-dbb1be41-05cb-407c-9fb7-807700564998.png)
 

5.	I created an app service in my docker-compose.yml file with the following content:

![image](https://user-images.githubusercontent.com/99163931/228209569-3196488f-9787-4b6a-929f-31cc280e1d0c.png)

 

In this service, I set up the build context and Dockerfile location for my PHP container. The image name is set to my-laravel-app, and the container name is set to my-laravel-app. I also mounted the php/src directory to the /var/www/html directory inside the container.
Additionally, I set the environment variables for the database connection and specified the database service as a dependency.
Next, I created a database service in the same docker-compose.yml file with the following content:

![image](https://user-images.githubusercontent.com/99163931/228209621-74b6a010-b040-4734-80fa-37a023960329.png)
 

In this service, I specified the MySQL image version, container name, and restart policy. I also set the environment variables for the database and mounted a volume for persistent storage.
Finally, I created a web server service with the following content:

![image](https://user-images.githubusercontent.com/99163931/228209650-45ea47d8-d486-4e3f-98cd-90a2bbf1f590.png)


In this service, I specified the Nginx image version, container name, and port mapping. I also mounted the nginx/conf.d and php/src directories to the container and specified the app service as a dependency.
After creating the docker-compose.yml file, I ran the following command to start the containers:

![image](https://user-images.githubusercontent.com/99163931/228209677-e00d5fee-7c7a-4d96-ab01-d413d82128ef.png)
 

his built the images and started the containers for the app, database, and web server services.
Finally, I accessed my Laravel application in the browser at http://localhost:8000.

