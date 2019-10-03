
# **docker_images**

**Currently available docker images -** </br>
  - ***Authentication Servers*** <br>
  	- **FreeRADIUS**
  	<br>Username : testuser
    <br>Password : password
    <br>Supported Auth-Types : PAP, CHAP, MSCHAP, or EAP-MD5

**Instructions to deploy a Docker image -**

1. Clone the repository<br>
    ``$ git clone git@github.com:the-c0d3br34k3r/docker_images.git``
2. Ensure that you have Docker installed
	```	
	$ docker -v
	Docker version 18.09.7, build 2d0083d
	```
3. Navigate to the desired docker image folder.<br>
    ``$ cd <PATH_TO_DOCKER_IMAGE_FOLDER>``

4. Ensure that the current directory you're in, contains a Dockerfile.

	```
	$ ls 
	...
	Dockerfile
	...
	```

5. Build the image from the Dockerfile. Provide a tag name that is relevant to the image being used.<br> For example, if you're using the FreeRADIUS docker image, ``freeradius`` would be a suitable tag.<br>
    ``$ docker image build . -t <TAG>``
6. Run the built docker image.<br>
    ``$ docker run -it <TAG>``
7. Run the desired service :<br>
    **For FreeRADIUS :**<br>
    ``root@<CONTAINER_ID>:/# freeradius -X``
8. Refer the test.txt file within the docker image folder for instructions on how to test the service.

