# SmDeltArt Fever Audio

Static audio companion for [topic.earth](https://github.com/SmDeltArt/topic.earth).

This repository is intended to host generated read-message audio outside the main app repository when batches become large. The app can still try local files first, then fall back to this repository through `TOPIC_EARTH_AUDIO_BASE_URL`.

## Layout

```text
assets/audio/read-messages/
  manifest.json
  tracking.json
  *.webm
```

## Public Base URL

For raw GitHub hosting, use:

```text
https://raw.githubusercontent.com/SmDeltArt/fever/main/assets/audio/read-messages
```

For jsDelivr CDN hosting, use:

```text
https://cdn.jsdelivr.net/gh/SmDeltArt/fever@main/assets/audio/read-messages
```

## Current Seed

The initial seed contains the generated tutorial and UI `.webm` recordings currently available from `topic.earth`. Fever loop recordings can be generated later from the `topic.earth` manifest and copied into the same folder.

## Generate From topic.earth

From the `topic.earth` repository:

```powershell
$env:OPENAI_API_KEY = "..."
tools\record-read-audio.ps1 -Lg en,fr,nl,de,ru,uk,zh,hi -Ids fever-loop-best-1975-short-en
```

For a full Fever batch, use the manifest tag:

```powershell
node tools\generate-read-audio.mjs --tag=fever-loop
```

Then copy the generated `.webm` files into this repository and push.
