# docker_mongodb
test create a container mongodbs
"files this projects"
1. compose.yaml
- image mongodb 
    einvironment: 
     - username 
     - password 
- image mongo-express
    - port
    environment
     - url, username, password 
2. .env
 password and username for db are hidden in this file.
3. .gitignore
 - hide .env

"test result"
 mongodb container: repeat retarting.
 mongo-express: successfully created.
"why is'nt created mongo container"
 1. check log: sudo docker logs mongodb-mongo-1
 2. find the couse of this problem.
     - conflict between kernel of linux(os of the host pc) and mongo.
 3. add "command: mongod --ignoreUnknownKernel" in the compose.yaml
   => problem wasn't resolved.
 4. next try: change mongo version.
     from mongo:latest => mongo:7.0
   => problem is resolved.
