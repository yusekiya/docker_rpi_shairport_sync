# Shairport-sync on docker on raspi

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
$ curl https://get.pimoroni.com/phatdac | bash
```

See [this web site][SetupPhatDac] for detail.

## TODO

- [ ] Confirm that all the above setup steps are relevant
- [ ] Modify `shairport-sync.conf` for raspi with pHAT DAC
- [ ] Integrate with snapcast


[SetupPhatDac]: https://learn.pimoroni.com/tutorial/phat/raspberry-pi-phat-dac-install
