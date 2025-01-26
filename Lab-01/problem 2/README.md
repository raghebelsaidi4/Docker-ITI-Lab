### 1. Run a CentOS or Ubuntu container in interactive mode
To start a container interactively, use one of the following commands based on your preferred base image:

For CentOS:
```bash
docker run -it --name my-container centos /bin/bash
```

For Ubuntu:
```bash
docker run -it --name my-container ubuntu /bin/bash
```

---

### 2. Run the command `echo docker` in the container
Inside the container, execute the following command:
```bash
echo docker
```
This command outputs the word `docker` to the terminal.

---

### 3. Open a bash shell in the container and create a file named `hello-docker`
If you have exited the container but need to interact with it again, you can reopen a bash shell using:
```bash
docker exec -it my-container /bin/bash
```
Once inside the container, create a file named `hello-docker` using the `touch` command:
```bash
touch hello-docker
```
This creates an empty file named `hello-docker` in the current directory inside the container.

---

### 4. Stop and remove the container
After completing your tasks, follow these steps to stop and remove the container:

- Exit the container:
  ```bash
  exit
  ```

- Stop the container:
  ```bash
  docker stop my-container
  ```

- Remove the container:
  ```bash
  docker rm my-container
  ```

**Note:** The `hello-docker` file created inside the container will no longer exist after the container is removed. Docker containers are stateless, meaning any data not explicitly persisted (e.g., using volumes) will be lost.

---

### 5. Remove all stopped containers
To clean up all stopped containers and free up system resources, run the following command:
```bash
docker container prune -f
```
This removes all stopped containers from your system.

---

