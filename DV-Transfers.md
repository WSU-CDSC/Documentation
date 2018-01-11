# Digital Capture of DV Tapes

While DV is contained on tapes in the same manner as analog media, since DV is a digital recording format it makes sense to treat DV tapes as born-digital content and archive them accordingly. Provided the correct adapters are available, DV content is able to be captured natively using the Firewire out that exists on DV playback machines.

This method has several advantages over capturing DV as analog video using a standard A/D converter. Not only will the captured DV stream conform to the data that was stored on the tape, which bolsters archival provenance, the amount of metadata contained within this stream can aid both quality control and cataloging. Using tools such as [MediaInfo](https://mediaarea.net/en/MediaInfo), [MediaInfo Online](https://mediaarea.net/MediaInfoOnline) and [DV Analyzer](https://mediaarea.net/DVAnalyzer) alows analysis of information such as recording time stamps, embedded timecode and playback error concealment. A sample DV Analyzer output is included below:


![DV Analyzer Output](Resources/DV_Analyzer_Out.png)
* Add note about ExFat if using usb drive

# Pre-transfer Inspection
* Before inserting the tape into the player, do a visual inspection. Is the lock tab (pictured below) set to the `SAVE` position? If not, then move it to `SAVE`. Check to see if the tape pack looks normal. Once you have inserted the tape into the player, fast-forward it to the end and then rewind it once to make sure that the tape tension is ready for correct playback.

![DV Lock](Resources/DV.png)

# Camera Setup
![DV Port](Resources/DV_Port.jpg)

# Transferring with Premiere

# Post Transfer Processing
* [DV Analyzer](https://mediaarea.net/DVAnalyzer)
- Files should be inspected using the `DV Analyzer` tool. This tool allows the embedded timecode metadata as well as error correction information to be inspected. Since DV is a tape based format, it is normal to have a certain amount of errors, but checking the file information with DV Analyzer will allow you to identify if there were any particularly problematic segments.

* Rewrap to raw DV if desired `ffmpeg -i INPUT.mov - f rawvideo -c:v copy OUTPUT.dv`
* Command for derivative: `ffmpeg -i INPUT.dv -c:v libx264 -pix_fmt yuv420p -movflags +faststart -preset slow -crf 18 -c:a aac -ar 48k -b:a 128k -vf yadif=deint=1 OUTPUT.mp4`

Alternately, if the original transfer was broken up into segments and it is desirable to combine them into a single access file, the [concat function of FFmpeg](https://amiaopensource.github.io/ffmprovisr/#join_files) can be used:
`ffmpeg -f concat -safe 0 -i ListOfDVs.txt -c:v libx264 -pix_fmt yuv420p -movflags +faststart -preset slow -crf 18 -c:a aac -ar 48k -b:a 128k -vf yadif=deint=1 OUTPUT.mp4`
