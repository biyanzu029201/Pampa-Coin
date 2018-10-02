### Setup docker on Debian 8.1

Install notes: https://docs.docker.com/install/linux/docker-ce/debian/#install-using-the-repository

Docker CLI: https://docs.docker.com/engine/reference/run/

Script that installs docker-ce: `setup_docker_debian.sh`

### Build&Run PAMPA docker container

Pre: `PampaCoin.conf MUST be available under link PAMPA_CONF_URL as pointed out in the Dockerfile`

Build container: `sudo docker build --tag pampa:1.0.3 .`

Run container: `docker run -d --name pampa.cont pampa:1.0.3`

See if it is up: `docker ps -a`

Shell in the container: `docker exec -it pampa.cont /bin/bash`

Test RPC: `pampa-cli -rpcuser=pampa -rpcpassword=<from config file> help`

Stop container: `docker stop pampa.cont`

Delete container: `docker rm pampa.cont`