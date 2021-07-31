# High Performance MangaDex@Home Client

Proof of concept.

- Utilize the performance and stability of _nginx_ as underlying reverse proxy and image cache.
- Highly customizable due to easy manipulation of the _nginx_ configuration template and the _NodeJS_ application script.
- Verification of expiration tokens is not yet supported (and probably never will).

## Setup (Ubuntu)

```bash
# install dependencies
curl -sL https://deb.nodesource.com/setup_14.x | sudo bash -
apt-get update
apt-get install -y nginx nodejs

# start
./mdathx --key=xxxxxxxx --port=44300 --cache=./cache --size=512 # --no-ssl

# verify
apt-get install -y curl
curl --insecure -I 'https://127.0.0.1:44300/data/8172a46adc798f4f4ace6663322a383e/B18-8ceda4f88ddf0b2474b1017b6a3c822ea60d61e454f7e99e34af2cf2c9037b84.png'
curl --insecure -I 'https://127.0.0.1:44300/-/data/8172a46adc798f4f4ace6663322a383e/B18-8ceda4f88ddf0b2474b1017b6a3c822ea60d61e454f7e99e34af2cf2c9037b84.png'

# benchmark
apt-get install -y apache2-utils
ab -n 2500 -c 50 'https://127.0.0.1:44300/-/data/8172a46adc798f4f4ace6663322a383e/B18-8ceda4f88ddf0b2474b1017b6a3c822ea60d61e454f7e99e34af2cf2c9037b84.png'
```

There are also some [docker images](https://hub.docker.com/r/mangadexnetwork/mdathx) available for poking around without installation ...

## Build (Docker)

```bash
# alpine based
docker build -f ./Dockerfile.alpine -t mangadexnetwork/mdathx:latest-alpine .
docker push mangadexnetwork/mdathx:latest-alpine

# ubuntu based
docker build -f ./Dockerfile.ubuntu -t mangadexnetwork/mdathx:latest-ubuntu .
docker tag mangadexnetwork/mdathx:latest-ubuntu mangadexnetwork/mdathx:latest
docker push mangadexnetwork/mdathx:latest-ubuntu
docker push mangadexnetwork/mdathx:latest
```