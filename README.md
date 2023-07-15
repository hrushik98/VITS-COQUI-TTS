# VITS-Coqui-TTS
Train a VITS model on Coqui framework using CUSTOM data.

# You Need:
1. Audio samples (.wav format)
2. Transcriptions of the audio files

# Preparing Metadata


Format of metadata:
`<audio-file-name-without-wav-suffix>|<transcription>|<transcription>`
<br>
example:
`Audio1|Hey John, how you doing?|Hey John, how you doing?`
<br>

Below is the code I have used to prepare metadata.csv <br> Note that I have first uploaded my transcripts into a folder called as `transcripts`.
```python
import os
import csv

transcriptis = os.listdir("/content/texts") 

for i in range(0, len(transcripts)):
    with open(f"/content/transcripts/{transcripts[i]}", "r") as f:
        text = f.read()
        print(text)

        with open("metadata.csv", "a") as f:
            datai = csv.writer(f)
            col1 = f"{transcripts[i][:-4]}|{text}|{text}"
            datai.writerow([col1])

```

# Let's start!
0. create a folder (ex: MyTTSdata) and a subfolder with the name "wavs". <br>
   Add the audio samples in the "wavs" sub-folder. <br>
   Add the metadata.csv file in the folder. (Not inside wavs).
1. 
