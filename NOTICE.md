# Notice

The code in `src/client/java/dev/spotifyhud/media/` (media session readers, album-art decoding, LRCLIB
lyrics client and parser) and the polling logic in `SpotifyService.java` are derived from
**Anubis Client** by 4ldenz (https://github.com/4ldenz/Anubis-client), licensed under the
GNU General Public License v3.0 (see `LICENSE`).

They were taken from the compiled release (Anubis_Beta_0_9_9_3.jar) with the Vineflower decompiler and then
modified: package renamed to `dev.spotifyhud.media`, identifiers/user agent/cache directory rebranded.

The HUD card rendering (`SpotifyHudElement`, `ArtTexture`), config, commands and entrypoint are new code
written for this mod. This mod as a whole is therefore distributed under GPL-3.0-only; if you redistribute it,
you must keep this notice and provide the source code.
