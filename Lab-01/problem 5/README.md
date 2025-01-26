### 1. Create a Docker Volume
To create a Docker volume named `mysql_data`, run the following command:
```bash
docker volume create mysql_data
```
This command creates a volume that will be used to persist MySQL data.

---

### 2. Deploy a MySQL Database Container
To deploy a MySQL database container named `app-database` using the latest MySQL image, follow these steps:

1. Run the container using the `-e` flag to set the MySQL root password:
   ```bash
   docker run -d --name app-database \
     -e MYSQL_ROOT_PASSWORD=P4sSw0rd0! \
     -v mysql_data:/var/lib/mysql \
     mysql:latest
   ```
   
   Explanation of the command:
   - `-d`: Runs the container in detached mode (in the background).
   - `--name app-database`: Assigns the name `app-database` to the container.
   - `-e MYSQL_ROOT_PASSWORD=P4sSw0rd0!`: Sets the MySQL root password to `P4sSw0rd0!`.
   - `-v mysql_data:/var/lib/mysql`: Mounts the `mysql_data` volume to `/var/lib/mysql`, the directory where MySQL stores its data.
   - `mysql:latest`: Specifies the MySQL image to use, with the `latest` tag.

---

### 3. Verify the Container is Running
To ensure the container is running successfully, use the following command:
```bash
docker ps
```
This command lists all running containers. You should see an entry for `app-database` with the MySQL image.

---

### 4. Access the MySQL Database
To access the MySQL database inside the container:

1. Open a bash shell in the running container:
   ```bash
   docker exec -it app-database /bin/bash
   ```

2. Access the MySQL client:
   ```bash
   mysql -u root -p
   ```

3. Enter the root password (`P4sSw0rd0!`) when prompted.
