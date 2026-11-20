<p align="center">
  <img src="assets/banner-article.png" alt="OSM Wallet guide" width="100%">
</p>

# Setting up an XRP wallet from zero

Setting up an XRP wallet takes a few minutes: install the app, create an account, write the recovery phrase down, fund the account past the base reserve, and send a small test payment before moving anything meaningful. Every XRP wallet follows that shape, because the account lives on the XRP Ledger rather than inside the app you install.

## What you are actually setting up

An XRP Ledger account is a pair of keys plus a ledger entry. The wallet is the software that holds the key and talks to the network, so "setting up a wallet" is really two steps: installing software, and creating or importing the key that controls an account. Keeping them separate explains most of what follows, including why an uninstalled wallet does not lose funds.

The account is identified by an address starting with an `r`, which is safe to share, and controlled by a key you must never share. The recovery phrase is the key written out in a form you can back up on paper.

## The steps

1. **Get the app from the official source.** For OSM Wallet, that is the project's releases page or the site, not a link from a message, an ad or a mirror.
2. **Create a new account** if this is your first one, or choose import if you already hold XRP elsewhere.
3. **Write the recovery phrase** on paper, in order, and read it back against the screen.
4. **Fund the account** with enough to cover the base reserve plus the amount you intend to hold.
5. **Confirm the deposit** appears in the wallet with the reserve accounted for.
6. **Send a small amount out** to prove the key works before trusting the wallet with a larger balance.
7. **Store the backup separately** from the device and from any cloud storage.

Step three is the one to slow down for. A phrase written with two words swapped produces a valid-looking backup that restores a different, empty account, and the error usually surfaces months later when the device is gone.

## What the first funding has to clear

An XRP Ledger account must hold a base reserve to exist. A first deposit below that amount does not leave you with a usable account, and a deposit at exactly that amount leaves nothing sendable. Fund above the reserve rather than at it, and expect the reserve to remain unavailable while the account exists.

The reserve is also why an account with issued tokens can show less available than expected: each trustline adds its own reserve requirement. If you plan to hold tokens, fund with margin rather than trimming to the minimum. The full arithmetic is in [The XRP reserve, explained without the confusion](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/xrp-reserve-explained-osmwallet.md), and the practical version when a send is refused is [Sending your full XRP balance](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/send-max-xrp-balance-osmwallet.md).

## Where OSM Wallet differs from a generic XRP wallet

OSM Wallet is a non-custodial XRP Ledger wallet built for desktop first: Windows, macOS and Linux, plus a browser extension. It does not chase multi-chain support, so the setup is narrower than a general-purpose wallet and the screens are about accounts, trustlines, tokens, swaps and payments rather than a portfolio of chains.

That narrowness matters for setup in one specific way: the wallet assumes you are working on a computer. If your habit is a phone, a desktop-first wallet is the wrong tool, and no amount of setup will change that. If you work at a desk, the desktop app keeps the key on one machine rather than in a browser profile shared with everything else.

The wallet is actively maintained, and the current release is downloaded from the GitHub releases page. Check that you are on it before diagnosing any problem, because a guide describes the current build.

## Importing instead of creating

If you already have an XRP account, creating a new one is optional. Choose import, enter the recovery phrase or secret for the existing account, and the wallet reads the balance and history from the ledger. Nothing is transferred by an import; the account never left the network. The steps and the pitfalls are in *Importing an existing XRP wallet*.

The one thing an import does not bring across is app-level state: local settings, saved contacts, an open session. Those belong to the app you left, not to the account.

## What to do straight after setup

Two habits make the difference between a wallet you can use and one you hope never breaks. Send a small test payment to yourself or to a destination you control, and confirm it arrives; then restore the wallet from the phrase on a second machine, or at least read the phrase back carefully, so the backup is proven rather than assumed.

If you are moving a balance in from an exchange, the withdrawal path has its own rules about destination tags, covered in [Moving XRP from an exchange into your own wallet](https://github.com/osmwallet/beginner-explainers/blob/HEAD/moving-xrp-from-an-exchange-into-osmwallet.md). For the ordered first-run checklist, see *First run: the setup checklist*, and for the model behind the phrase, *Protecting a seed phrase you cannot reset*.

### FAQ

### How long does setting up an XRP wallet take?

A few minutes plus the funding step. The slow part is waiting for the first deposit to validate or for an exchange to process a withdrawal, not the wallet setup itself.

### Do I need XRP before I create a wallet?

You need XRP to activate an account, because the ledger requires a base reserve. You can create the key and back it up first and fund it later, but the account does not exist on the ledger until it is funded.

### Can I set up the same account in two wallets?

Yes. Import the same recovery phrase into a second wallet and both will show the same account and balance, because the account is on the ledger. Keeping two copies of the key in active use doubles your exposure, so do it deliberately.

### Is a desktop wallet the right choice for a first wallet?

It is if you will use the XRP Ledger from a computer. For payments on the go a mobile wallet fits better, and for a balance you rarely move a hardware device is worth considering before you fund heavily.
