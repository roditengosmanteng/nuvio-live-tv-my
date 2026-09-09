# nuvio-live-tv-my

Nuvio/Stremio-protocol addon exposing free-to-air Malaysian live TV channels as a
static catalog, for use with [NuvioTV](https://github.com/NuvioMedia/NuvioTV).

Addon base URL:
`https://raw.githubusercontent.com/roditengosmanteng/nuvio-live-tv-my/main`

## Scope

Only channels that are (a) genuinely free-to-air / permanently free, and (b) whose
stream URL traces back to the broadcaster's own official CDN infrastructure:

- **RTM** (government broadcaster): TV1, TV2, TV6, Berita RTM, RTM Parlimen (Dewan
  Rakyat & Dewan Negara) - served from RTM's own CloudFront distribution
  (`d25tgymtnqzu8s.cloudfront.net`), same infrastructure used by RTM's own
  `rtmklik.rtm.gov.my` player.
- **Media Prima / Tonton** (commercial FTA broadcaster): TV3, 8TV, TV9, DidikTV KPM -
  served from Tonton's own Akamai CDN (`tonton-live-ssai.akamaized.net`).

**Deliberately excluded** (see the owning project's task notes for full reasoning):
- RTM Sukan and RTM Okey - these use Axinom DRM with a live per-session token
  exchange (`rtm-player.glueapi.io`), which cannot be expressed as a static stream
  URL. Needs a native resolver.
- Any Astro/NJOI/sooka channel - Astro's own free FAST streaming site (sooka.my,
  operated by MEASAT Broadcast Network Systems Sdn Bhd) requires account
  registration/login before it reveals any playable stream URL, confirmed by
  live testing. Not expressible as a static URL either.
- Astro's temporary 30th-anniversary promo channels ("Astro 30", "ANIPLUS") -
  time-limited free access, not a permanent FTA offering.
- Any third-party proxy/relay (e.g. personal Cloudflare Workers proxies) that
  merely fronts a broadcaster's stream rather than being the broadcaster's own
  infrastructure.

This repo only points at already-public official broadcast stream URLs - it hosts
no media itself.
