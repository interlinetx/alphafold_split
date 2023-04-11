# Building the MSA-only AlphaFold Docker image

To build the image on a local machine, run the following in the top direcotry of this repo:

`docker build --build-arg -f docker/Dockerfile-msa -t alphafold-split .`

Note that if you're building this on Apple Silicon, you'll need to specify the architecture for installing
Miniconda with the `CONDARCH` Docker build arg:

`docker build --build-arg CONDARCH=Linux-aarch64 -f docker/Dockerfile-msa -t alphafold-split .`

## Building and pushing to a remote Docker image repository

Use Docker's buildx capability to 

` docker buildx build -f docker/Dockerfile-msa --platform linux/amd64 --network host --push -t 056117122700.dkr.ecr.us-west-2.amazonaws.com/alphafold-split:latest .`