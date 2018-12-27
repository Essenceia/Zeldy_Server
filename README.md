# Zeldy_Server

## Overview
The backend consists of :
- a time-series database : [InfluxDB](https://www.influxdata.com/)
- a web interface to visualize the data : [Grafana](https://grafana.com/)
- also used, but not included here, an NGINX reverse proxy that handles https

## Requirements
- docker
- docker-compose
- the ESP32 must be able to reach the machine hosting the InfluxDB database

## Quickstart
- Populate the `{grafana|influxdb}-variables.env` files, using the `.dist` templates provided
- `docker-compose up`
- The Grafana web interface is at `http://127.0.0.1:3000`, with the credentials given in `grafana-variables.env`
- Add a data source : `InfluxDB` at `http://influxdb:8086`, with the credentials and database name given in `influxdb-variables.env`

## Make it survive
Have it start as a background task with `docker-compose up -d`. It should survive reboots as is.
You may have to launch the docker daemon, and enable it at boot : `systemctl start docker` and `systemctl enable docker`
