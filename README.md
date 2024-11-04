# slideshow
A simple script for converting PNGs to a video stream to show past work.

Image Sequence to Video Converter
A bash script that combines a sequence of PNG images into a video file, with configurable durations for each frame and transition effects.
Features

Automatic image sequencing based on timestamps
Configurable duration for each frame
Optional fade transitions between images
Multiple quality presets
Maintains aspect ratios
Handles varying image dimensions
Efficient single-pass processing

Prerequisites

macOS (tested on Sonoma 14.6)
ffmpeg (required for video processing)

If ffmpeg is not installed, you can install it using Homebrew:
bashCopybrew install ffmpeg
Installation

Save the script to a file (e.g., png-to-video.sh)
Make it executable:

bashCopychmod +x png-to-video.sh
Usage
Basic Usage
bashCopy./png-to-video.sh /path/to/your/images
Advanced Usage
bashCopy./png-to-video.sh /path/to/your/images -d 3 -o myvideo.mp4 -q high -t 0.5
Options

-d, --duration SECONDS: Default duration per image (default: 2)
-o, --output FILENAME: Output filename (default: output.mp4)
-f, --framerate FPS: Output framerate (default: 30)
-q, --quality QUALITY: Encoding quality (low|medium|high, default: medium)
-t, --transition SECONDS: Fade transition duration (default: 0.5, 0 for no fade)
-h, --help: Show help message

Quality Presets

low: Faster encoding, larger file size reduction
medium: Balanced quality and encoding speed
high: Best quality, slower encoding

How It Works

The script creates a temporary working directory
Images are processed in timestamp order
A duration file is created for frame timing
You can review and modify durations before processing
Images are combined into a video using ffmpeg
The final video is moved to the original directory

Customizing Frame Durations
The script creates a durations.txt file in the temporary directory with the format:
Copyimage001.png=2
image002.png=2
image003.png=3
You can edit this file before confirming video creation to customize individual frame durations.
Output Format

Container: MP4
Codec: H.264
Pixel Format: YUV420P
Aspect Ratio: Maintained from source images
Framerate: 30 fps (configurable)

Troubleshooting

Permission Errors

Ensure you have write permissions in the target directory
Run chmod 644 on your PNG files if needed


Memory Issues

For large image sequences, try the low quality preset
Reduce the output framerate


Dimension Errors

The script automatically handles odd dimensions
Source images can have different dimensions



Tips

Use consistent image dimensions for best results
For social media, consider using the medium quality preset
Add transitions for smoother playback
Back up your original images before processing
