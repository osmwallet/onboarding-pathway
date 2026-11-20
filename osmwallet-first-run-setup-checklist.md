<p align="center">
  <img src="assets/banner-article.png" alt="OSM Wallet guide" width="100%">
</p>

# First run: the setup checklist

The first run is short if the order is right: create the account, write the recovery phrase down before any XRP arrives, confirm the balance, and only then import anything you already own. OSM Wallet walks through that order because an account funded before its backup is tested is one accident away from being unrecoverable. The first run is about the backup, and the balance can wait until that is done.

## The checklist

1. **Install and open the wallet.** On Windows, macOS or Linux, from the official release.
2. **Choose create, not import**, if this is your first XRP account.
3. **Write the recovery phrase on paper** as it is shown, in order, and confirm it in the app.
4. **Check the restore before you fund.** If the app offers a verification step, complete it; a phrase you have not read back is a phrase you have not tested.
5. **Fund the account past the base reserve.** An account needs a base reserve before it can exist and hold a spendable balance.
6. **Confirm the balance appears** in the wallet, not only on the sending side.
7. **Send a small test payment out**, to prove the key works, before you move a larger balance in.
8. **Only now import an existing account**, if you have one, as a second step rather than a first.

Steps five to seven are where new users lose time. A freshly created account with no funds shows nothing, and a first deposit that lands exactly at the reserve shows a balance with nothing available to send. Both are the ledger behaving normally.

## Why the backup comes first

A recovery phrase is the only thing that can reconstruct the key. If the phrase is written after the account is funded, there is a window where a crash, a lost laptop or a wiped drive costs the funds. Doing it first costs a minute; doing it later costs the balance in the worst case.

Write it on paper, in order, and store it somewhere that is not the same bag, drawer or house as the device. Photographs, cloud notes and browser password managers all put the phrase within reach of exactly the malware self-custody is meant to avoid.

## What you do not need on the first run

You do not need to import a seed, add a trustline, enable a second account or configure a testnet on day one. Each of those is a separate decision with its own failure mode, and doing them before the basic account works makes it harder to tell which step broke.

You also do not need to move your whole balance in. A wallet is proven by a small, round trip - in, then out - and only then is it worth trusting with anything meaningful. The sending side of that test is covered in [Sending your full XRP balance](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/send-max-xrp-balance-osmwallet.md), and the reserve arithmetic in [The XRP reserve, explained without the confusion](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/xrp-reserve-explained-osmwallet.md).

## What the app looks like afterwards

OSM Wallet is a non-custodial XRP Ledger wallet: a desktop app for Windows, macOS and Linux, plus a browser extension. After the first run you have one account with its address, its balance and its reserve shown, and the same account is visible from either surface if you open it in both.

It is actively maintained, and the current release is downloaded from the GitHub releases page. Running an older build is the most common reason a screen does not match a guide, so check that before troubleshooting anything.

## When the first run goes wrong

The three failures worth knowing before they happen: the phrase was written incorrectly, so a later restore opens a different empty account; the first deposit was below the reserve, so the account never becomes usable; or the deposit went to a different address than the one the wallet shows, which is usually a copy-paste error.

Each has a check. Read the phrase back to yourself against the screen before confirming; fund above the reserve rather than exactly at it; copy the address from the wallet's own receive screen and verify both ends after pasting.

For the longer version of this sequence, see [Setting up an XRP wallet from zero](https://github.com/osmwallet/onboarding-pathway/blob/HEAD/how-to-set-up-an-xrp-wallet-osmwallet.md). For bringing in a wallet you already own, *Importing an existing XRP wallet*; for the storage model behind the phrase, *Protecting a seed phrase you cannot reset*; and for what to do if a restore lands on an empty account, *Restoring access after losing a device*.

### FAQ

### Do I have to fund the wallet immediately?

No. You can create the account, back it up and leave it empty until you need it. The account only exists on the ledger once it has been funded, so an empty wallet is a key waiting for a first deposit.

### Can I skip the recovery phrase step?

Not safely. The wallet asks for it because a non-custodial account has no other recovery path. Skipping it means the account cannot be restored by anyone, including the developers.

### Should I import my old wallet first or create a new one?

Create the new account first if you are new to self-custody, so the practice run happens before real funds are involved. Import when you already have an account you want to keep using.

### Why does my new account show a balance but nothing available to send?

Because the base reserve is part of the balance and cannot be spent while the account exists. A deposit at or just above the reserve activates the account and leaves little or nothing sendable.
