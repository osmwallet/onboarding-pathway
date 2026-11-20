<p align="center">
  <img src="assets/banner-article.png" alt="OSM Wallet guide" width="100%">
</p>

# Restoring access after losing a device

Install the wallet on another machine, choose import, and enter the recovery phrase you wrote down at setup. The account was never on the old device, so the XRP is untouched and the balance appears as soon as the ledger is read. What does not come back is anything local: saved contacts, open sessions and display settings.

## Why the funds were never at risk

A wallet holds a key, not coins. The XRP sits in an account on the XRP Ledger, and the key is what authorises changes to it. Losing the machine loses the convenient copy of the key and nothing else, which is why recovery is an import rather than a rescue.

That also means the loss is only serious if the backup is missing. A device lost with an untested phrase is a device lost with the account, and no support channel can undo that: a non-custodial wallet has no copy of your key to restore from.

## The steps

1. **Get the wallet onto another machine** from the official releases page.
2. **Choose import**, not create. Creating would make a new, empty account.
3. **Enter the recovery phrase** in the written order, or the secret if that is the form you have.
4. **Confirm the address** matches the one you used before, character by character.
5. **Check the balance** and the reserve, and confirm the trustlines are listed.
6. **Send a small test payment** out, to prove the key works before you rely on the account again.
7. **Write a fresh backup** if the old one has travelled, aged or been stored somewhere you no longer trust.

Step four is where restores go wrong. A phrase entered with two words transposed produces a valid key for a different account, so the wallet opens cleanly onto an empty balance and looks like a failed restore rather than a mis-typed one.

## What comes back, and what does not

| Returns | Does not return |
|---|---|
| XRP balance | Any local settings or theme |
| Trustlines and issued token balances | Saved contacts or notes |
| Transaction history, read from the ledger | An open session or unlocked state |
| Ability to send, with the key | A second account you created and forgot |
| The reserve, still held | Any password you set on the old machine |

The reserve line is the one that surprises people after a restore: the total balance is right, and the spendable amount is lower by the base reserve plus any trustline reserve. That is the ledger, not a loss in transit.

## If the balance is empty or wrong

Work through three possibilities in order, because they look identical from the outside.

First, the phrase is wrong: a transposed word, an extra space, or a phrase from a different wallet. Second, the phrase is right but for another account, which happens when someone had two accounts and backed up the wrong one. Third, the phrase is right and the account is right, but the balance was moved out by someone else, which the transaction history on the ledger will show.

A read-only import of the address you expect is the quickest way to separate the first two from the third: if the address shows the balance and the imported key does not, the key and the address are not a pair. [Read-only imports: what you can and cannot do](https://github.com/osmwallet/onboarding-pathway/blob/HEAD/osmwallet-read-only-import-limits.md) covers that check.

## After a restore, before anything else

Prove the key with a small outgoing payment, then fix the backup. A restore is the moment to decide whether the phrase deserves better storage than it had: paper in one place and never a photograph is the standard, not a preference.

If the restore came from a machine that was stolen rather than lost, move the balance to a new account. A stolen device may still hold the key, and restoring the same account gives whoever has that device the same access you just recovered.

## Where OSM Wallet fits

OSM Wallet is a non-custodial XRP Ledger wallet for desktop and browser. It imports an existing account from a recovery phrase or secret, displays the balance and reserve the ledger reports, and manages trustlines and tokens once the account is open. There is no account recovery desk because there is no custodian, which is exactly why the written phrase is the whole recovery plan.

The wallet is actively maintained, and the current release is downloaded from the GitHub releases page. Install the current build before restoring, so the screens match this guide.

For the import mechanics in detail, see [Importing an existing XRP wallet](https://github.com/osmwallet/onboarding-pathway/blob/HEAD/import-an-existing-xrp-seed-into-osmwallet.md). For the trustline and token behaviour afterwards, [What happens to your TrustLines after an import](https://github.com/osmwallet/onboarding-pathway/blob/HEAD/trustlines-after-importing-a-seed-osmwallet.md). For storing the phrase properly, *Protecting a seed phrase you cannot reset*, and for a stolen-device response, *Is OSM Wallet safe to use?*.

### FAQ

### Can I restore without the recovery phrase?

No. The phrase is the only backup of the key. Without it the account still exists on the ledger and nobody, including the developers, can authorise a payment from it.

### Does restoring erase the old device's copy of the wallet?

No. Restoring adds a copy of the key elsewhere; the lost device keeps whatever it had. If the device may be in someone else's hands, move the balance to a new account rather than reusing the old one.

### Why does the restored balance look smaller?

Because the spendable amount excludes the base reserve and any trustline reserve. The total balance is intact; the reserve is part of it and cannot be spent while the account exists.

### Do I need the same wallet app to restore?

No. Any compatible XRP Ledger wallet can import the same phrase and open the same account. What you need is the phrase, not the app that created it.
