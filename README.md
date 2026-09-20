# purrformance-updates

The file every copy of [Purrformance](https://github.com/Jacobalicious/purrformance)
reads once at start-up. The mod itself is private; this is not, because the mod
has to be able to fetch it without a token.

`gate.json` answers three questions:

- **What version is current.** Anybody running an older one is told so in chat,
  once, shortly after they join a world.
- **What to tell them.** One line, plus a link.
- **Which accounts the mod refuses to run for.** By uuid, or by name.

Editing it is a commit to this repository — or a click in GitHub's web editor.
Raw serves the change within a minute or two.

There is nothing secret in here. It is a public noticeboard, and it is meant to
be read.

## It fails open

If the mod cannot reach this file — no internet, this repository moved, GitHub
down — the mod plays as normal. That is on purpose: a check that fails closed
turns every outage into everybody's mod breaking at once, for a problem none of
them had. What survives an outage is the *last* answer, cached on the player's
disk and signed, so once somebody has been told no, pulling the network cable
does not undo it.
