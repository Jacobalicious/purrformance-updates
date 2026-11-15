<div align="center">

# 📣 Purrformance – Updates

**The small public noticeboard that every copy of the Purrformance emote mod checks at start-up.**

![JSON](https://img.shields.io/badge/format-JSON-000000?style=for-the-badge&logo=json&logoColor=white)
![Fabric](https://img.shields.io/badge/Fabric-Minecraft%2026.2-62B47A?style=for-the-badge)
![Latest](https://img.shields.io/badge/latest-1.0.0-ff6eb4?style=for-the-badge)

</div>

## ✨ What this is

[Purrformance](https://github.com/Jacobalicious/purrformance) is a Minecraft mod that brings real
motion-capture dances and emotes to the player. The mod itself is private; this repository is
public because the mod must be able to read one file from it without a password:
[`gate.json`](gate.json).

There is nothing secret in here. It is a public noticeboard, and it is meant to be read.

## 🚀 What `gate.json` answers

- **What version is current** – anybody running an older one is told so in chat, once, shortly
  after they join a world.
- **What to tell them** – one line of text, plus a link to where to get the new version.
- **Which accounts the mod refuses to run for** – by Minecraft account id (lasts) or by name
  (stops working if they rename). Removing an entry lets them back in next time they start the game.

## 🛠️ How it works

| Step | What happens |
| --- | --- |
| Start-up | The mod fetches the raw file from GitHub once, asking for a fresh (non-cached) copy |
| Update | Editing the file *is* the deployment – a commit or a click in GitHub's web editor; it is live within a minute or two |
| Offline | **It fails open.** No internet, GitHub down, repository moved: the mod simply plays as normal |
| Remembered | The last answer is cached on the player's disk and signed, so unplugging the network does not undo a block |

Failing open is deliberate: a check that fails closed turns every outage into everybody's mod
breaking at once, for a problem none of them had.

## 📦 Posting an update

1. Release the new mod build and put it where players can download it.
2. Set `latest` in `gate.json` to the new version number (compared number by number: `1.0.0 < 1.0.1 < 1.1.0`).
3. Optionally edit `message` and `url`. Commit. Done.

Every field is optional; an empty `{}` means "current version, nobody blocked, carry on".
The file explains its own fields in its `_comment` block.

## 🧰 Built with

- Plain JSON served by GitHub's raw file hosting
- Read by the mod's update check (Java, Fabric)
