# Matomo-on-premises

This document explain how to setup the Matomo analytics tool on premises with docker image.

The docker image which I used at the time of setup is **matomo:4.5.0-apache** and latest docker image available is **matomo:4.6.2-apache**

Steps for running Matomo -

1. Create EC2 instance for running *Matomo*
2. Give Access on port 80 with security group or what ever preferred port number.
3. SSH the EC2 machine.
4. install docker on EC2 machine with appropriate config.
5. Create folder *Matomo*
6. cd *Matomo*
7. create env file .env.production with the variable -
  - MATOMO_DATABASE_HOST=**host url of my sql db** 
  - MATOMO_DATABASE_USERNAME=**user name for my sql db**
  - MATOMO_DATABASE_PASSWORD=**password for user**
  - MATOMO_DATABASE_DBNAME=**database used**  [^1]
8. execute the below sh command for running the Matomo with docker. Change the port if any.

```sh
docker run --env-file "$(pwd)/.env.production" --restart=always --name weatherspork-matomo -p 80:80 -v "$(pwd)/data:/var/www/html" -d matomo:4.5.0-apache
```

[^1] Create a seperate db for Matomo
