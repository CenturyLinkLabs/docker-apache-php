panamax-docker-php
================

Base docker image to run PHP applications on Apache


Usage
-----

To create the image `panamax/docker-php`, execute the following command on the panamax-docker-php folder:

	docker build -t panamax/docker-php .


Installing your PHP application
-------------------------------

To install your application, copy your code inside the image in `/app`. For example, if using git:

	sudo docker run -d panamax/docker-php git clone https://github.com/fermayo/hello-world-php.git /app


It will print the new container ID (like `d35bf1374e88`). To create an image from that, execute:

	sudo docker commit d35bf1374e88 panamax/hello-world-php


You can now push your changes to the registry:

	sudo docker push panamax/hello-world-php



Running your PHP application
----------------------------

Pull your container if it's not yet on your local docker machine:

	sudo docker pull panamax/hello-world-php


Run the `/run.sh` script to start apache (via supervisor):

	sudo docker run -d -p 80 panamax/hello-world-php /run.sh


It will print the new container ID (like `d35bf1374e88`). Get the allocated external port:

	sudo docker port d35bf1374e88 80


It will print the allocated port (like 4751). Test your deployment:

	curl http://localhost:4751/


Hello world!
