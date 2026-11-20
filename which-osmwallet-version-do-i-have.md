<p align="center">
  <img src="assets/banner-article.png" alt="OSM Wallet guide" width="100%">
</p>

# Which version am I running?

Open the wallet's about or settings panel and read the version string it shows, then compare it with the current release listed on the project's releases page. If the two differ, install the current release. That comparison, not the number itself, is the useful answer, because what matters is whether you are behind.

## Where the version lives in the app

Desktop wallets put the version in an about panel, a settings page or the window's title area, and the browser extension shows it on its own details screen. OSM Wallet follows that pattern: the app reports its own version internally, and that is the number to compare rather than a number remembered from a download page.

If you cannot find it, the reliable fallback is to reinstall from the releases page: the build you end up with is the current one, and the account is unaffected because the key is not stored in the application binary.

## Why the number alone does not answer the question

A version string is only meaningful against a reference. Without the releases page, the number on its own answers nothing: it may be current, three releases behind, or a build from a fork. The reference is the project's own release list, which is why every comparison starts there rather than with a memory of what was downloaded.

There is a second reason to check rather than assume: an installer saved months ago and reused is the most common way people end up running an old build while believing they are current.

## How to compare, in order

1. Read the version the app reports.
2. Open the project's releases page and read the most recent release.
3. If they match, you are current and there is nothing to do.
4. If the app is older, install the current release over it; the account and keys are unaffected.
5. If the app is somehow newer than the published release, you are running a build that is not from the official release list, and you should replace it.

Step five is worth taking seriously. A build that claims a version ahead of the official list did not come from the official list, and an unofficial build of a wallet is a wallet whose behaviour you cannot verify.

## What updating does and does not touch

Updating replaces the application. It does not touch the account, because the account is on the XRP Ledger and the key is stored by the wallet's data, not by the executable. An update that appeared to wipe an account usually replaced the wallet's stored data as well, which is a different operation from installing a new build.

That distinction is why the recovery phrase matters even during an update: it is what turns a bad update, a corrupted profile or a reinstalled system into lost time rather than lost funds.

## When the version explains the problem

Most "the guide does not match my screen" reports are a version difference. A feature described in current documentation may not exist in a build from a year ago, and a screen that seems to be missing an option is often simply older than the article describing it.

The reverse also happens: a wallet that behaves oddly after an update is usually a build that did not install cleanly, and reinstalling the current release from the official page resolves it more often than any setting does.

When the symptom is a zero balance, [Why the wallet shows zero available XRP](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/why-osmwallet-shows-zero-available-xrp.md) covers the common causes.

## Why this matters beyond curiosity

Knowing your version is the first diagnostic step for everything else. It decides whether a documented fix applies, whether a security fix is present, and whether a bug report is about the current code at all. It also protects you from the most common social-engineering angle in this space: a message claiming you must install a specific update to keep access, which is an attempt to get you to run something that is not the official release.

The rule is simple. Updates come from the releases page, and nobody needs to send you one.

OSM Wallet is a non-custodial XRP Ledger wallet for desktop and browser, actively maintained, with the current release published on its GitHub releases page.

For the update procedure itself, the prudent path is a fresh install of the current release over the existing one; the account survives because the key is not in the binary. If the version question came up because something is broken, [Sending your full XRP balance](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/send-max-xrp-balance-osmwallet.md) covers the most common symptom and [Is OSM Wallet safe to use?](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/is-osmwallet-safe.md) covers the impersonation angle, and *First run: the setup checklist* is the reference for what a current first run looks like, and *Setting up an XRP wallet from zero* covers a clean install from zero.

### FAQ

### Where do I find the version in OSM Wallet?

In the app's about or settings panel, and in the browser extension's details screen. If it is not visible, reinstalling the current release from the official page gives you the current build without touching the account.

### Does updating lose my funds?

No. The account is on the XRP Ledger and the key is not in the executable, so replacing the application does not move or delete anything. Keep the recovery phrase anyway; it is what makes a failed update cost time instead of funds.

### How often should I update?

Whenever a new release is published, and before troubleshooting anything. Running the current release means a guide describes your build, which is the difference between a five-minute fix and an hour of guessing.

### Someone messaged me an update file. Should I install it?

No. Updates come from the releases page, and a file sent by message is not that. This is one of the most common ways wallet users are targeted.
