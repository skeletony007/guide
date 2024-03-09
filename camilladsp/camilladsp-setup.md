# Installing CamillaDSP (macOS Apple Silicon)

> Video demo -> <https://youtu.be/O8YpPSXKzuE>
>
> Disable recording indicator (orange dot) -> <https://github.com/cormiertyshawn895/RecordingIndicatorUtility>

Install CamillaDSP

```
wget https://github.com/HEnquist/camilladsp/releases/download/v1.0.3/camilladsp-macos-aarch64.tar.gz 
tar -zxvf camilladsp-macos-aarch64.tar.gz
```

Organise and cleanup

```
mkdir ~/.camilladsp
rm camilladsp-macos-aarch64.tar.gz
mv camilladsp ~/.camilladsp
```

## Using AutoEq2CamillaDSP

Using [AutoEQ] with [AutoEQ2CamillaDSP] and [[blackhole/blackhole-setup]] on
macOS (Apple Silicon).

Existing `config.yml` files in `.dotfiles/.camilladsp`.

Install `autoeq2camilladsp`

```
wget https://github.com/Ebert-Hanke/autoeq2camilladsp/releases/download/v0.5.2/autoeq2camilladsp-macos-arm64.zip
unzip autoeq2camilladsp-macos-arm64.zip
```

Organise and cleanup

```
mkdir ~/.camilladsp
rm autoeq2camilladsp-macos-arm64.zip
mv autoeq2camilladsp ~/.camilladsp
```

Execute `autoeq2camilladsp`

```
~/.camilladsp/autoeq2camilladsp
```

1. Select your device in the tui. (type the name, arrow keys to navigate)

2. Select `no`; no custom `devices` section.

3. Select `None`; do not include Crossfeed.

Then the `config.yml` will be created :)

Change the `capture` and `playback` devices

```yml
  capture:
    type: CoreAudio
    channels: 2
    device: "BlackHole 2ch"
  playback:
    type: CoreAudio
    channels: 2
    device: "MacBook Air Speakers"
```

where the `capture` device is selected as output for programs and the
`playback` device is the used output device.

Also move the `config.yml` to somewhere you can find it.

Command to show audio devices:

```
system_profiler SPAudioDataType
```

Example output

```
Audio:

    Devices:

        BlackHole 2ch:

            ...

        MacBook Air Speakers:

            ...

```

[AutoEQ]: https://github.com/jaakkopasanen/AutoEq

[AutoEQ2CamillaDSP]: https://github.com/Ebert-Hanke/autoeq2camilladsp
