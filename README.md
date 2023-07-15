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



# Let's start!
0. create a folder (ex: MyTTSdata) and a subfolder with the name "wavs"
   Add the audio samples in the "wavs" sub-folder
   Add the metadata.csv file in the folder. (Not inside wavs)
1. 
