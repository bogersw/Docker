# Dockerfile

This Dockerfile can be used to create Python 3.12.5 docker images that runs Jupyterlab when run as a container. There
are two versions of the _requirements.txt_ file:

-   **requirements_base_ds.txt**: the base Python environment with a lot of the standard data science packages (numpy,
    pandas, seaborn and so on).
-   **requirements_full_ds.txt**: contains all the packages from the base Python environment but also packages for
    machine learning (keras, tensorflow and so on).

Copy one of these to **requirements.txt** (this is the file that is referenced in the _Dockerfile_).

# Building the images

Run the Docker _build_ command from the directory where the _Dockerfile_ and the _requirements.txt_ file are located:

Base environment:

```
docker build -t python_jupyter_base_ds:v3.12.5 .

docker run -d -p 8889:8888 --mount type=bind,source="${PWD}"/jupyter,target=/home/jupyter --name Jupyter_base python_jupyter_base_ds:v3.12.5
```

Full environment:

```
docker build -t python_jupyter_full_ds:v3.12.5 .

docker run -d -p 8889:8888 --mount type=bind,source="${PWD}"/jupyter,target=/home/jupyter --name Jupyter_full python_jupyter_full_ds:v3.12.5
```

The Docker _run_ command can be executed from any directory if the docker daemon is active. Make sure that a
subdirectory _jupyter_ is present in that directory.

The host directory from which the docker container is started will be mounted to _/home/jupyter_ in the container.
