# AdImmunity — Privacy Policy

**Effective Date:** March 15, 2026

---

## Overview

AdImmunity is a Chrome browser extension that blocks advertisements and trackers on websites. This privacy policy explains how AdImmunity handles user data.

## Data Collection

**AdImmunity does not collect, store, or transmit any personal data.** The extension operates entirely on your local device.

The only data stored by the extension is:

- **User preferences**: Your settings such as whether ad blocking is enabled and any websites you have whitelisted. These are stored locally on your device using Chrome's built-in storage API.
- **Blocking statistics**: Aggregate counts of ads blocked, trackers blocked, and DOM elements removed. These counters are stored locally and reset daily. They contain no information about which websites you visited or what content was blocked.

## Data Sharing

AdImmunity does **not** share, sell, transfer, or transmit any data to third parties. All extension functionality operates locally within your browser.

## Network Requests

AdImmunity does **not** make any network requests to external servers. The extension works by:

1. Blocking outgoing requests to known ad-serving and tracking domains using Chrome's Declarative Net Request API.
2. Removing ad-related elements from web page content using local content scripts.

No data about your browsing activity leaves your device through AdImmunity.

## Remote Code

AdImmunity does **not** use any remote code. All scripts and resources are bundled within the extension package. No external JavaScript is loaded, and no dynamic code execution (such as `eval()`) is used.

## Permissions

AdImmunity requests the following permissions solely to fulfill its ad-blocking functionality:

| Permission | Purpose |
|---|---|
| `declarativeNetRequest` | Block ad/tracker network requests |
| `declarativeNetRequestWithHostAccess` | Apply blocking rules across all websites |
| `declarativeNetRequestFeedback` | Count blocked requests for user statistics |
| `storage` | Save user preferences and stats locally |
| `scripting` | Inject scripts to remove ad elements from pages |
| `tabs` | Detect page navigation for timely ad blocking |
| `activeTab` | Show stats for the current tab in the popup |
| `webNavigation` | Handle navigation events and iframe ad blocking |
| `alarms` | Schedule daily statistics reset |
| Host permission (`<all_urls>`) | Enable ad blocking on all websites |

## User Rights

Since AdImmunity does not collect any personal data, there is no personal data to access, modify, or delete. Your locally stored preferences and statistics can be cleared at any time by uninstalling the extension or clearing extension data through Chrome's settings.

## Children's Privacy

AdImmunity does not collect data from any users, including children under the age of 13.

## Changes to This Policy

If this privacy policy is updated, the revised version will be made available alongside the extension. Continued use of AdImmunity after any changes constitutes acceptance of the updated policy.

## Contact

If you have questions about this privacy policy, please open an issue on the extension's support page or contact the developer through the Chrome Web Store listing.
