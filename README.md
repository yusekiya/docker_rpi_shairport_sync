# Shairport-sync on docker on raspi

## Setup

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

Maximize volume using alsamixer.

## TODO

- [ ] Confirm that all the above setup steps are relevant
