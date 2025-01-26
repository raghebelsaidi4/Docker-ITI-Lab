

### Run an HTTPD container with volumes for static files and configuration
To run an HTTPD container with two volumes attached, follow these steps:

1. Create directories on your host machine to serve as volumes:
   ```bash
   mkdir -p /path/to/static-html
   mkdir -p /path/to/httpd-config
   ```

2. Run the HTTPD container with the volumes attached:
   ```bash
   docker run -d --name apache \
     -v /path/to/static-html:/usr/local/apache2/htdocs \
     -v /path/to/httpd-config:/usr/local/apache2/conf \
     httpd
   ```

3. Stop and remove the HTTPD container:
   ```bash
   docker stop apache
   docker rm apache
   ```

---

### Run a new HTTPD container with port mapping and the same volumes
To run a new HTTPD container with the previous volumes and map port 80 to 9898 on the host machine:

1. Run the container:
   ```bash
   docker run -d --name apache \
     -v /path/to/static-html:/usr/local/apache2/htdocs \
     -v /path/to/httpd-config:/usr/local/apache2/conf \
     -p 9898:80 \
     httpd
   ```

2. Access the static HTML files from your browser:
   Open your web browser and navigate to:
   ```
   http://localhost:9898
   ```
   You should see the static HTML files served by the HTTPD container.
