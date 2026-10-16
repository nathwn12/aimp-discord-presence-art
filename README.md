<h1 align="center">aimp-discord-presence-art</h1>
<p align="center"><strong>Cover art for the AIMP Discord Rich Presence - art only, no code.</strong></p>

## What it is

Public cover-art host for the AIMP Discord Rich Presence. Files under `covers/` are consumed over raw.githubusercontent by the presence client. This repo is art only and contains no code.

Layout: `covers/` holds one cover image per track, named after the SHA-256 of the source art plus `.jpg` — 145 covers today, alongside a `black.png` used when no track art exists; `assets/` holds the repo artwork (`icon.svg` for the header, `signature.svg` for the house footer); `LICENSE` is MIT. Every entry is a plain image blob, so nothing sits between the URL and the bytes: no download step, no build, no manifest.

The presence client builds one raw URL per track and requests it directly:

```text
https://raw.githubusercontent.com/nathwn12/aimp-discord-presence-art/main/covers/<sha256>.jpg
```

Because the file name is content-addressed, adding art never changes the URL of art that already ships. Verified live against the largest shipped cover (`covers/c945382f98e2d4969eea03c82888857c870b325fd235f072f7e445237168399f.jpg`): the request returned `HTTP/1.1 200 OK` with `Content-Type: image/jpeg` and `Content-Length: 158391` — matching the checked-in file byte for byte — plus an open CORS header (`Access-Control-Allow-Origin: *`) so the presence can fetch the art from its own origin.

## License

MIT — see [LICENSE](LICENSE).

<!-- nathwn12 house footer: identical in every repo. Do not edit. -->
<p align="center">
  <a href="https://github.com/nathwn12"><img src="assets/signature.svg" width="96" alt="nathwn12" /></a>
</p>
<p align="center">
  <sub>Built by <a href="https://github.com/nathwn12">nathwn12</a> · <a href="https://github.com/nathwn12?tab=repositories">All projects</a></sub>
</p>
