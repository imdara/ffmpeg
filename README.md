# Video Conversion with FFmpeg

FFmpeg is a versatile tool for converting videos between different formats, codecs, and qualities. This guide provides commands and examples to help you efficiently convert videos.

---

## Why Use FFmpeg for Video Conversion?

- **Wide Format Support**: Convert videos between almost any format, such as MP4, AVI, MKV, MOV, etc.
- **Customizable Options**: Adjust resolution, bitrate, frame rate, and more.
- **Hardware Acceleration**: Leverage GPU for faster conversions.
- **Batch Processing**: Automate multiple conversions at once.

---

## Common Video Conversion Commands

### 1. **Basic Format Conversion**

Convert a video from one format to another:

```bash
ffmpeg -i input.mp4 output.avi
```

- `input.mp4`: The source video file.
- `output.avi`: The converted video file.

### 2. **Specify Video Codec**

Choose a specific codec for the output video:

```bash
ffmpeg -i input.mp4 -vcodec libx264 output.mp4
```

- `-vcodec libx264`: Specifies the H.264 video codec for high compatibility.

### 3. **Change Resolution**

Resize the video to a specific resolution:

```bash
ffmpeg -i input.mp4 -vf scale=1280:720 output.mp4
```

- `scale=1280:720`: Sets the resolution to 720p.

### 4. **Adjust Bitrate**

Reduce video size by setting a specific bitrate:

```bash
ffmpeg -i input.mp4 -b:v 1000k output.mp4
```

- `-b:v 1000k`: Sets the video bitrate to 1000 kbps.

### 5. **Convert Audio and Video Codecs**

Change both the video and audio codecs:

```bash
ffmpeg -i input.mkv -vcodec libx265 -acodec aac output.mp4
```

- `-vcodec libx265`: Uses the H.265 codec for better compression.
- `-acodec aac`: Sets the audio codec to AAC.

### 6. **Frame Rate Conversion**

Change the frame rate of a video:

```bash
ffmpeg -i input.mp4 -r 30 output.mp4
```

- `-r 30`: Sets the frame rate to 30 FPS.

---

## HE-AAC Audio Codec

HE-AAC (High-Efficiency AAC) is an advanced audio codec known for delivering high-quality audio at lower bitrates. Here’s how you can use it in FFmpeg:

### Convert Audio to HE-AAC

```bash
ffmpeg -i input.mp4 -c:a libfdk_aac -b:a 64k output.mp4
```

- `-c:a libfdk_aac`: Specifies the HE-AAC codec (via the Fraunhofer FDK AAC library).
- `-b:a 64k`: Sets the audio bitrate to 64 kbps (adjustable as needed).

> **Note**: The `libfdk_aac` encoder provides excellent HE-AAC quality but must be enabled when FFmpeg is built. If unavailable, you can use `aac` as a fallback:

```bash
ffmpeg -i input.mp4 -c:a aac -b:a 64k output.mp4
```

---

## Advanced Conversion Features

### Convert Video for a Specific Device

Optimize videos for playback on specific devices:

```bash
ffmpeg -i input.mp4 -preset ultrafast -tune zerolatency output.mp4
```

### Extract Video Stream Only

Remove audio and keep just the video stream:

```bash
ffmpeg -i input.mp4 -an output.mp4
```

### Convert Videos in Batch

Process multiple videos with a single command:

```bash
for file in *.mkv; do ffmpeg -i "$file" "${file%.mkv}.mp4"; done
```

### Convert to a Specific Aspect Ratio

Force a specific aspect ratio for the output video:

```bash
ffmpeg -i input.mp4 -vf "scale=1280:720,setsar=1:1" output.mp4
```

---

## Hardware Acceleration for Faster Conversions

Leverage GPU-based encoders (if available) for faster processing.

### Using NVIDIA GPU:

```bash
ffmpeg -i input.mp4 -c:v h264_nvenc -preset fast output.mp4
```

### Using Intel Quick Sync:

```bash
ffmpeg -i input.mp4 -c:v h264_qsv output.mp4
```

---

## Troubleshooting Video Conversion

- **Output Video Quality is Low**: Increase bitrate or use a higher-quality codec like H.264.
- **Conversion is Slow**: Use hardware acceleration or a faster preset (`-preset ultrafast`).
- **File Size is Large**: Reduce resolution, bitrate, or use efficient codecs like H.265.

---

## Resources

- [FFmpeg Official Documentation](https://ffmpeg.org/documentation.html)
- [Codec Guides](https://trac.ffmpeg.org/wiki/Encode/H.264)
- [HE-AAC Overview](https://en.wikipedia.org/wiki/High-Efficiency_Advanced_Audio_Coding)

---

Feel free to use this updated README.md file for the "video-conversion" branch. Let me know if you’d like further refinements or additions! 🚀
