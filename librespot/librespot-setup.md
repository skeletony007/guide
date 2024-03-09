[GitHub](https://github.com/librespot-org/librespot)

> Spotify Connect receiver

# Installing librespot on macOS

Install librespot

```
brew install librespot
```

# Installing librespot on Android Termux

> Using instructions from:
> https://www.reddit.com/r/termux/comments/q8ydao/is_running_a_spotify_connect_client_on_a_phone/

Install `librespot` using the [pulseaudio backend](https://github.com/librespot-org/librespot/wiki/Compiling#features)

```
pkg install rust pulseaudio
cargo install librespot --no-default-features --features "pulseaudio-backend"  # ℹ️ run this to update as well
```

`librespot` is in the directory `/data/data/com.termux/files/home/.cargo/bin/librespot`.

To execute just `librespot`, add the Cargo bin directory to `PATH`

```
echo export PATH="$HOME/.cargo/bin:$PATH" >> ~/.bashrc && source ~/.bashrc
```

(this assumes you are using `bash`)

# Usage

Start `librespot` with receiver\* configuration

```
librespot --disable-audio-cache --disable-credential-cache -n DEVICENAME -b 320 --format F32 --disable-gapless
```

See examples of [usage options](https://github.com/librespot-org/librespot/wiki/Options).
