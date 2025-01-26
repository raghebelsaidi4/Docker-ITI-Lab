### 1. Run the HTTPD Container Without Volumes
Run the HTTPD container without attaching any volumes using the following command:
```bash
docker run -dit --name apache httpd
```
This command starts a detached HTTPD container named `apache` with an interactive terminal.

---

### 2. Add Static HTML Files to the Container
To add static HTML files, execute the following steps:

1. Open a bash shell in the running container:
   ```bash
   docker exec -it apache /bin/bash
   ```

2. Add an HTML file to the container:
   ```bash
   echo "<h1>Welcome to My Custom HTTPD Server!</h1>" > /usr/local/apache2/htdocs/index.html
   ```

3. Exit the container:
   ```bash
   exit
   ```

---

### 3. Commit the Container to Create a New Image
Commit the changes in the container as a new Docker image using the following command:
```bash
docker commit apache IMAGE_NAME
```
Replace `IMAGE_NAME` with the desired name for your new image. This creates a new image containing the static HTML file added in the previous step.

---

### 4. Create a Dockerfile for the Committed Image
To replicate the committed image, create a `Dockerfile` with the following content:
```Dockerfile
# Use the official HTTPD image as the base image
FROM httpd

# Copy static files to the container
COPY index.html /usr/local/apache2/htdocs/
```

Place the `Dockerfile` and `index.html` in the same directory on your host machine.

---

### 5. Build the Image From the Dockerfile
To build a new image using the Dockerfile, execute the following command:
```bash
docker build -t IMAGE_NAME .
```
Replace `IMAGE_NAME` with your preferred image name. This command builds a new image from the Dockerfile and includes the static HTML file.

---

### 6. Run the Newly Built Image
To run a container from the newly built image, use the following command:
```bash
docker run -d -p 8080:80 --name custom-apache IMAGE_NAME
```
Replace `IMAGE_NAME` with the name of the image built in the previous step. This maps port 80 of the container to port 8080 on the host machine.

Access the static HTML file by navigating to:
```
http://localhost:8080
```

