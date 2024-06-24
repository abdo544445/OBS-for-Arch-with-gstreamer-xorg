# Installing and Configuring OBS on Arch Linux for AMD GPUs

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

4. Install necessary dependencies for Xorg, GStreamer, and AMD GPU support:
   ```bash
   sudo pacman -S xorg-server gstreamer gst-plugins-base gst-plugins-good gst-plugins-bad gst-plugins-ugly mesa vulkan-radeon libva-mesa-driver mesa-vdpau
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

3. Configure OBS to use GStreamer with AMD GPU acceleration:
   - Go to Settings > Output
   - Set the "Output Mode" to "Advanced"
   - In the "Streaming" tab:
     - Set "Type" to "Custom Output (FFmpeg)"
     - Set "FFmpeg Output Type" to "Output to URL"
     - In the "File Path or URL" field, enter your streaming URL
     - Set "Container Format" to "flv"
     - Set "Video Encoder" to "h264_vaapi" (for VA-API) or "h264_amf" (for AMF)
   - In the "Recording" tab:
     - Set "Type" to "Custom Output (FFmpeg)"
     - Choose your desired container format (e.g., "mkv" or "mp4")
     - Set "Muxer Settings" to "movflags=faststart"
     - Set "Video Encoder" to "h264_vaapi" (for VA-API) or "h264_amf" (for AMF)
     - Set "Audio Encoder" to "aac"

4. Enable AMD GPU encoding:
   - Go to Settings > Advanced
   - In the "Video" section, set "Video Adapter" to your AMD GPU

5. Add sources:
   - Click the "+" button in the "Sources" box
   - Add "Screen Capture (XSHM)" for capturing your screen
   - Add "Audio Input Capture" and "Audio Output Capture" for audio

6. Test your configuration:
   - Start a test recording or stream to ensure everything is working correctly

## Troubleshooting

If you encounter issues:
- Ensure your AMD GPU drivers are up-to-date
- Check if VA-API or AMF is properly installed and configured on your system
- Try switching between VA-API and AMF encoders to see which performs better
- Monitor your GPU usage and temperatures during streaming/recording
- Consult the Arch Wiki or OBS forums for specific error messages related to AMD GPUs

Remember to keep OBS and your system updated regularly for best performance and compatibility.
