# PassWall2 APK repository

Rebuilt mirror of [Openwrt-Passwall/openwrt-passwall2](https://github.com/Openwrt-Passwall/openwrt-passwall2) **26.4.20-1**,
signed as OpenWrt 25.12 APK feeds. Check for upstream updates every 4 hours.

## Online feed (recommended)

Pick the URL matching your router's architecture; register the **full packages.adb URL**
explicitly to avoid apk's legacy `APKINDEX.tar.gz` fallback warning:

| Arch | Feed URL |
|---|---|
| `x86_64` | `https://huruojin.github.io/build-passwall2-repo/x86_64/packages.adb` |
| `aarch64_cortex-a53` | `https://huruojin.github.io/build-passwall2-repo/aarch64_cortex-a53/packages.adb` |
| `aarch64_generic` | `https://huruojin.github.io/build-passwall2-repo/aarch64_generic/packages.adb` |

```sh
# 1. Trust this repo's signing key (one time)
wget -O /etc/apk/keys/passwall2-repo.rsa.pub \
    https://huruojin.github.io/build-passwall2-repo/passwall2-repo.rsa.pub

# 2. Register the feed (replace <arch>)
echo "https://huruojin.github.io/build-passwall2-repo/<arch>/packages.adb" >> /etc/apk/repositories.d/customfeeds.list

# 3. Install
apk update
apk add luci-app-passwall2
apk add luci-i18n-passwall2-zh-cn
/etc/init.d/rpcd restart
```

## Offline snapshot

Per-arch zip archives on the [`26.4.20-1`](https://github.com/huruojin/build-passwall2-repo/releases/tag/26.4.20-1) release:

- [passwall2-x86_64-26.4.20-1.zip](https://github.com/huruojin/build-passwall2-repo/releases/download/26.4.20-1/passwall2-x86_64-26.4.20-1.zip)
- [passwall2-aarch64_cortex-a53-26.4.20-1.zip](https://github.com/huruojin/build-passwall2-repo/releases/download/26.4.20-1/passwall2-aarch64_cortex-a53-26.4.20-1.zip)
- [passwall2-aarch64_generic-26.4.20-1.zip](https://github.com/huruojin/build-passwall2-repo/releases/download/26.4.20-1/passwall2-aarch64_generic-26.4.20-1.zip)

Extract, put the directory somewhere webserver-reachable, and point apk at its `packages.adb`.
