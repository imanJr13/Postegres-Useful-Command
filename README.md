# Postegres-Useful-Command


## List the running Docker containers to find the container ID of your PostgreSQL instance. Open a terminal and run the following command:

```
docker ps
```

This will display a list of running containers along with their details.

Once you have identified the container ID for your PostgreSQL instance, use the following command to access the container's shell:

```
docker exec -it <container_id> bash
```

Replace <container_id> with the actual ID of your PostgreSQL container.

Inside the container's shell, connect to the PostgreSQL server using the psql command-line tool:
```
psql -U <username> -d <database_name>
```

Replace <username> with the appropriate username and <database_name> with the name of the database you want to delete (e.g., 'Tracer').

Run the following SQL query to see which sessions are currently connected to the database:

```
SELECT pid, usename, application_name FROM pg_stat_activity WHERE datname = 'Tracer';
```
This will display a list of active sessions connected to the 'Tracer' database.

For each session that you want to disconnect, run the following command, replacing <pid> with the process ID of the session:
```
SELECT pg_terminate_backend(<pid>);
```

This will force the disconnection of the specified session.
