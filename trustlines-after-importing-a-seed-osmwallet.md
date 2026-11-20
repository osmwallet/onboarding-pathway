<p align="center">
  <img src="assets/banner-article.png" alt="OSM Wallet guide" width="100%">
</p>

# What happens to your TrustLines after an import

Trustlines belong to the account on the XRP Ledger, not to the app you used. Import the same seed elsewhere and the trustlines come with the account, along with the tokens they hold and the reserve they require. If the tokens look missing after an import, the cause is almost always a different account or a view that has not loaded yet, not trustlines left behind.

## Why trustlines travel with the account

A trustline is a ledger entry: it records that a particular account accepts a particular issuer's asset, up to a limit. That entry sits on the ledger next to the account's XRP balance, so any wallet that opens the account sees it. Nothing about it is stored locally, and nothing about it depends on the software.

The practical consequence is reassuring and occasionally confusing. Reassuring, because a migration does not require re-adding a dozen trustlines. Confusing, because a fresh account created instead of imported starts with none, and the difference between those two operations is one menu choice made weeks earlier.

For the import itself, see [Importing an existing XRP wallet](https://github.com/osmwallet/onboarding-pathway/blob/HEAD/import-an-existing-xrp-seed-into-osmwallet.md).

## What an import brings, and what it does not

| Item | Comes with the account | Notes |
|---|---|---|
| Trustlines | Yes | Created and owned on the ledger |
| Token balances | Yes, through their trustlines | A token with no trustline cannot show |
| Reserve held for trustlines | Yes | Each trustline adds to the reserve requirement |
| Limit settings per trustline | Yes | They are part of the ledger entry |
| Local app preferences | No | Contacts, theme, saved sessions |
| A deactivated trustline | It stays deactivated | Reactivating is a transaction |

The last two rows explain the two questions that follow an import. Why the balance looks short: the reserve. Why a token is missing: either its trustline does not exist on this account, or it exists with a zero balance because nothing was ever received.

## The reserve question

Every trustline adds a reserve requirement to the account. An account with five trustlines therefore needs more XRP held back than an account with none, and an import that brings trustlines also brings that requirement. The requirement is the same per trustline whatever the token is worth, so a cheap token reserves as much as an expensive one. A wallet showing a lower spendable balance than the user expected is usually showing exactly this.

That is also why importing an account with many trustlines into an account that is nearly empty can leave nothing spendable: the reserve obligations arrive with the trustlines, and the XRP to cover them did not.

## If a token is missing after the import

Work in this order, because each step rules out one cause.

1. Confirm the address is the account you meant, character by character.
2. Confirm the trustline exists on that account, as listed by the wallet or a ledger explorer.
3. Confirm the token balance is above zero, since a trustline can exist with nothing received.
4. Confirm the issuer matches the token you expect, because two issuers can share a ticker.
5. If the trustline is genuinely absent, the account you imported is not the one that held the token.

Step four is the one people miss. A token's identity is its issuer and currency code together, so a trustline to a different issuer holds a different asset with the same name.

## Adding a trustline after an import

If you need a trustline that is genuinely missing, adding it is a transaction: it needs the key, it costs a fee, and it increases the reserve requirement. Do it deliberately, and check the issuer before you confirm, because a trustline to the wrong issuer is a trustline to a different asset.

Removing one is also a transaction, and the reserve is released only when the token balance on it is zero. That ordering trips people up when they are trying to recover reserve from an old account: tokens first, then the trustline.

## Where OSM Wallet fits

OSM Wallet is a non-custodial XRP Ledger wallet for desktop and browser that manages trustlines alongside XRP transfers, showing the reserve implications as part of the account. It imports an existing account from a recovery phrase or secret, so trustlines and tokens arrive with the account rather than being recreated.

It is actively maintained, and the current release is downloaded from the GitHub releases page, which is worth checking before diagnosing a display difference.

For a token that will not appear at all, [Issued tokens and TrustLines in practice](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/issued-tokens-and-trustlines-in-osmwallet.md). For the reserve arithmetic behind the lower spendable balance, [The XRP reserve, explained without the confusion](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/xrp-reserve-explained-osmwallet.md), and for a restore after a lost machine, *Restoring access after losing a device* and *Protecting a seed phrase you cannot reset*.

### FAQ

### Do I have to re-add trustlines after importing a seed?

No, if you imported the account that held them. Trustlines are ledger entries on that account, so they appear with it. You would only re-add one for a genuinely new account.

### Why did my XRP balance drop after importing?

It did not drop; the requirement rose. Trustlines that came with the account require additional reserve, so the spendable amount is lower even though the total is unchanged.

### Can I move a trustline to another account?

No. A trustline belongs to one account. To hold the same token elsewhere you create a trustline on the new account and send the tokens to it.

### What happens to reserve when I remove a trustline?

It is released once the token balance on that trustline is zero. Removing the trustline with tokens still held is not possible until they are moved or spent.
