# Digital Capture of DV Tapes

While DV is contained on tapes in the same manner as analog media, since DV is a digital recording format it makes sense to treat DV tapes as born-digital content and archive them accordingly. Provided the correct adapters are available, DV content is able to be captured natively using the FireWire out that exists on DV playback machines.

This method has several advantages over capturing DV as analog video using a standard A/D converter. Not only will the captured DV stream conform to the data that was stored on the tape, which bolsters archival provenance, the amount of metadata contained within this stream can aid both quality control and cataloging. Using tools such as [MediaInfo](https://mediaarea.net/en/MediaInfo), [MediaInfo Online](https://mediaarea.net/MediaInfoOnline) and [DV Analyzer](https://mediaarea.net/DVAnalyzer) allows analysis of information such as recording time stamps, embedded timecode and playback error concealment. A sample DV Analyzer output is included below:


![DV Analyzer Output](Resources/DV_Analyzer_Out.png)
* Add note about ExFat if using usb drive

# Pre-transfer Inspection
* Before inserting the tape into the player, do a visual inspection. Is the lock tab (pictured below) set to the `SAVE` position? If not, then move it to `SAVE`. Check to see if the tape pack looks normal. Once you have inserted the tape into the player, fast-forward it to the end and then rewind it once to make sure that the tape tension is ready for correct playback.

![DV Lock](Resources/DV.png)

# Camera Setup

To connect the player/camera to the computer you will use the 'DV Out' port (example picture below) on the camera and connect it via the FireWire to Thunderbolt adapter. This enables the computer to control the player and capture the contents of the tape as data rather than as analog video.


![DV Port](Resources/DV_Port.jpg)

Link to Manual for [CDSC Camera](https://www.sony.co.uk/electronics/support/res/manuals/3061/30615081M.pdf)

# Transferring with AVCVideoCap (Suggested method)

AVCVideoCap can be downloaded through the [Apple Developer Tools](https://developer.apple.com/develop/) (an account must be registered first). It is a part of the FireWire SDK and can be downloaded by searching for `Firewire` and then installing the package.

![AVCVideoCap1](Resources/avcvideocap1.png)

![AVCVideoCap2](Resources/avcvideocap2.png)

![AVCVideoCap3](Resources/avcvideocap3.png)

# Transferring with Premiere (Non-preferred Method)

Premier is capable of capturing data from DV tapes, but is not the preferred method due to its tendency to drop frames when it encounters a problem segment. If there are no problem segments, and Premier is able to capture a tape as a single file then that file may be considered preservation quality. It is, however, available within the Libraries using existing infrastructure so instructions for its use are being included.

![New Project](Resources/NewProject.png)

![Capture Menu](Resources/CaptureMenu.png)

![Capture Screen](Resources/CaptureScreen.png)

# Post Transfer Processing
* [DV Analyzer](https://mediaarea.net/DVAnalyzer):
Files should be inspected using the `DV Analyzer` tool. This tool allows the embedded timecode metadata as well as error correction information to be inspected. Since DV is a tape based format, it is normal to have a certain amount of errors, but checking the file information with DV Analyzer will allow you to identify if there were any particularly problematic segments.

* Re-wrap to raw DV if desired: Since Premier captures DV files in a MOV wrapper, it may be preferable to re-wrap them to a raw DV stream. This is slightly smaller, and a more true representation of the data contained on the taper. To do this, use the progam [FFmpeg](https://www.ffmpeg.org/) and the following command: `ffmpeg -i INPUT.mov - f rawvideo -c:v copy OUTPUT.dv`

## Make Derivatives
The following commands will create a high quality `mp4` file that has been deinterlaced for optimum viewing quality on modern screens.
* Command for derivative: `ffmpeg -i INPUT.dv -c:v libx264 -pix_fmt yuv420p -movflags +faststart -preset slow -crf 18 -c:a aac -ar 48k -b:a 128k -vf yadif=deint=1 OUTPUT.mp4`

Alternately, if the original transfer was broken up into segments and it is desirable to combine them into a single access file, the [concat function of FFmpeg](https://amiaopensource.github.io/ffmprovisr/#join_files) can be used:
`ffmpeg -f concat -safe 0 -i ListOfDVs.txt -c:v libx264 -pix_fmt yuv420p -movflags +faststart -preset slow -crf 18 -c:a aac -ar 48k -b:a 128k -vf yadif=deint=1 OUTPUT.mp4`

# Resources
* [Information](https://www.adamwilt.com/DV-tech.html) about DV specifications and various formats
* [DV Analyzer](https://mediaarea.net/DVAnalyzer/what-does-it-analyze) list of information about the metadata that DV Analyzer reads.
