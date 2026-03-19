# opn-plugins

Custom OPNsense plugins built and published as a signed FreeBSD pkg repository.

## Available Plugins

| Plugin | Description |
|--------|-------------|
| `os-blocky` | [Blocky](https://github.com/0xERR0R/blocky) DNS proxy and ad-blocker integration |

## Installation

### 1. Add the repository public key

Download `repo.pub` from this repository to your OPNsense box:

```sh
fetch -o /usr/local/etc/pkg/repos/jokajak-opn-plugins.pub \
  https://jokajak.github.io/opn-plugins/repo.pub
```

### 2. Add the repository configuration

Create `/usr/local/etc/pkg/repos/jokajak-opn-plugins.conf`:

```ucl
jokajak-opn-plugins: {
  url: "https://jokajak.github.io/opn-plugins/FreeBSD:14:amd64",
  signature_type: "pubkey",
  pubkey: "/usr/local/etc/pkg/repos/jokajak-opn-plugins.pub",
  enabled: yes
}
```

### 3. Install a plugin

```sh
pkg update
pkg install os-blocky
```

## Repository Structure

```
FreeBSD:14:amd64/   # Signed pkg repository index and packages
repo.pub            # RSA public key for verifying package signatures
```
