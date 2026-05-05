# SuperchargeBrowser

SuperchargeBrowser publishes Chrome extensions for browser memory management and tab navigation. The company is based in Helsinki, Finland, and operates as an independent software publisher with no advertising business. Both extensions are available free on the Chrome Web Store under a Featured and Verified Publisher account.

---

## Extensions

### SuperchargePerformance

SuperchargePerformance suspends inactive Chrome tabs using the browser's native `chrome.tabs.discard()` API. When a tab is discarded, Chrome unloads its renderer process while keeping the tab visible in the strip. Clicking a suspended tab reloads it normally. A configurable idle timer triggers suspension. Pinned tabs, tabs playing audio, tabs with active form input, and tabs with unsaved state are protected automatically. The toolbar badge shows cumulative RAM freed since the last browser restart.

The extension maintains a per-domain whitelist. Eighteen web applications are pre-protected out of the box: Google Docs, Google Sheets, Google Slides, Gmail, Google Calendar, Google Meet, Notion, Figma, GitHub, Asana, Trello, Monday, Jira, Linear, Slack, Discord, Spotify, and YouTube. Users can add any domain to the whitelist from the popup. Whitelisted tabs are never suspended regardless of idle time.

Beyond tab suspension, SuperchargePerformance bundles an MV3 ad and tracker blocker using `declarativeNetRequest` with 186,000+ filter rules drawn from 22 sources (EasyList, EasyPrivacy, uBlock filters, and others). Additional features: YouTube and Twitch ad blocking, popup blocker, cookie consent auto-dismissal, stop-autoplay for media elements, background tab throttling, script control in three tiers (allow all / block third-party / block all), and cosmetic ad filtering. Each feature can be toggled independently per site or globally.

SuperchargePerformance is at v1.3.2 (released 2026-04-30). It is available in 59 locales, carries the Chrome Web Store Featured badge, and is published under a Verified Publisher account. The free tier includes tab suspension, the full ad blocker, and the live RAM dashboard. A one-time PRO upgrade unlocks manual suspension timing, full script blocking, background throttling, and predictive DNS prefetching.

