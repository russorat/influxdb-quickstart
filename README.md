# Plaid quickstart again

This repository accompanies InfluxDB's **quickstart guide**.

Here you'll find full example integration app using our [**client libraries**][libraries]:

## Table of contents

- [1. Clone the repository](#1-clone-the-repository)
- [2. Set up your environment variables](#2-set-up-your-environment-variables)
- [3. Run the quickstart](#3-run-the-quickstart)
  - [Run with Docker](#run-with-docker)
    - [Pre-requisites](#pre-requisites-1)
    - [Running](#running-1)
      - [Start the container](#start-the-container)
      - [View the logs](#view-the-logs)
      - [Stop the container](#stop-the-container)
  - [Run without Docker](#run-without-docker)
    - [Pre-requisites](#pre-requisites)
    - [1. Running the backend](#1-running-the-backend)
      - [Python](#python)

## 1. Clone the repository

Using https:

```
$ git clone https://github.com/russorat/influxdb-quickstart
$ cd influxdb-quickstart
```

Alternatively, if you use ssh:

```
$ git clone git@github.com:russorat/influxdb-quickstart.git
$ cd influxdb-quickstart
```

## 2. Set up your environment variables

```
$ cp .env.example .env
```

Copy `.env.example` to a new file called `.env` and fill out the environment variables inside. At
minimum `INFLUXDB_URL`, `INFLUXDB_ORG` and `INFLUXDB_TOKEN` must be filled out. Get your values from
your InfluxDB Cloud account: https://cloud2.influxdata.com

> NOTE: `.env` files are a convenient local development tool. Never run a production application
> using an environment file with secrets in it.

## 3. Run the Quickstart

There are two ways to run the quickstart in this repository. You can simply choose to use Docker, or you can run the
code directly. If you would like to run the code directly, skip to the
[Run without Docker](#run-without-docker) section.

### Run with Docker

#### Pre-requisites

- `make` available at your command line
- Docker installed and running on your machine: https://docs.docker.com/get-docker/
- Your environment variables populated in `.env`
- If using Windows, a working Linux installation on Windows 10. If you are using Windows and do not already have WSL or Cygwin configured, we recommend [running without Docker](#run-without-docker).

#### Running

There are three basic `make` commands available

- `up`: builds and starts the container
- `down`: stops the container
- `logs`: tails logs

##### Start the container

```
$ make up
```

The quickstart backend is now running on http://localhost:8000.

If you make changes to one of the server files, simply run `make up language=node` again to rebuild and restart the container.

If you experience a Docker connection error when running the command above, try the following:

- Make sure Docker is running

##### View the logs

```
$ make logs
```

##### Stop the container

```
$ make down
```

### Run without Docker

#### Pre-requisites

- The language you intend to use is installed on your machine and available at your command line.
  This repo should generally work with active LTS versions of python >= 3.8.
- Your environment variables populated in `.env`
- If using Windows, a command line utility capable of running basic Unix shell commands

#### 1. Running the backend

Once started with one of the commands below, the quickstart will be running on http://localhost:8000 for the backend.

##### Python

**:warning: As `python2` has reached its end of life, only `python3` is supported.**

```
$ cd ./python

# If you use virtualenv
# virtualenv venv
# source venv/bin/activate

$ pip install -r requirements.txt
$ ./start.sh
```

If you get this error message:

```
ssl.SSLError: [SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed (_ssl.c:749)
```

You may need to run the following command in your terminal for your particular version of python in order to install SSL certificates:

```
# examples:
open /Applications/Python\ 3.9/Install\ Certificates.command
# or
open /Applications/Python\ 3.6/Install\ Certificates.command
```

[libraries]: https://docs.influxdata.com/influxdb/cloud/api-guide/client-libraries/
[python-example]: /python
[docker]: https://www.docker.com
