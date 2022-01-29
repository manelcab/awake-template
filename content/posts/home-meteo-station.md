---
title: Home meteo station
subtitle: Metereological station with e-ink display and esp32 devices
category:
  - About Awake
author: Daniel Kelly
date: 2019-07-29T17:30:16.858Z
featureImage: /uploads/purge-css-hero.jpg
---




# Caveats

There are some caveats to Purge CSS especially around dynamically created classes. Since these classes aren't fully fleshed out in the .vue files, Purge CSS doesn't know they exist and therefore will strip out their  corresponding css. The fix is pretty simple though, Purge CSS allows us to whitelist classes that should never be purged whether they are found in the html or not. The whitelisting process is described in full in the [Purge CSS docs](https://www.purgecss.com/whitelisting). You can set the `whitelist` option as well as any other purge css option in `config/build.js`.
Sometimes when dev mode and adding markup that uses classes that have not previously been in use, you must restart dev mode for Purge CSS to pick up on the change. 
