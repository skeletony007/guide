# keeweb

[GitHub](https://github.com/keeweb/keeweb)

Use this to quickly view passwords in a web browser.

# Installing KeePassXC on macOS

[GitHub](https://github.com/keepassxreboot/keepassxc)

```bash
brew install keepassxc
```

NOTE that `keepassxc-cli` does not install with the dmg package.

# Installing KeePassDX Android

[GitHub](https://github.com/Kunzisoft/KeePassDX)

[F-Droid](https://f-droid.org/en/packages/com.kunzisoft.keepass.libre/)

F-Droid is the recommended way of installing.

## keepasssc-cli in Termux 

Go to Settings → Apps → All Apps → Termux → Permissions. Grant the permission
to access the storage.

**Add the `keepassxc-cli` command**
```
pkg install keepassxc
```

# Usage example

Run `keepassxc-cli` (example 🔑 Spotify)

```
keepassxc-cli show -k "/path/to/passwords_key_file.keyx" -a Password -s "/path/to/passwords.kdbx" Spotify
```

