# AdImmunity — Privacy Policy

**Effective Date:** March 25, 2026

---

## Overview

AdImmunity is a Chrome browser extension that blocks advertisements and trackers on websites and warns users before navigating to known phishing or malware domains. This privacy policy explains how AdImmunity handles information on your device and the limited network requests it makes.

## Data the developer receives

**AdImmunity does not send your data to the developer, analytics services, or any developer-operated server.** There is no account system, no telemetry, and no developer-side cloud sync. Your browsing history, page contents, form data, and personal information are never transmitted to the developer.

## What is stored on your device

AdImmunity uses two of Chrome's storage areas:

### Local storage (`chrome.storage.local`) — stays on this device

- **Statistics:** Aggregate counters such as ads blocked, trackers blocked, popups blocked, and scripts blocked. These are numeric counters, not a log of every URL you visit.
- **Per-tab statistics:** While a tab is open, AdImmunity keeps an in-memory tally of ads and trackers blocked on that tab so the popup can show a "Privacy Receipt" for the current page. This data is cleared when the tab closes or you navigate away — it is never persisted to disk and never leaves your device.
- **Phishing blocklist cache:** A list of domains downloaded from URLhaus (see "Network requests" below) is cached locally so the warning page can load offline.
- **Optional "Report missed ad":** If you click *Report Missed Ad* in the popup, AdImmunity may save the **page URL**, **hostname**, **text you typed** in the description field, and (if you choose to attach one) **a screenshot of the visible tab**. These reports are stored only in your local Chrome profile to help you document issues. **They are not uploaded by the extension** to the developer or any server. Old reports are pruned automatically (the most recent 50 are retained).
- **Theme preference:** Your dark/light mode choice for the popup.

### Sync storage (`chrome.storage.sync`) — roams across your signed-in Chrome profiles

If you are signed in to Chrome and have Chrome Sync enabled, the following preferences are synchronised across your devices through Google's sync infrastructure (the same mechanism Chrome uses for bookmarks and other settings):

- Whether AdImmunity is enabled
- Which feature toggles are on (DOM scanning, network blocking, cookie banner dismissal, phishing protection, debug mode)
- The list of sites you have whitelisted (paused) for AdImmunity, capped at 200 entries

If you do not use Chrome Sync, this data stays on the local device. AdImmunity does not transmit these preferences to the developer in either case.

## Data sharing

AdImmunity does **not** sell, rent, or transmit stored data to third parties or to the developer. The extension does not include analytics SDKs, advertising SDKs, or cross-site identifiers.

## Network requests

AdImmunity makes the following network requests:

1. **Blocking ads and trackers.** Chrome's [Declarative Net Request](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest) API blocks requests to known ad and tracker domains based on a static rule list packaged with the extension. The extension itself does not initiate these requests — Chrome consults the rule list when sites you visit try to load them.
2. **Phishing/malware protection.** Once per day, AdImmunity downloads a public hosts-file blocklist from **URLhaus** (`https://urlhaus.abuse.ch/downloads/hostfile/`), a free threat-intelligence feed maintained by abuse.ch. The download contains a list of currently known malicious domains and is unauthenticated and anonymous (no personal information is sent in the request). The list is cached locally for offline use. URLhaus's own privacy notice applies to that request: <https://urlhaus.abuse.ch/>.

AdImmunity does not contact the developer's servers and does not stream your browsing data anywhere.

## Remote code

AdImmunity does **not** load executable code from the internet. All JavaScript and rule lists included in the extension are packaged with the extension at install time, as required by Chrome Web Store / Manifest V3. The phishing blocklist downloaded from URLhaus is **plain-text data only** (a list of domains) — it is never executed as code.

## Permissions

AdImmunity requests permissions only for ad blocking, the popup, and phishing protection:

| Permission | Purpose |
|---|---|
| `declarativeNetRequest` | Block ad and tracker network requests using the bundled rule list |
| `declarativeNetRequestWithHostAccess` | Apply network rules on the sites you visit |
| `storage` | Save settings, statistics, theme preference, cached phishing list, and optional local reports |
| `tabs` | Read the active tab's host for the popup; broadcast enable/disable messages to open tabs when you change settings |
| `activeTab` | Act on the current tab when you use the popup (e.g., the optional screenshot for a report) |
| `alarms` | Schedule the daily statistics reset and the daily phishing-list refresh |
| `webNavigation` | Detect main-frame navigations to known phishing/malware domains and redirect to the safety warning page before the dangerous site loads |
| Host permission (`<all_urls>`) | Inject the declared content scripts and apply blocking on every site |

Content scripts are listed in `manifest.json`. AdImmunity does **not** request the `scripting`, `cookies`, `history`, `bookmarks`, `geolocation`, `notifications`, or `identity` permissions.

## Phishing warning page

If AdImmunity blocks a navigation to a domain on the URLhaus list, it redirects the tab to a built-in warning page (`warning/warning.html`). The blocked URL and hostname are passed in the warning page's URL parameters so you can see what was blocked and choose to proceed anyway. This information stays in your browser — it is not transmitted anywhere.

## Children's privacy

The extension is not directed at children under 13 and does not knowingly collect personal information for the developer.

## Your choices

- You can disable any feature toggle in the popup at any time.
- You can whitelist specific sites with one click in the popup.
- You can clear all extension data by removing AdImmunity in Chrome's extension settings, which deletes locally stored settings, stats, cached phishing list, and saved reports. If you used Chrome Sync, you may also need to clear synced data through your Google Account.

## Changes

Updates to this policy will be reflected in the published privacy policy URL linked from the Chrome Web Store. Material changes will be noted in the extension's update changelog.

## Contact

Questions about this policy can be sent through the Chrome Web Store listing or the project's GitHub repository linked in the extension popup.
