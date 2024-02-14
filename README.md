# Local ELK Stack
Local ELK Stack, backup tool, and more.

## Table of Contents
- [The Stack](#the-stack)
- [Running Backups](#running-backups)

## The Stack
The stack consists of the core components: Elasticsearch, Logstash, and Kibana.
There is also a Fluentd service for logging, as well as Logstash pipeline configurations.

## Running the Stack

The command `docker-compose` can read environment variables from an `.env` file (e.g., `mv .env_sample .env`)

```bash
# Build and run the stack
docker-compose up
docker-compose --build

# Shutdown the stack
docker-compose down
docker-compose down --remove-orphans
```

## Running Backups
To back up data volumes, such as `elasticsearch_data`, launch a `busybox` Docker container to execute
the shell script `./backup/volume_backups.sh` to archive the volumes
and store the archives in the `backup` folder.


```bash
# Run Docker Container and shell script
docker-compose run backup
```

You can schedule the Docker container to run periodically by adding the docker-compose command to your crontab.

```bash
# Open your crontab file in edit mode
crontab -e

# Add a line like this to run the backup daily at a specific time, such as 2 AM:
0 2 * * * docker-compose -f /path/to/your/docker-compose.yml run backup
```
