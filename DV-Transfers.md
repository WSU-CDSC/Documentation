# What is DV
![DV Analyzer Output](Resources/DV_Analyzer_Out.png)
* Add note about ExFat if using usb drive

# Pre-transfer Inspection
![DV Lock](Resources/DV.png)

# Camera Setup
![DV Port](Resources/DV_Port.png)

# Transferring with Premiere

# Post Transfer Processing
* Rewrap to raw DV if desired `ffmpeg -i INPUT.mov - f rawvideo -c:v copy OUTPUT.dv`
* [DV Analyzer](https://mediaarea.net/DVAnalyzer)
* Command for derivative `ffmpeg -i INPUT.dv -c:v libx264 -pix_fmt yuv420p -movflags +faststart -preset slow -crf 18 -c:a aac -ar 48k -b:a 128k -vf yadif=deint=1 OUTPUT.mp4`
