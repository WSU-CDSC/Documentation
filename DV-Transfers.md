# Digital Capture of DV Tapes

While DV is contained on tapes in the same manner as analog media, since DV is a digital recording format it makes sense to treat DV tapes as born-digital content and archive them accordingly. Provided the correct adapters are available, DV content is able to be captured natively using the Firewire out that exists on DV playback machines.

This method has several advantages over capturing DV as analog video using a standard A/D converter. Not only will the captured DV stream conform to the data that was stored on the tape, which bolsters archival provenance, the amount of metadata contained within this stream can aid both quality control and cataloging. Using tools such as [MediaInfo](https://mediaarea.net/en/MediaInfo), [MediaInfo Online](https://mediaarea.net/MediaInfoOnline) and [DV Analyzer](https://mediaarea.net/DVAnalyzer) alows analysis of information such as recording time stamps, embedded timecode and playback error concealment. A sample DV Analyzer output is included below:


![DV Analyzer Output](Resources/DV_Analyzer_Out.png)
* Add note about ExFat if using usb drive

# Pre-transfer Inspection
![DV Lock](Resources/DV.png)

# Camera Setup
![DV Port](Resources/DV_Port.jpg)

# Transferring with Premiere

# Post Transfer Processing
* Rewrap to raw DV if desired `ffmpeg -i INPUT.mov - f rawvideo -c:v copy OUTPUT.dv`
* [DV Analyzer](https://mediaarea.net/DVAnalyzer)
* Command for derivative `ffmpeg -i INPUT.dv -c:v libx264 -pix_fmt yuv420p -movflags +faststart -preset slow -crf 18 -c:a aac -ar 48k -b:a 128k -vf yadif=deint=1 OUTPUT.mp4`
