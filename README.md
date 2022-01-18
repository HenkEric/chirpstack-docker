# ChirpStack Docker

This repository contains a skeleton to setup the [ChirpStack](https://www.chirpstack.io)
open-source LoRaWAN Network Server stack using [Docker Compose](https://docs.docker.com/compose/).

## Directory layout
* `docker-compose.yml`: the docker-compose file containing the services/containers
* `configuration/chirpstack*`: directory containing the ChirpStack configuration files, see:
    * https://www.chirpstack.io/gateway-bridge/install/config/
    * https://www.chirpstack.io/network-server/install/config/
    * https://www.chirpstack.io/application-server/install/config/
* `configuration/postgresql/initdb/`: directory containing PostgreSQL initialization scripts

## Configuration
The ChirpStack stack components components are pre-configured to work with the provided
`docker-compose.yml` file and defaults to the EU868 LoRaWAN band. Please refer
to the `configuration/chirpstack-network-server/examples` directory for more configuration
examples.

# Data persistence
Redis data is persisted in Docker volumes, see the `docker-compose.yml`
`volumes` definition.

## Requirements
Before using this `docker-compose.yml` file, make sure you have [Docker](https://www.docker.com/community-edition)
installed.

## Usage
1. Establish a performing PostgreSQL server/database
2. Run the provided scripts (```configuration/postgresql/initdb/```)
3. Rename ```.env.sample``` to ```.env``` and verify each variable
4. Run ```docker-compose up```

After all the components have been initialized and started, you should be able
to open;
- http://localhost:8080/ for the ChirpStack application server.

### Add Network Server
When adding the Network Server in the ChirpStack Application Server web-interface
(see [Network Servers](https://www.chirpstack.io/application-server/use/network-servers/)),
you must enter `chirpstack-network-server:8000` as the Network Server `hostname:IP`.
