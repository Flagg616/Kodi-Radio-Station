# Kodi Radio Station

Kodi Radio Station is a self-contained Kodi service add-on that turns the music currently playing in Kodi into a simple web radio experience.

It provides a browser-based now-playing page, a compact embeddable player, remote playback controls, album information, artwork, and a live MP3 stream that can be opened in external players such as Winamp and VLC.

It does not require Icecast, DarkIce, FFmpeg, or a separate streaming server.

## Features

• Responsive web-based now-playing page  
• Compact player designed for embedding in websites or dashboards  
• Current album artwork  
• Song title  
• Artist  
• Album  
• Genre  
• Playback progress and elapsed time  
• Browser playback of the current Kodi audio source  
• Live MP3 stream for external players  
• Winamp-compatible PLS playlist  
• M3U playlist support  
• ICY now-playing metadata  
• Password-protected administration page  
• Previous track  
• Play / pause  
• Stop  
• Next track  
• Seek control  
• Volume control  
• Mute  
• Shuffle  
• Repeat all  
• Repeat one  
• Repeat off  
• Album information links using TheAudioDB  
• Reverse-proxy-aware client handling  
• Configurable station name  
• Configurable HTTP port  
• Configurable bind address  
• Configurable administrator credentials  
• Cross-platform Kodi/Python implementation  
• No additional streaming daemon required  

## Typical Use

Once installed and running, Kodi Radio Station starts a small HTTP server inside Kodi.

If the Kodi machine is available at:

```text
http://192.168.0.199:8000
```

the main web player is available at:

```text
http://192.168.0.199:8000/
```

The compact player is:

```text
http://192.168.0.199:8000/compact
```

The administration page is:

```text
http://192.168.0.199:8000/admin
```

## External Players

For Winamp, open:

```text
http://192.168.0.199:8000/winamp.pls
```

For VLC or other M3U-compatible players:

```text
http://192.168.0.199:8000/winamp.m3u
```

The direct live MP3 stream is:

```text
http://192.168.0.199:8000/live.mp3
```

The external-player stream follows Kodi playback and carries ICY metadata in the form:

```text
StationTitle-ArtistName-SongName
```

The live stream is MP3-only and does not transcode source audio.

## Web Player

The full web player shows the current Kodi playback state and artwork and updates automatically as Kodi changes tracks.

It includes:

• Artwork  
• Station name  
• Song title  
• Artist  
• Album  
• Genre  
• Timing  
• Progress  
• Playback control  

The browser player is separate from the Winamp/VLC live stream and is designed for normal web use.

## Compact Player

The compact player is intended for embedding into another website or dashboard.

Example:

```html
<iframe
    src="http://SERVER-IP:PORT/compact"
    title="Kodi Radio Station"
    style="width:100%;height:112px;border:0;"
    allow="autoplay">
</iframe>
```

The compact player provides the same essential now-playing information in a much smaller layout.

## Administration

The administration page provides remote control of Kodi playback.

Available controls include:

• Previous  
• Play / pause  
• Stop  
• Next  
• Seek  
• Mute  
• Shuffle  
• Repeat all  
• Repeat song  
• Repeat off  

The administrator username and password are configurable in the add-on settings.

## Album Information

Kodi Radio Station can link the currently playing album to TheAudioDB.

No MusicBrainz fallback is used.

If TheAudioDB cannot resolve the album, the add-on simply reports that no album information was found.

## Reverse Proxy Support

Kodi Radio Station can be placed behind a reverse proxy and used with a normal HTTPS hostname.

For example:

```text
https://radio.example.com/
```

forwarding internally to:

```text
http://127.0.0.1:8000/
```

The add-on supports trusted reverse-proxy addresses and forwarded client information while avoiding blindly trusting proxy headers from arbitrary clients.

## Main Endpoints

```text
/                  Full web player
/compact           Compact embeddable player
/admin             Administration page
/api/status        Current Kodi playback state
/api/health        Service health
/art/current       Current album artwork
/stream            Browser-oriented audio stream
/album-info        TheAudioDB album lookup
/live.mp3          Live MP3 stream
/winamp.pls        Winamp playlist
/winamp.m3u        M3U playlist
/api/winamp-debug  Live-stream diagnostic information
```

## Requirements

• Kodi  
• Python support provided by Kodi  
• MP3 source audio for the external live MP3 stream  
• Network access to the configured HTTP port  

No external media server or transcoding software is required.

## Intended Use

Kodi Radio Station is useful for:

• Listening to Kodi playback from another computer  
• Displaying now-playing information on a local website  
• Embedding a small player in a dashboard  
• Controlling Kodi remotely from a browser  
• Feeding Kodi playback into Winamp, VLC, or similar players  
• Publishing a private household or LAN radio-style interface  
• Placing Kodi playback behind a reverse-proxied HTTPS hostname  

The add-on is designed to remain lightweight, self-contained, and easy to deploy while keeping Kodi as the source of playback and control.

