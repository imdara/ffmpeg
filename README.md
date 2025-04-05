# Getting Started with FFmpeg on ARM Windows

FFmpeg is a powerful multimedia framework that can be used on ARM Windows devices, such as laptops running Snapdragon processors. This guide will help you set up FFmpeg and utilize both CPU-based and GPU-based encoding options.

---

## Why Use FFmpeg on ARM Windows?

- **Optimized Builds**: Precompiled binaries are available for ARM Windows, ensuring compatibility and performance.
- **Flexible Encoding**: Choose between CPU-based or GPU-based encoding depending on your needs.
- **Lightweight Processing**: ARM devices are power-efficient, making FFmpeg ideal for multimedia tasks.

---

## Installation on ARM Windows

### 1. **Precompiled FFmpeg Binaries**

The easiest way to set up FFmpeg on ARM Windows is to download precompiled binaries:

- Visit the [tordona/ffmpeg-win-arm64 repository](https://github.com/tordona/ffmpeg-win-arm64).
- Download the appropriate variant (e.g., Essentials or Full).
- Extract the archive to a folder on your device (e.g., `C:\ffmpeg\`).

### 2. **Add FFmpeg to PATH**

To use FFmpeg globally from the command line:

1. Open **Settings** > **System** > **About** > **Advanced system settings**.
2. Click **Environment Variables**.
3. Under **System Variables**, find `Path` and click **Edit**.
4. Add the path to your FFmpeg binaries folder (e.g., `C:\ffmpeg\bin\`).
5. Restart your terminal or system.

### 3. **Verify Installation**

To confirm FFmpeg is installed, open Command Prompt or PowerShell and run:

```bash
ffmpeg -version
```

You should see version details of FFmpeg.

---

## CPU-Based Encoding

### **Basic Video Encoding**

Encode videos using the CPU:

```bash
ffmpeg -i input.mp4 -vcodec libx264 output.mp4
```

- `libx264`: A software-based encoder for H.264, compatible across devices.

### **Adjusting Bitrate**

Set a specific bitrate for video encoding:

```bash
ffmpeg -i input.mp4 -b:v 1000k output.mp4
```

### **Optimizing for Performance**

Use presets to balance speed and quality:

```bash
ffmpeg -i input.mp4 -preset ultrafast -crf 23 output.mp4
```

- `-preset ultrafast`: Prioritizes speed for encoding.
- `-crf 23`: Adjusts video quality (lower values mean better quality).

---

## GPU-Based Encoding

### **Using Adreno GPU**

Leverage Adreno GPUs for hardware-accelerated encoding:

```bash
ffmpeg -i input.mp4 -c:v h264_v4l2m2m -b:v 1000k output.mp4
```

- `h264_v4l2m2m`: Utilizes the Video4Linux2 hardware encoder compatible with Adreno GPUs.
- `-b:v 1000k`: Sets the bitrate to 1000 kbps for optimal performance.

### **DirectX Video Acceleration (DXVA)**

For ARM Windows devices, FFmpeg can use DXVA for hardware acceleration:

```bash
ffmpeg -hwaccel dxva2 -i input.mp4 -c:v h264_nvenc output.mp4
```

- Replace `h264_nvenc` with supported encoders for your device.

---

## When to Use CPU vs. GPU Encoding

- **CPU-Based Encoding**: Ideal for smaller files or when GPU acceleration is unavailable.
- **GPU-Based Encoding**: Recommended for faster processing or larger files, especially if Adreno GPUs are available.

---

## Common Commands on ARM Windows

### **Basic Format Conversion**

Convert a video from one format to another:

```bash
ffmpeg -i input.mp4 output.avi
```

### **Screen Recording**

Capture your screen on an ARM Windows device:

```bash
ffmpeg -f gdigrab -framerate 30 -i desktop output.mp4
```

### **Resizing Videos**

Change the resolution of a video:

```bash
ffmpeg -i input.mp4 -vf scale=1280:720 output.mp4
```

### **Compress Videos**

Reduce video size by adjusting bitrate:

```bash
ffmpeg -i input.mp4 -vcodec libx264 -crf 20 output.mp4
```

---

## Troubleshooting FFmpeg on ARM Windows

1. **Performance Issues**:

   - Verify hardware acceleration is enabled.
   - Use faster presets (e.g., `-preset ultrafast`).

2. **Path Errors**:

   - Ensure the FFmpeg binaries folder is added to the system PATH.

3. **Unsupported Codecs**:
   - Some codecs may require custom FFmpeg builds. Check the repository or compile FFmpeg manually.

---

## Resources

- [FFmpeg Official Documentation](https://ffmpeg.org/documentation.html)
- [FFmpeg Windows ARM64 Builds](https://github.com/tordona/ffmpeg-win-arm64)
- [Windows PATH Environment Guide](https://learn.microsoft.com/en-us/windows/desktop/system/environment-variables)

---
