# base

[![build-ublue](https://github.com/graybush/ublue-base/actions/workflows/build.yml/badge.svg)](https://github.com/graybush/ublue-base/actions/workflows/build.yml)

A base image with a (mostly) stock Fedora Silverblue. Help us make a sweet base image: Pull requests and improvements appreciated and encouraged!

## Usage

Warning: This is an experimental feature and should not be used in production, try it in a VM for a while, you have been warned!

    sudo rpm-ostree rebase --experimental ostree-unverified-registry:ghcr.io/graybush/ublue-base:latest

We build date tags as well, so if you want to rebase to a particular day's release:

    sudo rpm-ostree rebase --experimental ostree-unverified-registry:ghcr.io/graybush/ublue-base:20221217

The `latest` tag will automatically point to the latest build.

## Features

- Start with a base Fedora Silverblue 37 image
- Removes Firefox from the base image
- Adds the following packages to the base image:
  - distrobox and gnome-tweaks
- Sets automatic staging of updates for the system
- Sets flatpaks to update twice a day
- Everything else (desktop, artwork, etc) remains stock so you can use this as a good starting image

## Applications

- All applications installed per user instead of system wide, similar to openSUSE MicroOS, they are not on the base image. Thanks for the inspiration Team Green!
- Mozilla Firefox, Evolution, Extension Manager, Libreoffice, DejaDup, FontDownloader, Flatseal, and the VLC Media Player
- Core GNOME Applications installed from Flathub
  - GNOME Calculator, Calendar, Characters, Connections, Contacts, Evince, Firmware, Logs, Maps, NautilusPreviewer, TextEditor, Weather, baobab, clocks, eog, and font-viewer

## Verification

These images are signed with sisgstore's [cosign](https://docs.sigstore.dev/cosign/overview/). You can verify the signature by downloading the `cosign.pub` key from this repo and running the following command:

    cosign verify --key cosign.pub ghcr.io/graybush/ublue-base
