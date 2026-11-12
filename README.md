# Exile capes

Capes and member list for Exile Client (Forge 1.7.10), read by the client's Cosmetics menu and by the launcher.

| Path | What it is |
|---|---|
| `capes/` | the capes. Files at the root go in the EXILE folder; every subfolder is a folder in the menu. |
| `members.txt` | one member per line: `name` or `name=cape`. |
| `identities.properties` | Mojang UUID per member (`uuid=name[,old name]`), for skins and renamed accounts. |
| `manifest.json` | every file with size and SHA-1: the client only downloads files the manifest lists. |

The easiest way to change it is the dashboard (the `exile-capes-admin` worker): it adds members, uploads capes and
rebuilds the manifest.

By hand: after changing `capes/`, `members.txt` or `identities.properties`, rebuild the manifest (from exile-client):

```
py -I source/exile-client/tools/capes/make_manifest.py <this folder>
```

then commit and push.

Cape format: a 2:1 PNG whose width is a multiple of 64 (64×32 … 2048×1024; the client draws at most 512 wide).
Animations: a vertical stack of whole capes in one PNG, or `id.png` + `id.anim.png` (a grid of front-face frames)
with an optional `id.txt` frame order.

The Minecon, OkenAaa, Pack Oken and Ufficiali folders came with the EXILE Lunar package and are stored here at
512 px wide (`tools/capes/BundleCapes.java` in exile-client).
