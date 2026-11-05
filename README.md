# uBlock-YT

<p align="center">
  <img src="info/a1.png" alt="uBlock-YT Banner" width="100%">
</p>

<p align="center">
  <a href="https://github.com/a111et/ublock-yt/blob/main/README-RU.md"><img src="https://img.shields.io/badge/Russian-README-blue?style=for-the-badge&logo=github" alt="English README"></a>
  <a href="https://github.com/a111et/ublock-yt/stargazers"><img src="https://img.shields.io/github/stars/a111et/ublock-yt?style=for-the-badge&logo=github&color=333" alt="Звезды"></a>
  <a href="https://github.com/a111et/ublock-yt/issues"><img src="https://img.shields.io/github/issues/a111et/ublock-yt?style=for-the-badge&logo=github&color=666" alt="Проблемы"></a>
  <a href="https://subscribe.adblockplus.org/?location=https://raw.githubusercontent.com/a111et/ublock-yt/refs/heads/main/ublock-YT-Clinin.txt&title=uBlock-YT%20Filters"><img src="https://img.shields.io/badge/Subscribe-Filter%20List-red?style=for-the-badge&logo=ublockorigin" alt="Подписаться"></a>
</p>

---

## 🎯 Project Goal
The main objective of this project is to make YouTube cleaner, less cluttered, and more enjoyable to use. It focuses on removing distracting elements, algorithmic clutter, and layout anomalies. 

*Planned future updates:* Custom user themes (skins) and tailored user scripts to further enhance or customize the layout.

## 📦 What is this?
This repository contains a curated collection of custom **uBlock Origin** rules specifically crafted for YouTube. It targets and eliminates irritating interface elements, clutter, and layout shifts that remain after standard ad blocking.

> [!TIP]
> Thank you so much for using my filters! If you notice any bugs, layout breaks, or have improvements, please open an Issue or a Pull Request with your solution. I will gladly merge it into the main list. Enjoy a cleaner YouTube!

---

## 🚀 Quick Setup & Installation

### Option 1: Automatic Subscription (Recommended)
Click the badge below to automatically import and subscribe to the filter list in uBlock Origin:

