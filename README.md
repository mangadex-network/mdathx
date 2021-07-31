# High Performance MangaDex@Home Client

Based on nginx

## Run (Ubuntu)

```bash
# install dependencies
curl -sL https://deb.nodesource.com/setup_14.x | sudo bash -
apt-get install -y nginx nodejs apache2-utils
npm install
# start
./mdathx --key=xxxxxxxx --port=44300 --cache=./cache --size=512
# verify
curl --insecure -I 'https://127.0.0.1:44300/data/8172a46adc798f4f4ace6663322a383e/B18-8ceda4f88ddf0b2474b1017b6a3c822ea60d61e454f7e99e34af2cf2c9037b84.png'
curl --insecure -I 'https://127.0.0.1:44300/-/data/8172a46adc798f4f4ace6663322a383e/B18-8ceda4f88ddf0b2474b1017b6a3c822ea60d61e454f7e99e34af2cf2c9037b84.png'
# benchmark
ab -n 2500 -c 50 'https://127.0.0.1:44300/-/data/8172a46adc798f4f4ace6663322a383e/B18-8ceda4f88ddf0b2474b1017b6a3c822ea60d61e454f7e99e34af2cf2c9037b84.png'
```

## Build Docker (Ubuntu)

```bash
docker build -f ./Dockerfile.ubuntu -t mangadexnetwork/mdathx:latest-ubuntu .
docker tag mangadexnetwork/mdathx:latest-ubuntu mangadexnetwork/mdathx:latest
docker push mangadexnetwork/mdathx:latest-ubuntu
docker push mangadexnetwork/mdathx:latest
```

## Build Docker (Alpine)

```bash
docker build -f ./Dockerfile.alpine -t mangadexnetwork/mdathx:latest-alpine .
docker push mangadexnetwork/mdathx:latest-alpine
```