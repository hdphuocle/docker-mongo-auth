# docker-mongo-auth
A Docker Image for MongoDB which makes it easy to create an Admin, a Database and a Database User when the container is first launched.

# Customization
There are a number of environment variables which you can specify to customize the username and passwords of your users. 

- With Dockerfile
  ```
  // Auth Configuration.
  // These environment variables can also be specified through command line or docker-compose configuration
  # ENV AUTH yes

  # ENV MONGODB_ADMIN_USER root
  # ENV MONGODB_ADMIN_PASS password

  # ENV MONGODB_APPLICATION_DATABASE your_db
  # ENV MONGODB_MAINTAIN_USER user
  # ENV MONGODB_MAINTAIN_PASS password
  # ENV MONGODB_DEVELOP_USER user
  # ENV MONGODB_DEVELOP_PASS password
  # ENV MONGODB_TESTER_USER user
  # ENV MONGODB_TESTER_PASS password
  ```
  
- With docker-compose.yml
  ```
  services:
    db:
      image: aashreys/mongo-auth:latest
      environment:
        - AUTH=yes
        - MONGODB_ADMIN_USER=admin
        - MONGODB_ADMIN_PASS=admin123
        - MONGODB_APPLICATION_DATABASE=sample
        - MONGODB_MAINTAIN_USER=aashrey
        - MONGODB_MAINTAIN_PASS=admin123
        - MONGODB_DEVELOP_USER=aashrey
        - MONGODB_DEVELOP_PASS=admin123
        - MONGODB_TESTER_USER=aashrey
        - MONGODB_TESTER_PASS=admin123
      ports:
        - "27017:27017"
  // more configuration
  ```

- With command line
  ```
  docker run -it \
    -e AUTH=yes \
    -e MONGODB_ADMIN_USER=admin \
    -e MONGODB_ADMIN_PASS=adminpass \
    -e MONGODB_APPLICATION_DATABASE=mytestdatabase \
    -e MONGODB_APPLICATION_USER=testuser \
    -e MONGODB_APPLICATION_PASS=testpass \
    -p 27017:27017 aashreys/mongo-auth:latest
  ```