[![Subscribe to Filter List](https://img.shields.io/badge/Click%20to%20Subscribe-uBlock%20Origin-red?style=for-the-badge&logo=ublockorigin)](https://subscribe.adblockplus.org/?location=https%3A%2F%2Fraw.githubusercontent.com%2Fa111et%2Fublock-yt%2Frefs%2Fheads%2Fmain%2Fublock-YT-Clinin.txt&title=uBlock-YT+Filters)

### Option 2: Manual Import
1. Copy the raw filter link: `https://raw.githubusercontent.com/a111et/ublock-yt/refs/heads/main/ublock-YT-Clinin.txt`
2. Open **uBlock Origin Dashboard** -> **Filter lists** tab.
3. Scroll down to the bottom, check **Import...**, paste the link, and click **Apply changes**.

---

## 🛠️ Included Rules Breakdown

### 1. Enhanced Grid Layout (4 Videos Per Row)
Forces the YouTube homepage to display exactly 4 videos per row for better visibility and a less cramped look.

![Layout Preview](info/a1.png)

```adblock
youtube.com##ytd-rich-grid-renderer:style(--ytd-rich-grid-items-per-row: 4 !important;)
youtube.com##ytd-rich-grid-renderer:style(--ytd-rich-grid-posts-per-row: 4 !important;)
youtube.com##ytd-two-column-browse-results-renderer.grid-6-columns:style(width: 100% !important;)
youtube.com##ytd-two-column-browse-results-renderer.grid:not(.grid-disabled):style(max-width: 100% !important;)
youtube.com##ytd-rich-grid-renderer, html:style(--ytd-rich-grid-slim-items-per-row: 7 !important;)
youtube.com##ytd-rich-grid-renderer, html:style(--ytd-rich-grid-game-cards-per-row: 7 !important;)
youtube.com##+js(set-attr, ytd-rich-shelf-renderer, is-show-more-hidden)
youtube.com##+js(ra, hidden, ytd-rich-item-renderer, stay)

```

### 2. Fix Empty Placeholder Blocks

Removes the empty blank spaces and broken container blocks that appear on the homepage after ads are hidden.

![alt text](info/a2.jpg)

```adblock
youtube.com##ytd-rich-section-renderer.style-scope.ytd-rich-grid-renderer

```

### 3. Total Shorts Blockout

Completely removes YouTube Shorts from the Desktop and Mobile interfaces, including the sidebar, homepage shelves, subscriptions, search results, and watch history.

```adblock
! === Shorts Removal (Desktop) ===
! YT - Homepage and Subscriptions (Grid View) - Hide the Shorts section
youtube.com##[is-shorts]
! YT - Menu - Hide the Shorts button
www.youtube.com###guide [title="Shorts"], .ytd-mini-guide-entry-renderer[title="Shorts"]
! YT - Search - Hide Shorts
www.youtube.com##ytd-search ytd-video-renderer:has([overlay-style="SHORTS"],[href^="/shorts/"])
! YT - Search, Channels, Subscriptions (List View) and Sidebar/Below Player Recommendations - Hide the Shorts sections
www.youtube.com##ytd-reel-shelf-renderer
! YT - Channels - Hide the Shorts tab
www.youtube.com##[tab-title="Shorts"]
! YT - Subscriptions - Hide Shorts - Grid View
www.youtube.com##ytd-browse[page-subtype="subscriptions"] ytd-grid-video-renderer:has([overlay-style="SHORTS"],[href^="/shorts/"])
! YT - Subscriptions - Hide Shorts - List View
www.youtube.com##ytd-browse[page-subtype="subscriptions"] ytd-video-renderer:has([overlay-style="SHORTS"],[href^="/shorts/"])
! YT - Subscriptions - New Layout - Hide Shorts
www.youtube.com##ytd-browse[page-subtype="subscriptions"] ytd-rich-item-renderer:has([overlay-style="SHORTS"],[href^="/shorts/"])
! YT - Sidebar - Hide Shorts
www.youtube.com###related :is(ytd-compact-video-renderer,yt-lockup-view-model):has([overlay-style="SHORTS"],[href^="/shorts/"])
! YT - History - Hide Shorts
www.youtube.com##ytd-item-section-renderer[page-subtype]:has(>#contents>[is-history]>#dismissible>ytd-thumbnail>#thumbnail[href^="/shorts/"])

! === Shorts Removal (Mobile) ===
! YT Mobile - Hide the Shorts Menu button
m.youtube.com##ytm-pivot-bar-item-renderer:has(>.pivot-shorts)
! YT Mobile - Hide the Shorts sections
m.youtube.com##:is(ytm-rich-section-renderer,grid-shelf-view-model):has([href^="/shorts/"])
! YT Mobile - Search - Hide Shorts
m.youtube.com##ytm-search ytm-video-with-context-renderer:has([href^="/shorts/"])
! YT Mobile - Channels - Hide the Shorts button
m.youtube.com##[tab-title="Shorts"]
! YT Mobile - History - Hide Shorts
m.youtube.com##[tab-identifier="FEhistory"] ytm-compact-video-renderer:has(>div>a[href^="/shorts/"])
```

### 4. Hide Community Posts on Homepage

Blocks text and image community posts from crowding your main video feed.

```adblock
! === Hide Community Posts ===
! YT Homepage - Hide the Posts Section
www.youtube.com##ytd-browse[page-subtype="home"] ytd-rich-section-renderer:has(ytd-rich-item-renderer[is-post])
! YT Homepage - Hide Posts
www.youtube.com##ytd-browse[page-subtype="home"] ytd-rich-item-renderer[is-post]
```

### 5. Purged Search Results

Restores the search results page to a classic look, showing **only actual videos, channels, and playlists** while hiding suggested shelves, "people also watched", and other algorithm traps.

```adblock
! === Clean Search Results (Videos, Channels, Playlists Only) ===
! YT Search - keep only videos (no shorts)
youtube.com##ytd-search ytd-item-section-renderer>#contents>:is(:not(ytd-video-renderer,yt-showing-results-for-renderer,[icon-name="promo-full-height:EMPTY_SEARCH"]),ytd-video-renderer:has([aria-label="Shorts"])),ytd-secondary-search-container-renderer

! YT Search - keep only videos (no shorts) and channels
youtube.com##ytd-search ytd-item-section-renderer>#contents>:is(:not(ytd-video-renderer,ytd-channel-renderer,yt-showing-results-for-renderer,[icon-name="promo-full-height:EMPTY_SEARCH"]),ytd-video-renderer:has([aria-label="Shorts"])),ytd-secondary-search-container-renderer

! YT Search - keep only videos (no shorts), channels and playlists
youtube.com##ytd-search ytd-item-section-renderer>#contents>:is(:not(ytd-video-renderer,ytd-channel-renderer,ytd-playlist-renderer,yt-lockup-view-model,yt-showing-results-for-renderer,[icon-name="promo-full-height:EMPTY_SEARCH"]),ytd-video-renderer:has([aria-label="Shorts"])),ytd-secondary-search-container-renderer
```

### 6. Hide Mixes

Hide Mixes playlists recommendation

```adblock
! YT Home - Hide Mixes
youtube.com##ytd-rich-item-renderer:has([href*="start_radio=1"])
! YT Sidebar - Hide Mixes
youtube.com##ytd-compact-radio-renderer, :is(#related yt-lockup-view-model,ytd-compact-video-renderer):has([href*="&start_radio=1"])
! YT Search- Hide Mixes
youtube.com##ytd-radio-renderer, :is(ytd-search yt-lockup-view-model,ytd-video-renderer[is-search]):has([href*="&start_radio=1"][aria-haspopup])
! YT Player - Hide Mixes in Video End Cards
youtube.com##.ytp-videowall-still[data-is-mix="true"]

! YT Sidebar - Hide "YouTube" (Music) playlists
youtube.com##ytd-compact-playlist-renderer:has([title^="YouTube"])
```


---

## 🔗 Check Out My Other Projects

If you like this project, check out **[Downloader](https://github.com/a111et/Downloader)** — a browser extension that adds quick download buttons for videos and photos into the context menu for many websites, including YouTube.

## 🤝 Credits & References

* Thanks to the community solutions found on the [r/uBlockOrigin Wiki](https://www.reddit.com/r/uBlockOrigin/wiki/solutions/youtube/)
* Developed and maintained by [@a111et](https://github.com/a111et)
