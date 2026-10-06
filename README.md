# debian-repo

Personal apt repository of `dev-jam`, served via GitHub Pages.

It contains:

* my own `devjam-*` packages, built from [`dev-jam/debian-packages`](https://github.com/dev-jam/debian-packages)
* a few third-party packages that are repackaged unmodified from their upstream `.deb` files (see below)

The repository is flat (no per-release suites) and only provides `amd64` and `all` packages.

## Add the repository

```sh
sudo apt-get update
sudo apt-get install -y ca-certificates curl

sudo install -m 0755 -d /usr/share/keyrings
sudo curl -fsSL -o /usr/share/keyrings/dev-jam.asc https://dev-jam.github.io/debian-repo/dev-jam.asc
sudo chmod a+r /usr/share/keyrings/dev-jam.asc

cat <<EOF | sudo tee /etc/apt/sources.list.d/dev-jam.sources
Types: deb
URIs: https://dev-jam.github.io/debian-repo/
Suites: ./
Signed-By: /usr/share/keyrings/dev-jam.asc
EOF

sudo apt-get update
```

Then install what you need, for example:

```sh
sudo apt-get install devjam-tools
```

## Remove the repository

```sh
sudo rm -f /etc/apt/sources.list.d/dev-jam.sources
sudo rm -f /usr/share/keyrings/dev-jam.asc
sudo apt-get update
```

Packages installed from this repository stay installed. Remove them separately with `apt-get remove`.

## Packages

### Own packages

All `devjam-*` packages, plus `apt-cleaner`, `brave-flags-wrapper` and `fclones-gui-launcher`. See the [package list](https://github.com/dev-jam/debian-packages#packages) for descriptions.

### Repackaged third-party packages

These are the upstream `.deb` files, not rebuilt. Copyright and licenses belong to the respective upstream projects.

`deadbeef-static`, `geteduroam-cli`, `geteduroam-gui`, `jan`, `modulejail`, `mx23-archive-keyring`, `mx25-archive-keyring`, `navidrome`, `nordvpn-release`, `oss-linux`, `phoronix-test-suite`, `pipeweaver`, `rescuezilla`, `systemd-manager-tui`, `yserver`
