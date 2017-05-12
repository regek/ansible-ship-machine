# Ansible Ship Machine
Ansible ship machine is a simple docker base image contain ansible used to test ansible roles, to build the image just follow the instructions below:

	$ cd <os_family>/<os_version>
	$ docker build -t <docker_images_name>:<os_family>-<os_version> .
	$ docker tag <docker_images_name>:<os_family>-<os_version> <your_docker_repo>/<docker_images_name>:<os_family>-<os_version>
	$ docker push <your_docker_repo>/<docker_images_name>:<os_family>-<os_version>
