# ffmpeg commands

Most common task: make a video file smaller without losing quality.

`ffmpeg -i input.mp4 -c:v libx264 -crf 22 -preset veryslow -c:a aac -b:a 128k -ar 44100 output.mp4`

- `crf` - Constant Rate Factor (0 - 51 range, 18 - 23 is the best for h.264)
- `preset` - controls encoding speed to compression ratio. Default is `medium`. Use `slow` or `slower` if `veryslow` takes too long.
- Example: 25 min. 3Gb mp4 video from Resolve (bitrate set to 16000 at exporting) &rarr; 930Mb video witout any noticable change in visual quality
- See [the ffmpeg wiki](https://trac.ffmpeg.org/wiki/Encode/H.264) to learn more about h.264 encoding.

---

If the video will be uploaded to YouTube add `-movflags +faststart` as an output option.

This will move some information (moov atom) to the beginning of the file. It's not required but YouTube ​recommends using it, so they can begin re-encoding before uploads complete.

---

This came in handy when I was editing a 4K 60fps h.265 encoded video. Creates a much larger file but is still fine for editing on a potato laptop. Transcodes the highly compressed h.264 to DNxHR.

`ffmpeg -i input_4k_60.mp4 -c:v dnxhd -profile:v dnxhr_lb -c:a pcm_s24le output.mov`

If filesize is no issue use `dnxhr_hq` (High Quality) instead of `dnxhr_lb` (Low Bitrate).

Audio is also uncompressed with `pcm_s24le`.

- `pcm` - Pulse Code Modulation
- `s24` - signed, 24-bit
- `le` - Little Endian

---

`ffprobe -hide_banner input.mp4`

Quickly check a file's codecs, resolution, bitrates, etc.
