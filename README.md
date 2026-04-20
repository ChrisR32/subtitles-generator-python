# Video Subtitle Generator Notebook

This notebook generates `.srt` subtitle files from a video using the `faster-whisper` library.

## Overview

The notebook:

- loads a video file
- transcribes the spoken audio
- formats the output into subtitle timestamps
- saves the result as an `.srt` subtitle file

This version is designed to be run in a Jupyter notebook from top to bottom.

## Requirements

Install the required package:

```python
!pip install faster-whisper
```

## Files

- `your_notebook.ipynb` — the notebook that generates subtitles
- `my_video.mp4` — the input video file
- `my_video.srt` — the generated subtitle file

## How to Run

1. Open the notebook in Jupyter.
2. Run the install cell:

   ```python
   !pip install faster-whisper
   ```

3. Run the cells that define the helper functions and subtitle generation function.
4. Set your video path:

   ```python
   video_path = "my_video.mp4"
   ```

5. Run the transcription cell:

   ```python
   output_file = generate_subtitles(
       video_path=video_path,
       model_size="small",
       language=None,
       device="cpu",
       compute_type="int8"
   )
   ```

6. The notebook will create an `.srt` file in the same location as the video unless another output path is provided.

## Notes on Code Sources

This notebook uses the `faster-whisper` Python library for speech-to-text transcription.

### Source attribution

- The overall notebook structure, helper functions, and `.srt` writing logic were custom-written for this project.
- The transcription approach is based on the public usage pattern of the `faster-whisper` library, specifically use of:
  - `WhisperModel(...)`
  - `model.transcribe(...)`

## Model Options

You can change the model size depending on speed vs accuracy:

- `tiny` — fastest
- `small` — good balance
- `medium` — better accuracy
- `large-v3` — highest accuracy, slower

Example:

```python
model_size="medium"
```

## Output

The output is a standard SubRip subtitle file:

```text
1
00:00:00,000 --> 00:00:02,500
hello and welcome

2
00:00:02,500 --> 00:00:05,000
this video demonstrates subtitle generation
```

## Disclaimer

The transcription quality depends on:

- audio clarity
- speaker accents
- background noise
- selected model size

Subtitles may need minor manual correction after generation.
