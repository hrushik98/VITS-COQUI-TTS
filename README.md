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

Below is the code I have used to prepare metadata.csv <br> Note that I have first uploaded my audio transcripts into a folder called as `transcripts` and then prepared the file.
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

# VITS CONFIG 

```python
config = VitsConfig(
    batch_size=32,
    eval_batch_size=16,
    num_loader_workers=4,
    num_eval_loader_workers=4,
    run_eval=True,
    test_delay_epochs=-1,
    epochs=2,
    text_cleaner="phoneme_cleaners",
    use_phonemes=True,
    phoneme_language="en-us",
    phoneme_cache_path=os.path.join(output_path, "phoneme_cache"),
    print_step=25,
    print_eval=False,
    mixed_precision=True,
    output_path=output_path,
    datasets=[dataset_config],
)

```

# Let's start!
0. create a folder (ex: MyTTSdata) and a subfolder with the name "wavs". <br>
   Add the audio samples in the "wavs" sub-folder. <br>
   Add the metadata.csv file in the folder. (Not inside wavs). <br>
1. follow this colab after you're done with the first step
   https://colab.research.google.com/drive/1v7MekB-aBm4YKCAB_8aHq7A2W5WD-zD8?authuser=1#scrollTo=OoF3FVlEK-vY
