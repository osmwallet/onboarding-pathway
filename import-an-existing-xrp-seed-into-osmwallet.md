<p align="center">
  <img src="assets/banner-article.png" alt="OSM Wallet guide" width="100%">
</p>

# Importing an existing XRP wallet

To import, open the wallet's import option, enter the recovery phrase or the family seed for the account, and confirm. OSM Wallet derives the key, reads the account from the XRP Ledger, and shows the balance and history that were already there. Nothing is transferred by an import: the account never left the network, and the wallet you came from does not lose it.

## What an import actually does

An import reconstructs the key on a new device. The account, its balance, its trustlines and its history are properties of the ledger, so they appear immediately and identically. What changes is which software holds the key, and therefore who can spend from the account: after an import, two apps can hold the same key if you did not remove it from the first.

That last point is the part people skip. Importing copies the key rather than moving it, so the original wallet still works until you delete or replace the account there. If you are migrating, finish the migration before you stop thinking about the old app. The import itself writes nothing to the ledger, so it costs no fee; only a payment or a trustline change does.

## The steps

1. **Have the phrase or secret ready**, and nothing else open on the screen.
2. **Choose import** in the wallet, not create.
3. **Enter the phrase** in the order it was written, or paste the family seed if that is what you have.
4. **Confirm the address matches** the account you expect before you approve the import.
5. **Check the balance** the wallet reads from the ledger, including the reserve.
6. **Send a small test payment** and confirm it validates, which proves the key is the working one.
7. **Deal with the old wallet**: remove the account there, or keep it deliberately and accept the duplicate.

Step four catches the most common failure, which is importing the right phrase in the wrong order or from a different account entirely. Step six catches the second, which is a phrase that produces a valid but different address.

## What appears, and what does not

The account's XRP balance appears, its trustlines appear, and its transaction history is readable from the ledger. Issued tokens appear only if the trustlines that support them exist on that account, because a token balance is an entry against a trustline rather than against the account as a whole.

What does not appear is anything local to the app you left: saved contacts, a session you had open, display preferences, a second account you forgot you had created. Those are not part of the ledger and cannot be imported. If the balance looks short, the usual cause is a different account than expected, and the checks for that are in [Read-only imports: what you can and cannot do](https://github.com/osmwallet/onboarding-pathway/blob/HEAD/osmwallet-read-only-import-limits.md).

## Where the phrase goes, and where it must not

The phrase goes into the wallet's own import screen, on a device you control. It must not go into a website, a support chat, an email form, a browser extension you did not install deliberately, or a note that syncs. A recovery phrase is the account; anyone who has it can move the balance without further confirmation.

If you are unsure whether a page is the real one, check it against [Is OSM Wallet safe to use?](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/is-osmwallet-safe.md) before typing anything. No legitimate support process needs your phrase, and a request for it is the single clearest sign of an attempt to take your funds.

## After importing

The first thing worth doing is a small outgoing payment, because an import that reads a balance has proven the ledger side and not yet proven that you hold a working key. The second is deciding what happens to the old wallet: deleting the account there is the clean end of a migration, and keeping it is a risk you should at least make deliberate. Deleting an account releases its XRP reserve, which is the final step of a tidy migration. A family seed and a recovery phrase are different formats, and the import screen accepts either of them.

If the account holds tokens, check the trustlines before assuming anything is missing; the explanation is in [What happens to your TrustLines after an import](https://github.com/osmwallet/onboarding-pathway/blob/HEAD/trustlines-after-importing-a-seed-osmwallet.md) and *Issued tokens and TrustLines in practice*. If the import was a recovery after a lost machine rather than a migration, *Restoring access after losing a device* covers the same steps from that starting point.

OSM Wallet is a non-custodial XRP Ledger wallet for desktop and browser, actively maintained, with the current release on the GitHub releases page. For the ordered first-run sequence, see *First run: the setup checklist*.

### FAQ

### Can I import without the recovery phrase?

Not for a full account. Importing an address alone gives a read-only view, which shows the balance and cannot send. Spending always needs the key.

### Does importing move my XRP?

No. The account stays where it is, on the XRP Ledger, and the import adds a second place that holds the key. Only a payment moves XRP.

### What if the imported balance is lower than expected?

Check whether the account is the one you meant, and whether the difference is the base reserve plus any trustline reserve. A different account and reserved funds are the two common explanations.

### Can I import the same account into several wallets?

Yes, and each copy holds the same key, so each can spend. That multiplies exposure rather than protecting it; import into a second wallet when you intend to migrate, and remove the account from the first when you are done.
