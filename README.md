# cmse492-hw02-wijayaju
## Overview
This project utilizes a Dockerized MySQL database (using the Sakila sample database) and a Jupyter notebook to carry out a small, portfolio-ready SQL analysis.

## Accomplishments / Skills Showcased
As I explored the database, I have created the following queries:
- Multi-join queries
- Aggregate queries utilizing a HAVING statement
- CTE queries
- Window function queries
- Performance check queries
- Report queries

## Connecting to the Database
Skip to [Running the Notebook](#running-the-notebook) (the next section) if you don't want to run anything on your local computer and only want to see the results.

Before we connect to the database, we have to make sure docker is installed. Open a terminal and run:
```bash
docker --version
```

You should see output like `Docker version 29.x.x, build ...`. If the command is not found, download and install Docker Desktop from https://www.docker.com/products/docker-desktop/ (you may have to restart your machine before continuing, if `docker` is not recognized immediately after installation).

Now that Docker is installed, start up Docker Desktop. Next, in your terminal, ensure that you are in the folder with the docker-compose.yml file and run:
```bash
docker compose up -d
```

This starts MySQL and Adminer in detached mode. The first run may take a minute while Docker pulls images.

Verify both containers are running:

```bash
docker compose ps
```

You should see both `cmse492-mysql` and `cmse492-adminer` with status `running`.

To ensure that things are set up correctly, you can check that MySQL is listening on port `3306` on your local machine.

Use the command for your operating system:

- **macOS**
  ```bash
  lsof -nP -iTCP:3306 -sTCP:LISTEN
  ```

- **Linux**
  ```bash
  ss -ltnp | grep :3306
  ```

- **Windows PowerShell**
  ```powershell
  Get-NetTCPConnection -LocalPort 3306 -State Listen
  ```

You should see a process listening on port `3306`. If you get a port conflict, run `docker compose down` and stop any local MySQL/MariaDB service before retrying.

If you _are_ seeing a process already listening on port `3306`, here are examples for stopping local services:

- **macOS (Homebrew)**
  ```bash
  brew services stop mysql
  brew services stop mariadb
  ```

- **Linux (systemd)**
  ```bash
  sudo systemctl stop mysql
  sudo systemctl stop mariadb
  ```

- **Windows PowerShell (Run as Administrator)**
  ```powershell
  Stop-Service -Name MySQL80 -Force
  Stop-Service -Name MariaDB -Force
  ```

Now you're ready to run the notebook!

## Running the Notebook
To run the notebook, open [HW02-JustinWijaya.ipynb](HW02-JustinWijaya.ipynb) and run the code cells as you read along to see the queries run on your local computer. If you just want to see the results, don't run any of the cells as outputs are already made for easy viewing.
