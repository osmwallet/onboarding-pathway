<p align="center">
  <img src="assets/banner-article.png" alt="OSM Wallet guide" width="100%">
</p>

# Moving from Xaman to a desktop wallet

There are two ways to move an account from Xaman to OSM Wallet, and they solve different problems. Export the account's secret in Xaman and import it in OSM Wallet to keep the same account, address and history. Or create a new account in OSM Wallet and send the balance across, which leaves the old account in place. The first keeps everything; the second starts clean.

## Which route fits

Keeping the same account is right when you have a history you care about, trustlines you want to carry, or an address other people already have. Starting a new account is right when the old one is compromised, when you want a clean separation, or when you would rather not export a secret at all.

The trade is exposure against continuity. Exporting a secret means the secret is briefly visible on screen, which is the moment to be alone and careful. Sending the balance across instead never exposes the key, but costs the history, the trustlines and the address.

For the import mechanics without the migration context, see [Importing an existing XRP wallet](https://github.com/osmwallet/onboarding-pathway/blob/HEAD/import-an-existing-xrp-seed-into-osmwallet.md).

## Route one: keep the same account

1. **Before you start**, have Xaman open on the device and OSM Wallet installed and ready on the computer.
2. **In Xaman, open the account's security settings** and choose the option that reveals the account secret. Read the warning: anyone who sees it can move the funds.
3. **Copy the secret, or write it down**, in one step, with nothing else on screen and nothing recording.
4. **In OSM Wallet, choose import** and enter the secret or the recovery phrase, depending on what Xaman showed.
5. **Compare the resulting address** with the address in Xaman, character by character. They must be identical.
6. **Check the balance and the trustlines**, which come from the ledger and should match.
7. **Send a small test payment** to prove the imported key can sign.
8. **Finish the move in Xaman**: remove the account there, so one copy of the key remains in use.

Step eight is the one people skip, and it is the difference between a migration and two copies of the same key sitting on two devices.

## Route two: send the balance across

1. **Create a new account in OSM Wallet** and back it up before it holds anything.
2. **Copy its address** from the receive screen.
3. **Send a small test amount from Xaman** and confirm it arrives.
4. **If the account holds tokens**, the new account needs trustlines first, or the tokens have nowhere to land.
5. **Send the remaining XRP**, leaving the reserve behind in Xaman.
6. **Once everything has arrived**, delete the old account in Xaman to recover its reserve, or leave it deliberately.

This route needs more transactions and two reserves' worth of XRP in play, which is its real cost. It also means the old account's address stops being useful, so anything that pays you at it needs updating.

## What does not come across on either route

Local app state stays behind on both routes: contacts, notes, display settings, a session you had open. Neither route moves the account to a different ledger location, because there is nowhere else for it to go; the account is on the XRP Ledger and both apps are readers of the same network.

Trustlines do come across on route one, because they belong to the account rather than the app. On route two they do not, because a new account starts with none, and that is where token transfers fail quietly.

## The risk that matters in this specific migration

The secret is the account. Revealing it in Xaman puts it on the screen, the clipboard and possibly a screenshot roll, which is why the export step is worth doing alone, on a clean device, with screen recording off. If you are unsure whether the secret was exposed, treat it as exposed and take route two or move the balance to a fresh account afterwards.

OSM Wallet is a non-custodial XRP Ledger wallet for desktop and browser, and it asks for a secret only in its own import screen. No support channel needs it. The wallet is actively maintained and the current release is downloaded from the GitHub releases page.

For the trustline behaviour that decides whether tokens follow, [What happens to your TrustLines after an import](https://github.com/osmwallet/onboarding-pathway/blob/HEAD/trustlines-after-importing-a-seed-osmwallet.md) and [Issued tokens and TrustLines in practice](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/issued-tokens-and-trustlines-in-osmwallet.md). For the reserve arithmetic when emptying the old account, *The XRP reserve, explained without the confusion*, and for the storage model behind the phrase, *Protecting a seed phrase you cannot reset*.

### FAQ

### Do I have to create a new address to use OSM Wallet?

No. Importing the account keeps the same address, history and trustlines. Creating a new one is a choice about continuity, not a requirement.

### Is exporting the secret from Xaman safe?

It is as safe as the moment it happens. On a clean device, alone, with nothing recording, it is a controlled exposure. On a shared or compromised machine it is the whole account.

### Will my tokens move with the account?

They will if you keep the same account, because trustlines belong to it. If you create a new account, add the trustlines there before sending tokens, or the transfer has nowhere to land.

### What happens to the old account afterwards?

If you keep the same account, the old app should have it removed so one key copy stays in use. If you moved the balance to a new account, delete the old one to recover its reserve, or leave it empty and funded deliberately.
