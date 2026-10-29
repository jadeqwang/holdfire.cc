# holdfire.cc

The watch site for **Hold Fire**, a music video by Jade Wang about counting into the dark (one, one, two, three, five, eight), the dark forest, and the running list of nuclear near-misses humanity survived because someone held their fire. One static page: the film, the lyrics, the near-misses that scroll past in the film, and notes on the lines.

Hold Fire. Song and lyrics by Jade Wang.

**Status: draft.** The film is not out yet. The near-miss list is a first pass at what scrolls past in the film. Check it against the film's actual list. Each entry has had one fact-check pass against Wikipedia, the National Security Archive and the sources in the page's Sources section.

## The film

The video id (the part after `watch?v=`) goes in the one constant near the top of the `<script>` in `index.html`:

```js
const YOUTUBE_ID = '';
```

While it is empty, the frame shows the poster (an inline SVG) with "Film coming soon", and the lyrics are plain text. Once it is set, the page loads the YouTube player (privacy-enhanced, youtube-nocookie.com).

To make the lyrics play-from-here buttons that light up as they are sung, give every lyric `<button class="ln">` a `data-t0` and `data-t1` (seconds into the video), as on orbitalsunrise.cc. Until every line has both, the lyrics stay plain text.

No video or audio files are kept in this repo.

## The near-misses

Each entry in `#events` is one `<li class="ev">` with a `data-kind` of `alarm`, `accident` or `crisis`, which drives the filter buttons. Entries named in the lyrics also carry the `lyric-ev` class. The tally and the odds dial count the entries, so adding or removing one needs no other change.

## Deploy

It is a plain static site: `index.html`, `favicon.*` and `img/`, no build step.

Cloudflare Pages: connect this repo, framework preset "None", build command empty, build output directory `/`. Any other static host works the same way: serve the repo root.

To preview locally: `python3 -m http.server` in the repo root, then open http://localhost:8000.
