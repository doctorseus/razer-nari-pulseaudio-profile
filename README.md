# Razer Nari pulseaudio profile

The Razer Nari is a gaming headset which has two stereo audio outputs. One for voice chat and one for the rest of the sound. It can be mixed between with a physical knob.

By default, pulseaudio only enables the voice chat output. This profile enables the second (game) output and the udev rule makes sure this profile is used when plugging in the device.

This solves the problem when only **mono** output is recognized for Nari.

## Installing

Install by copying the following files:

- `razer-nari-output-game.conf` and `razer-nari-output-chat.conf` to `/usr/share/pulseaudio/alsa-mixer/paths/`
- `razer-nari-usb-audio.conf` to `/usr/share/pulseaudio/alsa-mixer/profile-sets/`
- `91-pulseaudio-razer-nari.rules` to `/lib/udev/rules.d/`

Script:
```
cp razer-nari-output-{game,chat}.conf /usr/share/pulseaudio/alsa-mixer/paths/
cp razer-nari-usb-audio.conf /usr/share/pulseaudio/alsa-mixer/profile-sets/
cp 91-pulseaudio-razer-nari.rules /lib/udev/rules.d/
```

Restart pulseaudio:

    pulseaudio -k
    pulseaudio --start

After that, plug in the device to see if it works.
