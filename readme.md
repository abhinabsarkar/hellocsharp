# Dockerfile & Source code for image - abhinabsarkar/abs-hello-csharp:v1

## To build the image, run docker build from the root directory of the application
```bash
# Build the abs image
docker build -t abs-hello-csharp:v1 .
# Run the docker container locally
# The release version runs the container at port 80 although the app is running at port 5000
docker run --name abs-hello-csharp-container -d -p 8002:80 abs-hello-csharp:v1
# Check the status of the container
docker ps -a | findstr abs-hello-csharp-container
# Test the app
curl http://localhost:8002/abs
# log into the running container 
docker exec -it abs-hello-csharp-container /bin/bash
docker exec -it abs-hello-csharp-container <command>
# Remove the container
docker rm abs-hello-csharp-container -f
# Remove the image
docker rmi abs-hello-csharp:v1
# Push the image to docker hub
docker login
# Tag the local image & map it to the docker repo
docker tag local-image:tagname new-repo:tagname
# eg: docker tag abs-hello-csharp:v1 abhinabsarkar/abs-hello-csharp:v1
# push the tagged image to the docker hub
docker push new-repo:tagname
# eg: docker push abhinabsarkar/abs-hello-csharp:v1
```