MangaDex@Home nginx based Client

```bash
npm install
./mdathx --key=xxxxxxxx --port=44300 --cache=./cache --size=512
# testing
curl --insecure -I 'https://127.0.0.1:44300/data/8172a46adc798f4f4ace6663322a383e/B18-8ceda4f88ddf0b2474b1017b6a3c822ea60d61e454f7e99e34af2cf2c9037b84.png'
curl --insecure -I 'https://127.0.0.1:44300/-/data/8172a46adc798f4f4ace6663322a383e/B18-8ceda4f88ddf0b2474b1017b6a3c822ea60d61e454f7e99e34af2cf2c9037b84.png'
# benchmark
ab -n 2500 -c 50 'https://127.0.0.1:44300/-/data/8172a46adc798f4f4ace6663322a383e/B18-8ceda4f88ddf0b2474b1017b6a3c822ea60d61e454f7e99e34af2cf2c9037b84.png'
```