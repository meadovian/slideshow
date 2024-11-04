# Image Sequence to Video Converter

A bash script that combines a sequence of PNG images into a video file, with configurable durations for each frame and transition effects.

## Features

- Automatic image sequencing based on timestamps
- Configurable duration for each frame
- Optional fade transitions between images
- Multiple quality presets
- Maintains aspect ratios
- Handles varying image dimensions
- Efficient single-pass processing

## Prerequisites

- macOS (tested on Sonoma 14.6)
- ffmpeg (required for video processing)

If ffmpeg is not installed, you can install it using Homebrew:
```bash
brew install ffmpeg
```

## Installation

1. Save the script to a file (e.g., `png-to-video.sh`)
2. Make it executable:
```bash
chmod +x png-to-video.sh
```

## Usage

### Basic Usage

```bash
./png-to-video.sh /path/to/your/images
```

### Advanced Usage

```bash
./png-to-video.sh /path/to/your/images -d 3 -o myvideo.mp4 -q high -t 0.5
```

### Options

- `-d, --duration SECONDS`: Default duration per image (default: 2)
- `-o, --output FILENAME`: Output filename (default: output.mp4)
- `-f, --framerate FPS`: Output framerate (default: 30)
- `-q, --quality QUALITY`: Encoding quality (low|medium|high, default: medium)
- `-t, --transition SECONDS`: Fade transition duration (default: 0.5, 0 for no fade)
- `-h, --help`: Show help message

### Quality Presets

- `low`: Faster encoding, larger file size reduction
- `medium`: Balanced quality and encoding speed
- `high`: Best quality, slower encoding

## How It Works

1. The script creates a temporary working directory
2. Images are processed in timestamp order
3. A duration file is created for frame timing
4. You can review and modify durations before processing
5. Images are combined into a video using ffmpeg
6. The final video is moved to the original directory

## Customizing Frame Durations

The script creates a `durations.txt` file in the temporary directory with the format:
```
image001.png=2
image002.png=2
image003.png=3
```

You can edit this file before confirming video creation to customize individual frame durations.

## Output Format

- Container: MP4
- Codec: H.264
- Pixel Format: YUV420P
- Aspect Ratio: Maintained from source images
- Framerate: 30 fps (configurable)

## Troubleshooting

1. **Permission Errors**
   - Ensure you have write permissions in the target directory
   - Run `chmod 644` on your PNG files if needed

2. **Memory Issues**
   - For large image sequences, try the `low` quality preset
   - Reduce the output framerate

3. **Dimension Errors**
   - The script automatically handles odd dimensions
   - Source images can have different dimensions

## Tips

- Use consistent image dimensions for best results
- For social media, consider using the `medium` quality preset
- Add transitions for smoother playback
- Back up your original images before processing

## Contributing

We welcome contributions from the community! Here's how you can help:

### How to Contribute

1. **Bug Reports**
   - Use the GitHub Issues section to report bugs
   - Provide detailed steps to reproduce the issue
   - Include your system information (OS version, ffmpeg version)
   - Share relevant error messages

2. **Feature Requests**
   - Submit feature requests through GitHub Issues
   - Explain the use case for the feature
   - Suggest implementation approaches if possible

3. **Code Contributions**
   - Fork the repository
   - Create a feature branch (`git checkout -b feature/amazing-feature`)
   - Commit your changes (`git commit -m 'Add amazing feature'`)
   - Push to the branch (`git push origin feature/amazing-feature`)
   - Open a Pull Request

### Code Guidelines

- Keep the bash script POSIX-compliant when possible
- Add comments for complex operations
- Update documentation for new features
- Test your changes on different macOS versions
- Maintain the existing error handling patterns

### Documentation

- Update the README.md if you add new features
- Provide examples for new functionality
- Keep the help function (`show_help`) up to date
- Document any new dependencies

## License

MIT License

Copyright (c) 2024 [Project Contributors]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

## Additional License Notes

- This project is intended to be freely available for both personal and commercial use
- You're welcome to use, modify, and distribute the code
- Attribution is appreciated but not required
- Contributions to this project will be subject to the same MIT license
- The license applies to the script and documentation, not to videos created using the script

## Community and Support

- Questions can be asked via GitHub Issues
- For extended discussions, use GitHub Discussions
- Consider helping others by sharing your experiences and solutions
- Join our community of contributors to make this tool even better!
