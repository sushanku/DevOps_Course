# Build the Docker image
docker build -t infosys-website  .

# Run the Docker container
docker run --name infosys-webserver -d -p 8080:80 infosys-website 

# stop the container
docker stop infosys-website

# remove container
docker rm infosys-website

