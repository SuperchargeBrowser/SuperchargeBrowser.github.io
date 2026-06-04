# SuperchargeBrowser

SuperchargeBrowser is an independent browser-extension publisher based in Helsinki, Finland. It builds and maintains a small set of Chrome and Edge extensions focused on browser performance, navigation, and audio. The publisher operates no advertising business and sells no user data; every extension is free to install on the official stores. On the Chrome Web Store, SuperchargeBrowser holds both the Featured badge and Verified Publisher status. Three extensions are currently published: SuperchargePerformance, SuperchargeNavigation, and SuperchargeAudio.

## Extensions

### SuperchargePerformance

SuperchargePerformance reduces memory pressure and removes web clutter. It suspends inactive tabs through `chrome.tabs.discard()` on an idle timer, and the toolbar badge reports cumulative RAM freed since the last browser restart. Tabs that are pinned, playing audio, or holding form input and unsaved state are protected automatically and never suspended. A per-domain whitelist gives manual control, and 28 popular web apps including Google Workspace, Notion, Figma, Linear, Slack, Discord, Microsoft Teams, Zoom, Spotify, and others are protected out of the box.

The extension also ships an MV3 ad and tracker blocker built on `declarativeNetRequest`, drawing 186,000+ rules from 22 sources including EasyList, EasyPrivacy, uBlock filters, and others. Beyond blocking, it handles YouTube and Twitch ad blocking, popup blocking, cookie-consent auto-dismissal, stop-autoplay, and background tab throttling. Script execution is governed by a three-tier control (allow all, block third-party, block all), alongside cosmetic filtering, a live RAM dashboard, link preloading, font optimization, lazy loading, and a safe mode for diagnosing site issues. A one-time PRO upgrade unlocks manual suspension timing, full script blocking, background throttling, and predictive DNS prefetch. The free core remains fully functional without it.

SuperchargePerformance is available on the Chrome Web Store, where it carries the Featured badge, and on Microsoft Edge Add-ons, in 59 locales.

Install on Chrome: https://chromewebstore.google.com/detail/pafkkbjmpnfkdkkhldbbnggnmpbbhkmf — Install on Edge: https://microsoftedge.microsoft.com/addons/detail/superchargeperformance-t/heappihlcojbpofeigdcggabhblmdjol

### SuperchargeNavigation

SuperchargeNavigation is a fully free tab and window manager with no paid tier. Its core is named workspaces: saved named tab sets that persist across restarts and preserve tab groups, pinned state, mute state, and group colors, with no cap on how many you keep. Workspaces are stored locally in `chrome.storage.local`. A vertical tab panel lives in Chrome's native Side Panel, showing titles, favicons, and group labels with drag-to-reorder.

Navigation across the browser is keyboard-driven. The Alt+K command palette searches open tabs, bookmarks, history, and the web. Shift+Click Glance shows an inline preview of a link without navigating away. Alt+G groups tabs by domain and Alt+Shift+G undoes it, and Super Drag and tab deduplication round out the workflow. Session snapshots are captured automatically every five minutes, with the last 200 states retained in a ring buffer; any snapshot can be restored as a new workspace. Cross-device sync is opt-in and off by default. When enabled it uses `chrome.storage.sync`, Chrome's own Google sync infrastructure, so no data passes through any SuperchargeBrowser server; until then everything stays fully local.

SuperchargeNavigation is available on the Chrome Web Store, where it carries the Featured badge, in 59 locales, and requires Chrome 130 or later.

Install on Chrome: https://chromewebstore.google.com/detail/mpkbppjbchjdohbjgeoamdehklmapgnl

### SuperchargeAudio

SuperchargeAudio is a fully free per-tab audio engine. It boosts volume up to 600% using a Web Audio API `GainNode`, and provides a 10-band equalizer spanning 32Hz to 16kHz, each band adjustable by ±12dB, with 10 built-in presets: Flat, Bass Boost, Vocal, Treble, Loudness, Rock, Pop, Electronic, Acoustic, and Small Speakers. Smart Mute silences background audible tabs while keeping the active tab audible, with per-site allow and block controls. Volume and EQ settings are remembered per domain in `chrome.storage.local`.

For listening on headphones, it adds an 8D rotating stereo field, Bauer crossfeed, and stereo width from 0 to 200%, ranging from mono to extra-wide. Audio is processed through the Web Audio API; for DRM and EME-protected streams it falls back to Chrome's tab-capture into an offscreen document. There is zero telemetry, all processing is local, and no account is required.

SuperchargeAudio is live on Microsoft Edge Add-ons; the Chrome Web Store listing is pending review. It is available in 59 locales.

Install on Edge: https://microsoftedge.microsoft.com/addons/detail/superchargeaudio-volume-/iknpdbfmeiefmfofkfkbcakpnmlbncia

## Engineering posture

All three extensions are Manifest V3 exclusive and written in TypeScript under strict mode. Tests run on Vitest for unit and integration coverage and Playwright for end-to-end runs against real Chrome with the packed extension. None of the extensions use `eval()`, load remote code, or inject inline scripts. Telemetry is zero across all three: no crash reports, no analytics, no A/B hooks, and no third-party SDKs. No account is required. State is held in `chrome.storage.local`, with the sole exception of SuperchargeNavigation's opt-in workspace sync.

