# Static Docker Container.
Docker templates for building a small static NGINX site using docker - serves as a proof of concept.

## Setup, Configure and Run Containers
1. Generate Site Certificates
The `bin\generate-certs.sh` script can be used to create the required certificate directory `./ssl` and generate certificates for both the site and CDN server.
2. Update docker environment variables in the `docker.env` file.
3. Update host file to include the IP address for cdn.localhost and site.localhost (127.0.0.1 if ran locally).
```
127.0.0.1 cdn.localhost site.localhost
::1 cdn.localhost site.localhost
```

4. Load docker variables into current session.
```
[user@host container-static]$ set -a
[user@host container-static]$ source docker.env
```

5. Build docker containers.
```
[user@host container-static]$ docker-compose build
```

6. Start docker containers.
```
[user@host container-static]$ docker-compose up -d
```

7. Open a web browser and navigate to the URI `https://cdn.localhost`. Once prompted accept certification.
8. Navigate to the URI `https:/site.localhost`. Once prompted accept certification. The page `.\test-site\html\index.html` will be displayed.

