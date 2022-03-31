# Crater contianer

**ATTENTION** these images are still being developed and tested and should only be used by Crater contributors.

Deploy *Crater* as a containerized application using Docker.

When testing SSL the container will create a Self-Signed certificate in the ``certificates`` volume. If you already have a valid certificate and private key for the domain that you're testing with, then copy the respective files to the certificates volume named ``crater.pem`` and ``crater.key`` and restart the container.

If testing SSL certificates using Lets Encrypt 
1. The domain is valid and it can be accessed from the internet
2. LETSENCRYPT_STAGING is set to true in the ``.env`` file

## Using the images

Download the docker compose and sample environment file from the repository
```
git clone https://github.com/irsheep/crater-image
cp .env.example .env
# Edit .env as required
```

Start the container
```
docker-compose up -d
```

Stop the container
```
docker-compose stop
```

Remove the container
```
docker-compose down
```

Remove the container including volumes 
```
docker-compose down -d
```

## volumes

By default **Crater container** will create four volumes, to hold persistent data.

- app: This will hold uploaded files and generated PDFs
- database: Crater MySQL database files
- certificates: If SSL is enable Nginx will look in this volume for ```crater.pem``` and ```crater.key``` for the certificate file and key respectivetly.
- acme: Lets Encrypt data
