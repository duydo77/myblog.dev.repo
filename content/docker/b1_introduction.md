# **Docker all in one**

Reference:

https://docker-curriculum.com/#what-will-this-tutorial-teach-me-

https://www.celantur.com/blog/run-cuda-in-docker-on-linux/



## 1. What is Container and Terminology

VMs run applications inside a guest Operating System, which runs on virtual hardware powered by the server’s host OS.

Containers take a different approach: by leveraging the low-level mechanics of the host operating system, containers provide most of the isolation of virtual machines at a fraction of the computing power.

#### 1.1. Image

An important distinction to be aware of when it comes to images is the difference between base and child images.

- **Base images** are images that have no parent image, usually images with an OS like ubuntu, busybox or debian.
- **Child images** are images that build on base images and add additional functionality.

Then there are official and user images, which can be both base and child images.

- **Official images** are images that are officially maintained and supported by the folks at Docker. These are typically one word long. In the list of images above, the `python`, `ubuntu`, `busybox` and `hello-world` images are official images.
- **User images** are images created and shared by users like you and me. They build on base images and add additional functionality. Typically, these are formatted as `user/image-name`.



#### 1.2. Container

Create from Image and run the actual aplication. We create Container by running the cmd `docker run`

#### 1.3. Docker Daemon

The background service running on the host that manages building, running and distriuting Containers.

#### 1.4. Docker Client

The cmd tool that allows user to interact with the daemon 

#### 1.5. Docker Hub

A registry of Docker Images. The repos that store many docker images that you can download/pull and use them. If required, one can host their own Docker registries and can use them for pulling images.

#### 1.6. **Dockerfile** 

is used to build a image; a simple text file that contains a list of commands that the Docker client call while create a Docker Image

## 2. Install and "Hello Docker" ^_^

Following the instruction of the docker docs page: https://docs.docker.com/engine/install/ubuntu/

### 2.1. Manage Docker as a non-root user

Add linux user to docker group to dont need to sudo when using docker: https://docs.docker.com/engine/install/linux-postinstall/ 

To create the `docker` group and add your user:

1. Create the `docker` group.

   ```
   $ sudo groupadd docker
   ```

2. Add your user to the `docker` group.

   ```
   $ sudo usermod -aG docker $USER
   ```

3. Log out and log back in so that your group membership is re-evaluated.

   If testing on a virtual machine, it may be necessary to restart the virtual machine for changes to take effect.

   On a desktop Linux environment such as X Windows, log out of your session completely and then log back in.

   On Linux, you can also run the following command to activate the changes to groups:

   ```
   $ newgrp docker 
   ```

4. Verify that you can run `docker` commands without `sudo`.

   ```
   $ docker run hello-world
   ```

   This command downloads a test image and runs it in a container. When the container runs, it prints a message and exits.

   If you initially ran Docker CLI commands using `sudo` before adding your user to the `docker` group, you may see the following error, which indicates that your `~/.docker/` directory was created with incorrect permissions due to the `sudo` commands.

   ```none
   WARNING: Error loading config file: /home/user/.docker/config.json -
   stat /home/user/.docker/config.json: permission denied
   ```

   To fix this problem, either remove the `~/.docker/` directory (it is recreated automatically, but any custom settings are lost), or change its ownership and permissions using the following commands:

   ```
   $ sudo chown "$USER":"$USER" /home/"$USER"/.docker -R
   $ sudo chmod g+rwx "$HOME/.docker" -R
   ```

***Since Docker creates a new container every time***

## Docker command

1. show all containers that are currenty running: `docker ps` 

   to show all contatiners contain exited contatiner: `docker ps -a`

2. Run a container: `docker run <container name>`

   Run with interactivetty: `docker run -it <container name>`

3. Remove a container: `docker rm <container ID>`

   Get container ID from `docker ps` command

   Remove all containers that have status of exited: `docker rm $(docker ps -a -q -f status=exited)`

4. 

## Dockerfile keyworld to build a Docker Image

1. FROM
2. WORKDIR
3. COPY
4. ADD is similar to COPY but you can use it with zip file, ADD will auto unzip and copy to des file. You also can copy a file from URL
5. VOLUME
6. RUN
7. EXPOSE
8. CMD [" "," ",...]