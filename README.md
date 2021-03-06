# Shairport-sync on docker on raspi

## Build docker container image for raspberry pi zero/w

``` shell
docker build -t "rpi-shairport-sync-alpine" -f Dockerfile.arm32v6 .
```

## Run container for raspberry pi zero/w

``` shell
docker run -d --net host --device /dev/snd --restart always \
--mount type=bind,src=$(pwd)/shairport-sync.conf,dst=/etc/shairport-sync.conf \
-e AIRPLAY_NAME=RaspiZero1 rpi-shairport-sync-alpine
```

## Run container for raspberry pi 3

``` shell
docker-compose up -d
```

## Setup for Raspberry Pi 3

Add the following lines to `/boot/config.txt`

```txt
disable_pvt=1
force_turbo=1
audio_pwm_mode=2
audio_sdm_mod_order=2
```

then reboot.

After reboot, issue the following command

```shell
$ sudo amixer cset numid=3 1
```

Maximize volume using alsamixer (in `alsa-utils` package).


## Setup for Raspberry pi with pHAT DAC

Make sure that Raspbian is up-to-date.
Run the following one-line installer

```bash
curl https://get.pimoroni.com/phatdac | bash
```

See [this web site][SetupPhatDac] for detail.

## TODO

- [ ] Confirm that all the above setup steps are relevant
- [ ] Modify `shairport-sync.conf` for raspi with pHAT DAC
- [ ] Integrate with snapcast


[SetupPhatDac]: https://learn.pimoroni.com/tutorial/phat/raspberry-pi-phat-dac-install
