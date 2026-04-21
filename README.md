# Subtitle Tools Notebook Collection

This repository contains a small set of Jupyter notebooks for generating, translating, and burning subtitles onto video files.

## Repository Structure

```text
.
├── burn_subs.ipynb
├── gen_subs.ipynb
├── README.md
└── subs_language_convert.ipynb
```

## Overview

These notebooks are designed to work as a simple subtitle workflow.

### `gen_subs.ipynb`
This notebook is used to generate subtitle files from a video.

It is used to:
- load a video file
- transcribe spoken audio
- auto-detect or set the language
- save subtitles as an `.srt` file

Typical use:
- generate French subtitles from a French video
- generate English subtitles from an English video
- create the base subtitle file before translation

### `subs_language_convert.ipynb`
This notebook is used to translate an existing subtitle file from one language to another.

It is used to:
- load an existing `.srt` file
- keep subtitle numbering and timestamps unchanged
- translate only the subtitle text
- save a new translated subtitle file

Typical use:
- convert French subtitles to English
- preserve subtitle timing while changing language

### `burn_subs.ipynb`
This notebook is used to burn subtitles directly into a video file.

It is used to:
- load a video file
- load an `.srt` subtitle file
- embed subtitles onto the video image
- export a new video file with hardcoded subtitles

Typical use:
- create a final video with subtitles permanently shown on screen

## Example Workflow

A common workflow for this repository is:

1. Use `gen_subs.ipynb` to generate subtitles from the original video.
2. Use `subs_language_convert.ipynb` to translate the subtitle file if needed.
3. Use `burn_subs.ipynb` to embed the subtitles into the final video.

## Requirements

Depending on the notebook, this project may use:

- `faster-whisper`
- `deep-translator`
- `ffmpeg`
- `pandas`
- `matplotlib`
- standard Python libraries such as `pathlib` and `subprocess`

## Notes on Code Sources

These notebooks combine custom notebook code with external Python libraries.

### External libraries used
- `faster-whisper` for subtitle generation from video/audio
- `deep-translator` for subtitle text translation
- `ffmpeg` for burning subtitles into video

### Authorship note
- The notebook structure and workflow code were written for this project.
- External library calls are based on the public documentation and normal usage patterns of those libraries.
- Comments should be included in the notebooks to make clear where external libraries are being used.

## Example comment style for notebook cells

```python
# external library used for speech-to-text transcription
from faster_whisper import WhisperModel

# uses faster-whisper api to generate subtitle segments
segments, info = model.transcribe(str(video_file), language=language, beam_size=5)
```

```python
# external library used for subtitle text translation
from deep_translator import GoogleTranslator
```

```python
# ffmpeg is called from python to burn subtitles into the final video
import subprocess
```

## Simple Summary

This repository is a small subtitle toolkit made up of Jupyter notebooks. It can generate subtitle files from video, translate subtitle files between languages, and burn subtitles directly onto videos.
