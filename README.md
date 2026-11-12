# Sotto releases

Signed downloads of **Sotto**, a private, end-to-end encrypted workspace for teams: messages, groups, channels and calls with no phone numbers or emails, an anonymous inbox, and sandboxed review of every file you receive.

Get the latest version from [Releases](https://github.com/codewic/sotto-releases/releases/latest):

- `Sotto-<version>-x86_64.AppImage`: runs on most Linux systems. Make it executable and open it.
- `Sotto-<version>-amd64.deb`: for Debian and Ubuntu.
- `sotto-tools-<version>-x86_64.tar.gz`: the `sotto-hook` command for posting from scripts and CI.

Once installed, Sotto updates itself.

## Every release is signed

Each release has a `latest.json` listing every file with its SHA-256 and size, and `latest.json.sig`, an Ed25519 signature over it made with the Sotto release key. That key stays offline with its owner and never touches CI or GitHub, so neither can publish an update the app will install.

The app checks the signature and each file's fingerprint before installing anything, and never installs an older version than it runs.

Release key (Ed25519 public key, hex):

```
7f1ed181be7057fd7cc171dadafff768aeda09c5f7ddbba2839e21a65f518a3d
```

To check a download yourself, compare its SHA-256 (`sha256sum <file>`) with the one in `latest.json`. To check `latest.json` itself, use `sotto-release verify latest.json latest.json.sig` from the Sotto source, which uses the same pinned key.

## Privacy of update checks

Sotto checks for updates by downloading the same public `latest.json` everyone downloads, with no identifiers or version number, about every 6 hours at random times. When Sotto uses Tor, so do update checks. In Extreme mode it checks only when you ask.
