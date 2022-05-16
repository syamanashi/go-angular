# A simple web application written with Go and Angular

===================================================

[![Build Status](https://travis-ci.com/Shpota/go-angular.svg?branch=master)](https://travis-ci.com/Shpota/go-angular)

I implemented this application while evaluating Go.
On the back end side, I used
[gorilla/mux](https://github.com/gorilla/mux) for
routing, [Gorm](https://github.com/jinzhu/gorm) as an
ORM engine and
[google/uuid](https://github.com/google/uuid)
for UUID generation. On the front end side, I used
[Angular 8](https://angular.io/) and
[Angular Material](https://material.angular.io/).

![Showcase](showcase/showcase.gif)

## System requirements

You need to have [Docker](https://www.docker.com)
installed in order to build and run the application.
No additional tools required.

## How to build and run

1. Create a Docker network:

2. ```shell script
   docker network create students-net
   ```

3. Start the DB:

4. ```shell script
   docker run \
     -e POSTGRES_USER=go \
     -e POSTGRES_PASSWORD=your-strong-pass \
     -e POSTGRES_DB=go \
     --name students-db \
     --net=students-net \
     postgres:11.5
   ```

5. Build the application image:

   ```shell script
   docker build -t students-app .
   ```

6. Start the application container:

   ```shell script
   docker run -p 8080:8080 \
     -e DB_PASS='your-strong-pass' \
     --net=students-net students-app
   ```

Access the application via <http://localhost:8080>
