# Spotify HUD (Fabric, Minecraft 1.21.11)

Zeigt den Song, den Spotify gerade spielt, als Karte im Spiel: Cover, Titel, Interpret, Fortschrittsbalken
und synchronisierte Lyrics. Kein Spotify-Login nötig, der Mod liest die Media-Session deines Betriebssystems.

- **Windows:** Windows-Media-Session (Fallback: Spotify-Fenstertitel)
- **Linux:** MPRIS über `dbus-send` (muss installiert sein, bei den meisten Distros ist es das)
- **macOS:** `osascript` (Spotify-App)
- Lyrics kommen von [LRCLIB](https://lrclib.net), werden lokal in `config/spotifyhud/lyrics-cache` zwischengespeichert
  und nur abgefragt, wenn `online` an ist.

## Bauen

Voraussetzung: JDK 21.

```
./gradlew build          # Windows: gradlew.bat build
```

Die fertige Datei liegt in `build/libs/spotifyhud-1.0.0.jar` (**nicht** die `-sources.jar`).
Sie kommt in den `mods`-Ordner, zusammen mit der **Fabric API**.

## Befehle (im Spiel, im Chat)

| Befehl | Wirkung |
|---|---|
| `/spotifyhud` | Status und Befehlsliste |
| `/spotifyhud toggle` | HUD an/aus |
| `/spotifyhud corner top_left\|top_right\|bottom_left\|bottom_right` | Ecke |
| `/spotifyhud offset <x> <y>` | Abstand zur Ecke |
| `/spotifyhud scale <0.5-3>` | Größe |
| `/spotifyhud width <120-400>` | Breite der Karte |
| `/spotifyhud opacity <0-100>` | Hintergrund-Deckkraft |
| `/spotifyhud lyriclines <1-3>` | Anzahl Lyrics-Zeilen |
| `/spotifyhud set art\|artist\|progress\|lyrics\|scroll\|idle\|online <true\|false>` | Optionen |
| `/spotifyhud play\|next\|prev` | Wiedergabe steuern |
| `/spotifyhud reload` | `config/spotifyhud.json` neu laden |

## Falls der Build meckert

Der Code wurde gegen die echten Signaturen von Fabric API 0.141.6 / Minecraft 1.21.11 (Mojang-Mappings)
geschrieben, aber nicht mit Gradle gebaut. Die beiden Stellen, die am ehesten abweichen können, sind
in `ArtTexture.java`: `NativeImage.setPixel(x, y, argb)` und `DynamicTexture`/`TextureManager.register/release`.
Sind die Cover-Farben vertauscht (rot/blau), tausche `r` und `b` in der Zeile mit `setPixel`.

## Lizenz

GPL-3.0-only, siehe `LICENSE` und `NOTICE.md`.
