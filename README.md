# kaminari-os &nbsp; [![bluebuild build badge](https://github.com/thund3rpat/kaminari-os/actions/workflows/build.yml/badge.svg)](https://github.com/thund3rpat/kaminari-os/actions/workflows/build.yml)

Kaminari (japanese for "thunder") is a customized version of Bluefin that comes pre-configured with essential tools for daily driving. 
It builds on the core strengths of Fedora Silverblue, adding a unique layer of customization to deliver a lightning-fast, streamlined, and modern immutable desktop.

Kaminari is built using BlueBuild - a set of tools and documentation for creating custom images of image-based Linux distributions.

## Installation

> **Warning**  
> [This is an experimental feature](https://www.fedoraproject.org/wiki/Changes/OstreeNativeContainerStable), try at your own discretion.

To rebase an existing atomic Fedora installation to the latest build:

- First rebase to the unsigned image, to get the proper signing keys and policies installed:
  ```
  rpm-ostree rebase ostree-unverified-registry:ghcr.io/thund3rpat/kaminari-os:latest
  ```
- Reboot to complete the rebase:
  ```
  systemctl reboot
  ```
- Then rebase to the signed image, like so:
  ```
  rpm-ostree rebase ostree-image-signed:docker://ghcr.io/thund3rpat/kaminari-os:latest
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
cosign verify --key cosign.pub ghcr.io/thund3rpat/kaminari-os
```
