![.github/workflows/build.yml](https://github.com/zhangyoufu/alpine/workflows/.github/workflows/build.yml/badge.svg)

# Introduction

Build alpine packages for {v3.9, v3.10, v3.11, v3.12, edge} × {amd64, i386, arm64v8, arm32v6, arm32v7, ppc64le, s390x}, and deploy to GitHub Pages.

Currently provides a modified version of iptables which does not require CAP_NET_RAW.

Builds for architectures other than amd64/i386 is SLOW, [qemu-user-static](https://github.com/multiarch/qemu-user-static) saves me from setting up cross-compile toolchain/rootfs.

# Usage

* add public key
  ```
  wget -P /etc/apk/keys https://zhangyoufu.github.io/alpine/zhangyoufu.rsa.pub
  ```
* add tagged repository
  ```
  (. /etc/os-release; echo "@zhangyoufu https://zhangyoufu.github.io/alpine/${PRETTY_NAME##* }/main" >>/etc/apk/repositories)
  ```
* install package
  ```
  apk add iptables@zhangyoufu
  ```

# Repository secrets

* PRIVATE_KEY: signing key in PEM format
* GITHUB_PERSONAL_ACCESS_TOKEN: trigger GitHub Pages build

---
Powered by GitHub Actions