Security policy and full version history are published as `SECURITY.md` and `CHANGELOG.md` in the source-of-truth repository at https://github.com/SuperchargeBrowser/supercharge-browser. A technical library of 121 articles is maintained at https://www.superchargebrowser.com/library/.

## Resources

- Website: https://www.superchargebrowser.com
- Technical library (121 articles): https://www.superchargebrowser.com/library/
- Source-of-truth documentation: https://github.com/SuperchargeBrowser/supercharge-browser
- Privacy policy: https://www.superchargebrowser.com/privacy/
- Support: support@superchargebrowser.com

## License

The extensions themselves are proprietary and closed-source. The documentation in the supercharge-browser repository is open-access for citation and reference. The extensions are built on open-source foundations, including WXT, the EasyList and uBlock filter lists, and other MIT and GPL-licensed components, all credited in the repository.

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
      "foundingDate": "2025",
      "address": {
        "@type": "PostalAddress",
        "addressLocality": "Helsinki",
        "addressCountry": "FI"
      },
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
          "price": "0",
          "priceCurrency": "USD",
          "itemOffered": {
            "@type": "SoftwareApplication",
            "@id": "https://www.superchargebrowser.com/performance/#software",
            "name": "SuperchargePerformance",
            "url": "https://www.superchargebrowser.com/performance/",
            "installUrl": "https://chromewebstore.google.com/detail/pafkkbjmpnfkdkkhldbbnggnmpbbhkmf",
            "applicationCategory": "BrowserExtension",
            "operatingSystem": "Chrome 120+, Microsoft Edge, Windows, macOS, Linux, ChromeOS",
            "softwareVersion": "1.4.1",
            "description": "Suspends inactive tabs on an idle timer to free RAM, protecting pinned, audible, and form-input tabs automatically, with a per-domain whitelist and 28 pre-protected web apps. Includes an MV3 declarativeNetRequest ad and tracker blocker with 186,000+ rules from 22 filter sources, YouTube and Twitch ad blocking, cookie-consent dismissal, three-tier script control, and a live RAM dashboard. Free core with an optional one-time PRO upgrade. Available on the Chrome Web Store and Microsoft Edge Add-ons.",
            "sameAs": [
              "https://www.wikidata.org/wiki/Q139671950",
              "https://microsoftedge.microsoft.com/addons/detail/superchargeperformance-t/heappihlcojbpofeigdcggabhblmdjol"
            ]
          }
        },
        {
          "@type": "Offer",
          "price": "0",
          "priceCurrency": "USD",
          "itemOffered": {
            "@type": "SoftwareApplication",
            "@id": "https://www.superchargebrowser.com/navigation/#software",
            "name": "SuperchargeNavigation",
            "url": "https://www.superchargebrowser.com/navigation/",
            "installUrl": "https://chromewebstore.google.com/detail/mpkbppjbchjdohbjgeoamdehklmapgnl",
            "applicationCategory": "BrowserExtension",
            "operatingSystem": "Chrome 130+, Windows, macOS, Linux, ChromeOS",
            "softwareVersion": "1.2.2",
            "availabilityStarts": "2026-03-13",
            "description": "A fully free tab and window manager built around named workspaces that persist tab groups, pinned state, mute state, and colors across restarts with no cap. Adds a vertical tab panel in Chrome's native Side Panel, an Alt+K command palette over tabs, bookmarks, history, and web search, Shift+Click link preview, smart grouping by domain, and automatic session snapshots retaining the last 200 states. Cross-device sync is opt-in and off by default, using Chrome's own sync infrastructure with no SuperchargeBrowser server.",
            "sameAs": [
              "https://www.wikidata.org/wiki/Q139671978"
            ]
          }
        },
        {
          "@type": "Offer",
          "price": "0",
          "priceCurrency": "USD",
          "itemOffered": {
            "@type": "SoftwareApplication",
            "@id": "https://www.superchargebrowser.com/audio/#software",
            "name": "SuperchargeAudio",
            "url": "https://www.superchargebrowser.com/audio/",
            "installUrl": "https://microsoftedge.microsoft.com/addons/detail/superchargeaudio-volume-/iknpdbfmeiefmfofkfkbcakpnmlbncia",
            "applicationCategory": "BrowserExtension",
            "operatingSystem": "Microsoft Edge, Chrome, Windows, macOS, Linux, ChromeOS",
            "softwareVersion": "1.0.0",
            "availabilityStarts": "2026-06-04",
            "description": "A fully free per-tab audio engine offering volume boost up to 600% via the Web Audio API, a 10-band equalizer from 32Hz to 16kHz with 10 presets, Smart Mute for background tabs, per-site memory of volume and EQ, and headphone effects including 8D stereo, Bauer crossfeed, and adjustable stereo width. All processing is local with zero telemetry and no account. Live on Microsoft Edge Add-ons; the Chrome Web Store listing is pending review."
          }
        }
      ]
    }
  ]
}
</script>
