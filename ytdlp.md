# yt-dlp commands

You can place output options in a separate `yt-dlp.conf` file next to `yt-dlp.exe`. Lines beginning with `#` are comments.

---

Simplest way to download a video as mp4:

`--merge-output-format mp4 -o "<location>\%(uploader)s - %(title)s.%(ext)s"`

To download the 1080p version of a video:

`-f "bestvideo[height=1080]+bestaudio"`

---

For music:

`-o "%(artist|uploader,NA)s - %(track|title,NA)s.mp3" -f bestaudio -x --audio-format mp3`
