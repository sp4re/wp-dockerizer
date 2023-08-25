# wp-dockerizer
Full WordPress service with Self-signed SSL Certs

## What is this?

This is a docker-compose project that creates containarized workloads required to build a functioning WordPress site.

Docker-compose.yaml builds MYSQL database, NGINX websevices and generates self-signed certificates for SSL (certbot).

## Installing

Installation is quite straighforward:

1. Create your own .env file with the information you wish to pass on to the Docker containers.

   > cp env.template .env

2. Open the newly create .env in your favorite text editor and update the variables.

3. Once all variables in .env file have been updated, user Docker compose to start the services.

    > docker-compose up -d 

4. Run the following command to check that all containers started without errors.

5. If all services started properly and certbot dry-run was successful, you are ready for creating the certificates.

6. Edit the certbot command in docker-compose.yaml on line 83 by removing the "--dry-run" flag and save changes. The certbot will now generate the certificates on next build.

7. Re-create the certbot container by running the following command:

    > docker-compose up --no-deps certbot

8. Re-create the ssl-nginx container to have it use the newly generated Certs

    > docker-compose up --no-deps ssl-nginx

9. Navigate to your domain and verify that the services are working as intended.

10. You have successfully setup a working Wordpress site!

## Debugging 

Debugging guides are yet to be created...
