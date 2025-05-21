**ALPHA**
<p align="center">
  <a href="https://github.com/visnudeva/bluiri">
    <img src="https://github.com/visnudeva/blupr/blob/main/bluiri1.png" width=200 />
  </a>
</p>

# bluiri (blurry) &nbsp; [![bluebuild build badge](https://github.com/visnudeva/blupr/actions/workflows/build.yml/badge.svg)](https://github.com/visnudeva/blupr/actions/workflows/build.yml)

AT THE MOMENT I CAN'T FIGURE A WAY TO GET THE CONFIG FILES COPIED TO THE INSTALLATION SO I AM USING MY DOTFILES INSTEAD
i'm just going to make an install script...

A work in progress of a simple riced Atomic Linux distro with Niri as a window manager which can make older computers fast and snappy with its low CPU and RAM usage but also modern and beautiful.
Based on Universal Blue and focused on niri because this window manager really deserves its own functional and themed distro out of the box.

It is mainly for personal use, but anyone is also welcome to use it.

At the first login (gdm) choose niri as a the desktop environment otherwise it will boot on Gnome which is also functional.

## Main Keybindings (US Keyboard)

<div align="left">

| Keys | Action |
| :--- | :--- |
| <kbd>Super</kbd> + <kbd>T</kbd> | kitty (terminal) |
| <kbd>Super</kbd> + <kbd>I</kbd> | geany (IDE) |
| <kbd>Super</kbd> + <kbd>W</kbd> | firefox (web browser) |
| <kbd>Super</kbd> + <kbd>F</kbd> | thunar (file manager) |
| <kbd>Super</kbd> + <kbd>M</kbd> | fuzzel (menu) |
| <kbd>Super</kbd> + <kbd>Q</kbd> | quit a window |
| <kbd>Super</kbd> + <kbd>X</kbd> | expand window |
| <kbd>Super</kbd> + <kbd>L</kbd> | hyprlock (lock) |

</div>

## Preinstalled Flatpaks

<div>

Web
- Firefox
- Transmission
- Telegram

Media
- VLC
- Musicpod
- Stremio
- Bottles

Productivity
- Onlyoffice
- Zed
  
Utilities
- Qview
- Localsend
- Warehouse
  
(The preinstalled flatpaks will be installed automatically during the first minutes after the first boot)
</div>


## Installation

> **Warning**  
> [This is an experimental feature](https://www.fedoraproject.org/wiki/Changes/OstreeNativeContainerStable), try at your own discretion.

To rebase an existing atomic Fedora installation to the latest build:

- First rebase to the unsigned image, to get the proper signing keys and policies installed:
  ```
  rpm-ostree rebase ostree-unverified-registry:ghcr.io/visnudeva/bluiri:latest
  ```
- Reboot to complete the rebase:
  ```
  systemctl reboot
  ```
- Then rebase to the signed image, like so:
  ```
  rpm-ostree rebase ostree-image-signed:docker://ghcr.io/visnudeva/bluiri:latest
  ```
- Reboot again to complete the installation
  ```
  systemctl reboot
  ```

The `latest` tag will automatically point to the latest build. That build will still always use the Fedora version specified in `recipe.yml`, so you won't get accidentally updated to the next major version.

## ISO

If build on Fedora Atomic, you can generate an offline ISO with the instructions available [here](https://blue-build.org/learn/universal-blue/#fresh-install-from-an-iso). These ISOs cannot unfortunately be distributed on GitHub for free due to large sizes, so for public projects something else has to be used for hosting.

## Verification

These images are signed with [Sigstore](https://www.sigstore.dev/)'s [cosign](https://github.com/sigstore/cosign). You can verify the signature by downloading the `cosign.pub` file from this repo and running the following command:

```bash
cosign verify --key cosign.pub ghcr.io/visnudeva/bluiri
```
