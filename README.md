# blupr &nbsp; [![bluebuild build badge](https://github.com/visnudeva/blupr/actions/workflows/build.yml/badge.svg)](https://github.com/visnudeva/blupr/actions/workflows/build.yml)

**At the moment it is a work in progress. (alpha stage)**

I want to make a simple, riced but snappy Atomic/immutable Linux distro with Hyprland as a window manager, 
based on Ublue just like Wayblue but more eye candy because I was tired of having to install hyprland and rice it manually every time I wanted it on a pc.
I have been waiting for someone to build it but no one did, so I am trying without much knowledge but as it is based on Ublue I don't need to do all the upstream hard work and maintaining but just to tweak it to my liking, so here it is, it is mainly for own use, but anyone is also welcome to use it.

## Main Keybindings

<div align="left">

| Keys | Action |
| :--- | :--- |
| <kbd>Super</kbd> + <kbd>T</kbd> | kitty (terminal) |
| <kbd>Super</kbd> + <kbd>W</kbd> | firefox (web browser) |
| <kbd>Super</kbd> + <kbd>F</kbd> | thunar (file manager) |
| <kbd>Super</kbd> + <kbd>M</kbd> | rofi (menu) |
| <kbd>Super</kbd> + <kbd>Q</kbd> | quit a window |
| <kbd>Super</kbd> + <kbd>L</kbd> | lock the screen |
| <kbd>Super</kbd> + <kbd>E</kbd> | exit Hyprland |
| <kbd>Super</kbd> + <kbd>X</kbd> | fullscreen |

</div>

## Preinstalled Flatpacks

<div>

- firefox
- mpv
- localsend
- stremio
- telegram
- Warehouse
- Shortwave
- gapless
- deluge
- Geany

(The preinstalled flatpacks will be installed automatically during the first minutes after the first boot)
</div>


## Installation

> **Warning**  
> [This is an experimental feature](https://www.fedoraproject.org/wiki/Changes/OstreeNativeContainerStable), try at your own discretion.

To rebase an existing atomic Fedora installation to the latest build:

- First rebase to the unsigned image, to get the proper signing keys and policies installed:
  ```
  rpm-ostree rebase ostree-unverified-registry:ghcr.io/visnudeva/blupr:latest
  ```
- Reboot to complete the rebase:
  ```
  systemctl reboot
  ```
- Then rebase to the signed image, like so:
  ```
  rpm-ostree rebase ostree-image-signed:docker://ghcr.io/visnudeva/blupr:latest
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
cosign verify --key cosign.pub ghcr.io/visnudeva/blupr
```
