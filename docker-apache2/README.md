# Build the Docker image for java application
`docker build -t infosys-website  .`

# Run the Java App Docker container
`docker run --name infosys-webserver -d -p 8080:80 infosys-website `

# stop the java app container
`docker stop infosys-website`

# remove java app container
`docker rm infosys-website`
