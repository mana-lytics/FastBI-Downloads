# FastBI

Downloadable packages for **FastBI v.0.1**, and the metadata needed to verify
them. This repository contains **no application source code** — it exists so the
packages can be downloaded without access to the development repository.

FastBI is a local analytics application. It runs on your machine, serves a web
interface at `http://127.0.0.1`, and reads only the files you give it. There is
no account, no cloud upload and no telemetry. Analysis, charts, HTML and
PowerPoint export are deterministic and work with no AI key; a key only adds
written narrative.

## Downloads

Get them from the [v0.1.0 release](../../releases/tag/v0.1.0).

| Your machine | File |
|---|---|
| Mac, Apple silicon (M1–M4) | `FastBI-v.0.1-macos-arm64.zip` |
| Mac, Intel | `FastBI-v.0.1-macos-x64.zip` |
| Linux, 64-bit | `FastBI-v.0.1-linux-x64.tar.gz` |

Not sure which Mac you have: **Apple menu → About This Mac**. "Apple M…" means
arm64; "Intel" means x64.

## Platform support and verification status

- **macOS arm64: native-tested**
- **macOS Intel x64: verified under Rosetta 2**
- **Linux x64: verified under QEMU**
- **Windows: no package in v.0.1**

**No Windows package in v.0.1.**

Every package was built and checked on the maintainer's own hardware. Each one
passed a 22-check verification run with the build toolchain removed — it
analyses a CSV, exports PowerPoint and HTML, joins tables, saves and reopens a
dashboard byte-identically, and makes no outbound network connection — and a
browser gate in which a real Chromium drives the packaged application through
save, reload and reopen.

The macOS Intel and Linux packages were verified under emulation (Rosetta 2 and
QEMU respectively) rather than on native hardware. Real x86_64 code executed and
passed every check, but if you are on an Intel Mac or an x86_64 Linux machine,
you are among the first to run these on physical silicon.

This is an **early prerelease**. Expect defects.

## Verify what you downloaded

`SHA256SUMS.txt` is attached to the release. Put it beside the archive and run:

```bash
shasum -a 256 -c SHA256SUMS.txt --ignore-missing    # macOS
sha256sum   -c SHA256SUMS.txt --ignore-missing      # Linux
```

You want `OK`. Anything else — stop, delete the file, download again.

`release_manifest.json` and the per-package manifests record the platform,
interpreter, file count and unpacked size of each package.

## Signing

The packages are **not code-signed or notarised**, so macOS will warn you the
first time you open one. `RUNNING_AN_UNSIGNED_BUILD.md` ships inside every
package with the full instructions. The short version:

- **macOS** — unzip, then **right-click** `FastBI-macOS.command` → **Open** →
  **Open**. Right-click the first time; double-clicking is what triggers the
  Gatekeeper block. If it still refuses: **System Settings → Privacy &
  Security → Open Anyway**.
- **Linux** — no equivalent warning. If the launcher will not start,
  `chmod +x FastBI-Linux.sh fastbi`.

## Where your data lives

Everything stays inside the folder you unpack. Deleting that folder removes the
application completely — no services, no registry keys, no login items.
