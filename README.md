# FFmpeg Notes 🧪🎬

A collection of notes, tips, and command examples for working with [FFmpeg](https://ffmpeg.org/), a powerful tool for processing audio and video files.

## 📂 Structure

This repo contains categorized notes and snippets for various FFmpeg use cases, including:

- 📹 Video conversion
- 🔊 Audio manipulation
- 🎞️ Cutting & trimming
- 🖼️ Image sequences
- 🎚️ Filters & effects
- 🧩 Advanced usage (codecs, containers, metadata, etc.)

## 🛠️ Installation

To use FFmpeg, you need to have it installed on your system:

### macOS (Homebrew)

```bash
brew install ffmpeg
```

### Ubuntu/Debian

```bash
sudo apt update
sudo apt install ffmpeg
```

### Windows

- Download from [FFmpeg.org download page](https://ffmpeg.org/download.html)
- Extract and add FFmpeg to your system PATH

## 🔧 Basic Usage Examples

### Convert a video to MP4

```bash
ffmpeg -i input.avi output.mp4
```

### Extract audio from video

```bash
ffmpeg -i video.mp4 -q:a 0 -map a audio.mp3
```

### Trim a video (from 00:00:30 to 00:01:00)

```bash
ffmpeg -i input.mp4 -ss 00:00:30 -to 00:01:00 -c copy trimmed.mp4
```

### Resize a video

```bash
ffmpeg -i input.mp4 -vf "scale=1280:720" output_720p.mp4
```

## 📚 Resources

- [FFmpeg Documentation](https://ffmpeg.org/documentation.html)
- [FFmpeg Wiki](https://trac.ffmpeg.org/)
- [Stack Overflow FFmpeg Questions](https://stackoverflow.com/questions/tagged/ffmpeg)

## ✅ TODO

- [ ] Add more codec-specific examples
- [ ] Include common error fixes
- [ ] Batch processing scripts
- [ ] Use cases for live streaming

## 📬 Contributing

Feel free to submit a PR with useful commands, or open an issue if something needs clarification.

---

> “FFmpeg is not just a tool, it's a toolbox.”  
> — Probably someone wise.
