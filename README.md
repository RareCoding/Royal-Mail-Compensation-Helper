# Royal Mail Compensation Helper

A Manifest V3 Chrome extension that helps eBay sellers prepare Royal Mail compensation claims from Seller Hub’s **All Orders** page.

It adds a compact **Claim Compensation** column to eBay orders, provides service and compensation reference tables, passes available order information into Royal Mail’s online form, and keeps the final decisions with the user.

> **Important:** This project is independent and is not affiliated with eBay, Royal Mail, Parcelforce Worldwide, or CEDR. It does not determine claim eligibility or guarantee a claim outcome. Check the current terms, deadlines, service level, proof requirements, and every form answer before submitting.

## What it does

- Adds a **Claim Compensation** column to eBay Seller Hub All Orders.
- Shows tracking, order number, and postage information in a consistent order.
- Identifies orders that are delivered, cancelled, or feedback-complete and visually mutes the related controls.
- Offers a user-led **Get Tracking** workflow for orders where eBay has no tracking number recorded.
- Cleans copied tracking values by removing spaces and dashes, opens eBay’s Add tracking form, and selects Royal Mail without saving the form.
- Opens Royal Mail’s claim form with available eBay order data.
- Provides Domestic and International compensation reference tables in the extension popup.
- Stores optional auto-complete profile details locally in Chrome extension storage.
- Adds a visible guidance message if Royal Mail returns the eP58 / eBay Simple Delivery eligibility outcome.

## What it does not do

- It does not upload proofs, complete CAPTCHA, submit a Royal Mail claim, press Royal Mail **Next**, or press eBay **Save and continue**.
- It does not make a compensation decision for you.
- It does not send your profile data to a third-party server.

## Install locally

1. Download or clone this repository.
2. Open `chrome://extensions` in Chrome.
3. Turn on **Developer mode**.
4. Select **Load unpacked**.
5. Choose this repository’s root folder, the folder containing `manifest.json`.
6. Open eBay Seller Hub’s All Orders page.

For updates, pull the new changes and click **Reload** on the extension card in `chrome://extensions`.

## Using the extension

### Start a claim

1. Open eBay Seller Hub → **All Orders**.
2. Locate the order in the new **Claim Compensation** column.
3. Confirm the displayed order, tracking, and postage details.
4. Select **Claim Compensation**.
5. Review the Royal Mail form and complete each step yourself.

### Add tracking from an eBay postage label

1. Select **Get Tracking** for an order that has no eBay tracking reference.
2. In eBay’s Print documents window, select **Postage label** and clear **Invoice/Packing slip**.
3. Copy the tracking reference from the label.
4. The extension removes spaces and dashes, opens eBay’s Add tracking form, and selects Royal Mail.
5. Check the value and save the eBay form yourself.

## Auto-complete profile

The popup’s **Configure auto-complete information** page can store the following locally:

- Title, first name, and last name
- Address lines, town, and postcode
- Email address
- Usual posting method
- Usual posting location

The values are used only to speed up compatible Royal Mail form fields. Leave a field blank when it varies by order.

## Permissions and privacy

See [PRIVACY.md](PRIVACY.md) for the full data-handling summary.

The current manifest includes permissions for `scripting`, `storage`, `cookies`, `webRequest`, `tabs`, `clipboardRead`, and `clipboardWrite`, plus broad host access. Before publishing to the Chrome Web Store, review whether every declared permission and host pattern is still necessary, and provide clear Chrome Web Store privacy disclosures.

## Development

There is no build step. Load the repository root as an unpacked extension after changes.

Validate the manifest and referenced assets with:

```bash
python3 scripts/validate_manifest.py
```

Before opening a pull request, test at least:

- eBay All Orders rendering and row refreshes
- Delivered, cancelled, and feedback-complete states
- Tracking-copy workflow and manual eBay save
- Royal Mail domestic and international form paths
- eP58 / Simple Delivery guidance display
- Popup profile storage and prefill

## Repository structure

```text
.github/                 GitHub templates and validation workflow
icon/                    Extension icons
scripts/                 Local validation utility
ebay.js / ebay.css       eBay Seller Hub integration
royalmail.js / .css      Royal Mail form integration
popup.*                  Extension popup and settings
service_worker.js        Manifest V3 background worker
manifest.json            Chrome extension manifest
```

## Contributing

Read [CONTRIBUTING.md](CONTRIBUTING.md) before opening an issue or pull request. Please remove personal data, order IDs, buyer details, tracking codes, and screenshots of private information from reports.

## Security

See [SECURITY.md](SECURITY.md). Do not submit security-sensitive reports through a public issue.

## License

No license has been selected for this repository yet. Choose and add a license before accepting external contributions or presenting the project as open source.

## Trademarks

eBay, Royal Mail, Parcelforce Worldwide, CEDR, and Chrome are trademarks of their respective owners. See [NOTICE.md](NOTICE.md).
