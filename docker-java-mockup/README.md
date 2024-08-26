# Docker build and deploy info

# Build the Docker image for java application
`docker build -t java-mockup-app  .`

# Run the Java App Docker container
`docker run --name mockup-app -d -p 8080:4567 java-mockup-app`
Alternative cmd: \
`docker run --rm --name mockup-app --network=mockup-network -d -p 4567:4567 java-mockup-app`

# stop the java app container
`docker stop mockup-app`

# remove java app container
`docker rm mockup-app`

# to create a bridge network between mockup app and mysql db
`docker network create -d bridge mockup-network`

# database setup
`docker run --name mysql-db -v ./mysql_db/:/docker-entrypoint-initdb.d/ -e MYSQL_ROOT_PASSWORD=sushan01 -e MYSQL_USER=mockup -e MYSQL_PASSWORD=Mockup@123 -e MYSQL_DATABASE=mockup_db -p 3306:3306  -d mysql:8.0.39`
Alternative cmd: \
`docker run --name mysql-db -v --network=mockup-network ./mysql_db/:/docker-entrypoint-initdb.d/ -e MYSQL_ROOT_PASSWORD=sushan01 -e MYSQL_USER=mockup -e MYSQL_PASSWORD=Mockup@123 -e MYSQL_DATABASE=mockup_db -p 3306:3306  -d mysql:8.0.39`
The above command will run mysql version 8.0.39 and provides the root mysql password, mysql user db and credential and mysql DB and exposes port 3306 on localhost









<br>
<br>

# App Info
This is a simple java app which will display information on the browser whether it is a number or a string.\
If it is a number, it says "It is a number"\
If it is a string, it says "Hello $string" 

<br>

Endpoint example:\
**number**: http:/server_ip:4567/role/1\
**string**: http:/server_ip:4567/role/author


## Pre-requiste
1. Ubuntu server (Good if we have latest). It could be anyother linux distro as well.
2. Java installed on that Ubuntu server (Java version 17)
3. Maven install

## Installation command for ubuntu
1. Java: `sudo apt-get openjdk-17-jdk`
2. Maven: `sudo apt-get install maven`

## Build Info
To build this java maven app, use this command\
`mvn clean install`


## Deploy info
To build this java app, it has a dependency with config files and mysql database setup\
Config files has database name with it's endpoint, DB username and DB password.\
First let's setup DB, DB username and DB password. Also grant all the privileges to this user to the database.\
After setting up database, we need to import the DB schema. mockup_db.sql has the schema.\
`mysql -u db_username -p db_name < mockup_db.sql` \
<br>
db_username, db_name is what you have created from the etc/config.properties.

### setup application home 
create username called mockup in your linux server \
create folder in home directory of mockup \
copy etc folder in that new directory \
copy jar file to that new directory\
then execute:\
`java -jar artifact-name.jar`


### Stopping deployed application
Execute ./stop.sh \