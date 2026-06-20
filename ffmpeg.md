# ffmpeg commands

Most common task: make a video file smaller without losing quality.

`ffmpeg -i input.mp4 -c:v libx264 -crf 22 -preset veryslow -c:a aac -b:a 128k -ar 44100 output.mp4`

- `crf` - Constant Rate Factor (0 - 51 range, 18 - 23 is the best for h.264)
- `preset` - controls encoding speed
- Example (25 min. mp4): 3Gb file from Resolve (bitrate set to 16000) &rarr; 930Mb video witout any noticable change in visual quality

---

This came in handy when I was editing a 4K 60fps h.265 encoded video. Creates a much larger file but is still fine for editing on a potato laptop. Transcodes the highly compressed h.264 to DNxHR.

`ffmpeg -i input_4k_60.mp4 -c:v dnxhd -profile:v dnxhr_lb -c:a pcm_s24le output.mov`

If filesize is no issue use `dnxhr_hq` (High Quality) instead of `dnxhr_lb` (Low Bitrate).

Audio is also uncompressed with `pcm_s24le`.

- `pcm` - Pulse Code Modulation
- `s24` - signed, 24-bit
- `le` - Little Endian
