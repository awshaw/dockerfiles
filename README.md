# Docker containers
This repo contains some dockerfiles I use to get my development environment setup quickly for machine learning. 

Feel free to clone and add, edit, and use.

## Setting up a container with GPU support

*(This assumes you have Docker and [**nvidia-docker**](https://github.com/NVIDIA/nvidia-docker "Title") installed)*

* First, build your container;
```
container_name=mlcont   # name of container
docker build --rm -t ${container_name} .

# test that drivers are installed
nvidia-docker run --rm ${container_name} nvidia-smi 
```
Run the container, and add your desired folders to share with the container;
```
nvidia-docker run -it -p 8888:8888 -p 6060:6060 -v /host/data:/data -v /host/config:/config ${container_name} bash
```

* Once you are inside the container;
```
jupyter notebook --allow-root --ip=0.0.0.0 --port=8888
```