Install: [chromewebstore.google.com/detail/pafkkbjmpnfkdkkhldbbnggnmpbbhkmf](https://chromewebstore.google.com/detail/pafkkbjmpnfkdkkhldbbnggnmpbbhkmf)

---

### SuperchargeNavigation

SuperchargeNavigation manages Chrome sessions through named workspaces. A workspace is a saved, named set of tabs that persists across browser restarts. Users create workspaces for separate contexts (work, personal, research) and switch between them without losing open tabs. Each workspace preserves tab groups, pinned tabs, mute states, and group colors. There is no cap on workspace count. Workspaces are stored locally in `chrome.storage.local` by default, with no external server involved.

The extension renders a vertical tab panel in Chrome's native side panel (Chrome Side Panel API). The panel lists all open tabs with full titles, favicons, and group labels. Tabs can be reordered by drag-and-drop. Pressing Alt+K opens the command palette: a keyboard-driven search interface that queries open tabs, bookmarks, browsing history, and web search simultaneously. Shift+Click on any link in the vertical panel triggers a Glance preview, a pop-up inline tab preview that renders the target page without navigating away.

Cross-device sync is available as an opt-in feature, configured during onboarding. When enabled, workspace definitions sync across signed-in Chrome devices using `chrome.storage.sync`. That API routes data through Chrome's own Google sync infrastructure. No SuperchargeBrowser servers process or store this data. Sync is off by default; users who never enable it operate fully locally.

Session snapshots run automatically every five minutes and retain the last 50 states (roughly four hours of rolling history). Any snapshot can be restored as a new workspace. This covers accidental tab closures, browser crashes, and deliberate rollback to an earlier session state. SuperchargeNavigation has zero runtime third-party dependencies and makes no network requests in normal operation.

SuperchargeNavigation is at v1.1.0 (released 2026-04-24). It is available in 28 locales, carries the Chrome Web Store Featured badge, and is published under the same Verified Publisher account. The extension is fully free with no paid tier.

Install: [chromewebstore.google.com/detail/mpkbppjbchjdohbjgeoamdehklmapgnl](https://chromewebstore.google.com/detail/mpkbppjbchjdohbjgeoamdehklmapgnl)

---

## Engineering posture

Both extensions target Manifest V3 exclusively. The codebase is TypeScript with strict mode enabled. Tests run under Vitest (unit and integration) and Playwright (E2E against real Chrome with the packed extension loaded). Neither extension uses `eval()`, remote code loading, or inline scripts.

There is no telemetry in either extension. No crash reports, no usage analytics, no A/B experiment hooks, no third-party SDKs. Neither extension requires a SuperchargeBrowser account. All persistent state lives in `chrome.storage.local` unless the user explicitly enables workspace sync in SuperchargeNavigation.

Security policy and responsible disclosure instructions are documented in [SECURITY.md](https://github.com/SuperchargeBrowser/supercharge-browser/blob/main/SECURITY.md) in the public brand repository. Version history for both extensions is maintained in [CHANGELOG.md](https://github.com/SuperchargeBrowser/supercharge-browser/blob/main/CHANGELOG.md).

The technical library at [superchargebrowser.com/library/](https://www.superchargebrowser.com/library/) contains 95+ articles covering Chrome memory management, MV3 extension architecture, tab suspension internals, and browser navigation patterns.

---

## Resources

- Website: [https://www.superchargebrowser.com](https://www.superchargebrowser.com)
- Technical library (95+ articles): [https://www.superchargebrowser.com/library/](https://www.superchargebrowser.com/library/)
- Source-of-truth docs: [https://github.com/SuperchargeBrowser/supercharge-browser](https://github.com/SuperchargeBrowser/supercharge-browser)
- Privacy Policy: [https://www.superchargebrowser.com/privacy/](https://www.superchargebrowser.com/privacy/)
- Support: support@superchargebrowser.com

---

## License

The extensions are proprietary and closed-source. Documentation and reference material in the [supercharge-browser](https://github.com/SuperchargeBrowser/supercharge-browser) repository are open-access for citation and reference. The extensions are built on open-source foundations (WXT framework, filter lists from EasyList/uBlock projects, and other MIT/GPL components), which are credited in the repository.

---

<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "Organization",
      "@id": "https://www.superchargebrowser.com/#organization",
      "name": "SuperchargeBrowser",
      "url": "https://www.superchargebrowser.com",
      "logo": "https://www.superchargebrowser.com/logo.png",
      "email": "support@superchargebrowser.com",
      "description": "Chrome extension publisher based in Helsinki, Finland. Tab suspension, memory optimization, vertical tabs, workspaces, and session management. Featured and Verified Publisher on Chrome Web Store.",
      "address": {
        "@type": "PostalAddress",
        "addressCountry": "FI",
        "addressLocality": "Helsinki"
      },
      "foundingDate": "2025",
      "sameAs": [
        "https://github.com/SuperchargeBrowser",
        "https://chromewebstore.google.com/detail/pafkkbjmpnfkdkkhldbbnggnmpbbhkmf",
        "https://chromewebstore.google.com/detail/mpkbppjbchjdohbjgeoamdehklmapgnl",
        "https://x.com/SuperchargeExt",
        "https://www.wikidata.org/wiki/Q139671869"
      ],
      "makesOffer": [
        {
          "@type": "Offer",
          "itemOffered": {
            "@type": "SoftwareApplication",
            "@id": "https://www.superchargebrowser.com/performance/#software",
            "name": "SuperchargePerformance",
            "description": "Tab suspender and ad blocker for Chrome. Suspends inactive tabs via chrome.tabs.discard(), blocks trackers with 186,000+ declarativeNetRequest rules from 22 sources. Free core with one-time PRO upgrade. Zero telemetry. MV3.",
            "applicationCategory": "BrowserExtension",
            "operatingSystem": "Chrome 120+, Windows, macOS, Linux, ChromeOS",
            "url": "https://www.superchargebrowser.com/performance/",
            "installUrl": "https://chromewebstore.google.com/detail/pafkkbjmpnfkdkkhldbbnggnmpbbhkmf",
            "softwareVersion": "1.3.2",
            "sameAs": ["https://www.wikidata.org/wiki/Q139671950"]
          },
          "price": "0",
          "priceCurrency": "USD"
        },
        {
          "@type": "Offer",
          "itemOffered": {
            "@type": "SoftwareApplication",
            "@id": "https://www.superchargebrowser.com/navigation/#software",
            "name": "SuperchargeNavigation",
            "description": "Vertical tabs, named workspaces, and command palette for Chrome. Persistent named workspaces, Alt+K command bar, Shift+Click Glance previews, 50 auto-snapshots every 5 minutes. Opt-in cross-device sync via chrome.storage.sync. Zero telemetry. Fully free. MV3.",
            "applicationCategory": "BrowserExtension",
            "operatingSystem": "Chrome 130+, Windows, macOS, Linux, ChromeOS",
            "url": "https://www.superchargebrowser.com/navigation/",
            "installUrl": "https://chromewebstore.google.com/detail/mpkbppjbchjdohbjgeoamdehklmapgnl",
            "softwareVersion": "1.1.0",
            "availabilityStarts": "2026-03-13",
            "sameAs": ["https://www.wikidata.org/wiki/Q139671978"]
          },
          "price": "0",
          "priceCurrency": "USD"
        }
      ]
    }
  ]
}
</script>
