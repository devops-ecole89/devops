# Architecture DevOps

## Introduction to Docker

### Presentation 

This section is intended to new users of Docker. We will see the main function of Docker.

Docker is composed of 3 parts :
  - A **Dockerfile** used to create a Docker image
  - A **Docker image**, which is a template of the expected virtual machine
  - A **Docker container**, the actual virtual machine

In folder ```docker```, a Dockerfile example is presented. Dockerfiles are structured as follow :
   - ```FROM``` command on the first line, which refers to the image the new image will be based on. In the example, our image is based on **ubuntu** image, the official small image to use the basic Ubuntu commands.
   - ```CMD```  command on the last line. This instruction is run when the container is used. In this example, *SSH* is started on the container when run. ```ENTRYPOINT``` is also an available last command.
   - In between these lines, the command are used to create and configure the image on which the container will be based.

### Image and container creation

Based on this Dockerfile, we can create an image. For this purpose, run the following command inside ```docker``` folder :

```sh 
docker build -t img_name .
```

> **docker build** is used to create an image
> 
> **-t** option is used to name the image. In this example, the image is named *img_name*
>
> **.** refers to the location of the Dockerfile used to build the image. Here, we are looking for the file in the current folder. The file should be named *Dockerfile*, otherwise the docker file name should be provided.

Next step is to run a container based on the built image. To do so, run the following command :

```sh 
docker run -d --name container_name img_name
```

> **docker build** is used to run a container based on a given image. The ```CMD``` or ```ENTRYPOINT``` command are run at this moment.
> 
> **-d** option is used to detach the run process from the terminal. This allows to use the terminal after the command is run. Without this flag, the terminal would be stuck on running the docker process.
>
> **--name** is used to name the container we are going to create. In this example, the container will be named *container_name*.
>
> **img_name** is the name of the image used for creating the container.

After that, we can verify that the container is running using ```docker ps```. This command will list the running containers and some information about them.

Finally, we can log into our container. This is available because of own we defined the container. To log into the container, use the following command :

```sh 
docker exec -it container_name bash
```

> **docker exec** is used to execute a command on a container. In this example, the executed command is *bash* which defines that we run a shell prompt once in the container.
>
> **-it** is short for *interactive* and *tty*, flags which allow to log into the container.
>
> ***container_name** is the name of the container we want to log into.

Once this command is run, you should be inside your container. You are now ready to go through the different practices.
