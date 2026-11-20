<p align="center">
  <img src="assets/banner-article.png" alt="OSM Wallet guide" width="100%">
</p>

# Read-only imports: what you can and cannot do

A read-only import loads an address without its key, so the wallet can show the account's balance, history and trustlines, and cannot sign anything. It is the right tool for watching an account you do not control, and the wrong tool for moving funds. If you need to send, the import has to include the recovery phrase or secret.

## What "read only" means mechanically

Signing a transaction requires the private key. An address is a public identifier derived from that key, so from the address alone a wallet can ask the ledger what the account holds, but it cannot produce a signature the ledger will accept. A read-only import is therefore a viewer: accurate, useful, and incapable of spending.

That is a feature rather than a limitation for two cases. Watching an account whose key lives elsewhere, such as a hardware device or a long-term cold account, lets you monitor it from the machine you use daily without putting the key on that machine. Checking whether an address you were given is funded and active is the other case.

For the full import path, see [Importing an existing XRP wallet](https://github.com/osmwallet/onboarding-pathway/blob/HEAD/import-an-existing-xrp-seed-into-osmwallet.md).

## The two imports, side by side

| | Read-only import | Full import |
|---|---|---|
| What you provide | The address | Recovery phrase or secret |
| Shows balance and history | Yes | Yes |
| Shows trustlines and tokens | Yes, as the ledger reports them | Yes |
| Can send XRP | No | Yes |
| Can create or remove a trustline | No | Yes |
| Key on this machine | No | Yes |
| Right for | Watching, verifying, monitoring | Daily use, migration, recovery |

The line that matters is the fifth. Anything that changes the account's state is a transaction, and every transaction needs a signature, so a read-only account is outside the wallet's ability to fix things as well as its ability to spend.

## When read-only is the right choice

Use it when the key deliberately lives somewhere else. A cold-storage account is the clearest example: you want to see the balance without turning the viewing machine into a second copy of the key. A merchant's receiving address is another: you can confirm payments arrived without holding anyone's secret.

Use it also as a diagnostic. If you are unsure whether an address belongs to the account you think it does, importing it read-only answers that question without exposing a key. A balance that appears under read-only and disappears under a full import means the two are not the same account.

## When read-only is the wrong choice

It is the wrong tool whenever you intend to transact: sending, adding a trustline, removing one, setting a regular key, deleting the account to recover the reserve. Each of those is a state change and each needs the key. People hit this after a botched migration, when the "import" they performed did not actually include the secret.

It is also the wrong way to test whether a phrase is correct. A read-only import accepts an address and tells you the account exists, which feels like confirmation without proving you hold the key. The only proof is a signed transaction, and the cheapest one is a small payment.

## How to tell which one you did

The wallet shows it plainly: a read-only account is marked as such, and the send controls are unavailable rather than failing after you fill them in. If send is greyed out, the import did not include a key, and no amount of re-entering the address will change that.

If you are not sure whether the account you imported is the right one, compare its address character by character with the source you trust, then check whether the balance matches what you expected before the reserve is taken into account. Those two checks separate "wrong account" from "right account, reserved funds".

## Where OSM Wallet fits

OSM Wallet is a non-custodial XRP Ledger wallet for desktop and browser that supports importing an existing account and, separately, importing an address for viewing. It shows the balance the ledger reports along with the reserve, so a read-only view is honest about what is spendable by someone who does hold the key.

It is actively maintained, and the current release is downloaded from the GitHub releases page; a guide written for the current build may not match an older one.

For the trustlines that still belong to the account even when you can only watch it, [What happens to your TrustLines after an import](https://github.com/osmwallet/onboarding-pathway/blob/HEAD/trustlines-after-importing-a-seed-osmwallet.md). For recovering access after losing a machine, [Restoring access after losing a device](https://github.com/osmwallet/onboarding-pathway/blob/HEAD/restoring-osmwallet-after-losing-a-device.md), and for the custody model behind the distinction, *What a non-custodial wallet actually means*, and for verifying that an address is the account you expect, *Is OSM Wallet safe to use?*.

### FAQ

### Can I send XRP from a read-only import?

No. Sending needs a signature and a signature needs the key. A read-only account can show everything the ledger records and change none of it.

### Why would I import an address instead of the phrase?

To watch an account whose key lives elsewhere, or to verify that an address is the account you think it is. Both are safer than putting a key on a machine that does not need it.

### Does a read-only import show tokens?

It shows what the ledger reports for that account, including trustlines and their balances. It cannot add or remove a trustline, because that is a transaction.

### Is a read-only import safe?

It is safer than a full import on an untrusted machine, because no key is present. The address is public anyway; what a read-only view adds is convenience, not exposure.
