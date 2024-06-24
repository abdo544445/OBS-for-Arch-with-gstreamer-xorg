# OBS-for-Arch-with-gstreamer-xorg
# Installing and Configuring OBS on Arch Linux

## Installation

1. Open your terminal.

2. Update your system:
   ```bash
   sudo pacman -Syu
   ```

3. Install OBS Studio:
   ```bash
   sudo pacman -S obs-studio
   ```

4. Install necessary dependencies for Xorg and GStreamer:
   ```bash
   sudo pacman -S xorg-server gstreamer gst-plugins-base gst-plugins-good gst-plugins-bad gst-plugins-ugly
   ```

## Configuration

1. Launch OBS Studio:
   ```bash
   obs
   ```

2. Configure OBS to use Xorg:
   - Go to Settings (gear icon) > Video
   - Set "Base (Canvas) Resolution" to match your display resolution
   - Set "Output (Scaled) Resolution" as desired
   - Choose your preferred FPS

3. Configure OBS to use GStreamer:
   - Go to Settings > Output
   - Set the "Output Mode" to "Advanced"
   - In the "Streaming" tab:
     - Set "Type" to "Custom Output (FFmpeg)"
     - Set "FFmpeg Output Type" to "Output to URL"
     - In the "File Path or URL" field, enter your streaming URL
     - Set "Container Format" to "flv"
     - Set "Video Encoder" to "h264_vaapi" (if you have an Intel GPU) or "h264_nvenc" (for NVIDIA GPU)
   - In the "Recording" tab:
     - Set "Type" to "Custom Output (FFmpeg)"
     - Choose your desired container format (e.g., "mkv" or "mp4")
     - Set "Muxer Settings" to "movflags=faststart"
     - Set "Video Encoder" to "libx264" or your GPU's hardware encoder
     - Set "Audio Encoder" to "aac"

4. Add sources:
   - Click the "+" button in the "Sources" box
   - Add "Screen Capture (XSHM)" for capturing your screen
   - Add "Audio Input Capture" and "Audio Output Capture" for audio

5. Test your configuration:
   - Start a test recording or stream to ensure everything is working correctly

## Troubleshooting

If you encounter issues:
- Check that all necessary codecs are installed
- Verify that your GPU drivers are up-to-date
- Consult the Arch Wiki or OBS forums for specific error messages

Remember to keep OBS and your system updated regularly for best performance and compatibility.
