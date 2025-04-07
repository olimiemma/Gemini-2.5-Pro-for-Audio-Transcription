
# 🎙️ Gemini 2.5 Pro Audio Transcription & Diarization

This project showcases how to use **Gemini 2.5 Pro** for transcribing multi-speaker audio, applying **audio diarization** (identifying "who said what"), and working with long-form audio files effectively.

---

## 🔍 Overview

With Gemini 2.5 Pro, you can:

- Upload and transcribe long-form audio (up to 9.5 hours in total per prompt).
- Perform **audio diarization** to segment and label speakers automatically.
- Handle common audio formats like `.wav`, `.mp3`, `.aac`, etc.
- Work within token and resolution limits using smart chunking.
- Extract meaningful text output with speaker attribution.

---

## 🧠 How Audio Diarization Works

```
Input Audio (Multi-speaker)
       |
1. Feature Extraction — Extract MFCCs, spectral features
       ↓
2. Voice Activity Detection (VAD) — Detect speech vs. non-speech
       ↓
3. Speaker Segmentation & Clustering — Identify unique speakers
       ↓
Output: Speaker-Labeled Timeline
```

Example:
```
[00:00–00:15] Speaker A: Hello and welcome...
[00:15–00:45] Speaker B: Thanks! I'm excited...
```

---

## 📁 Supported Audio Formats

Gemini supports:

- WAV - `audio/wav`
- MP3 - `audio/mp3`
- AIFF - `audio/aiff`
- AAC - `audio/aac`
- OGG - `audio/ogg`
- FLAC - `audio/flac`

---

## 🧩 Tokenization & Audio Limits

- **1 second** of audio ≈ **32 tokens**
- **1 minute** of audio ≈ **1,920 tokens**
- Max **input tokens** = `1,000,000`
- Max **output tokens** = `64,000`

| Audio Duration | Input Tokens (approx.) | Output Tokens |
|----------------|------------------------|----------------|
| 15 minutes     | 28,800 tokens           | ~8K tokens     |
| 1 hour         | 115,200 tokens          | ~32K tokens    |
| 2 hours        | 230,400 tokens          | ~64K tokens    |

> 🔁 To process more than 2 hours of audio, chunk the file and use prompt windowing (e.g., from X min to Y min).

---

## 💾 Uploading Audio to Gemini

You can provide audio in two ways:

- **Pre-upload** via API or file handler.
- **Inline data** in the request body.
---

**NB:** I removed the lines  
```python  
#import IPython.display as ipd  
#ipd.Audio("/content/HS4830417304.mp3", autoplay=True)  
```  
so that the file can be uploaded to Git—it was beyond the 25MB limit.  
Feel free to add those lines at the end of the notebook if needed.

## 💵 Pricing (as of Gemini 2.5 Pro)

| Modality         | Price / 1M Tokens |
|------------------|------------------|
| Input ≤ 200K     | $1.25            |
| Input > 200K     | $2.50            |
| Output ≤ 200K    | $10.00           |
| Output > 200K    | $15.00           |

---

## 🧪 Additional Notes

- Audio is **downsampled to 16 kbps mono**. Stereo channels are merged.
- Gemini understands **non-speech audio**, but only returns responses for **English-language speech**.
- You can label speakers manually if diarization doesn’t identify names correctly.

---

## 🧰 Example Use Case

```python
prompt = """
Please transcribe the audio and indicate speaker turns.

From minute 5:00 to minute 10:00:
Speaker A is Alice
Speaker B is Bob
"""
```

---

## 📈 Output Example

```
[Alice]: Welcome to the show!
[Bob]: Thanks, it’s great to be here.
...
```

---

## 🚀 How to Use (Coming Soon)

- [ ] Python example with Gemini API
- [ ] Audio file chunking helper
- [ ] Diarization label enhancer

---

## 📦 File Summary

- `Gemini_2_5_Pro_Podcast_Audio_transcription_boo.ipynb` – Jupyter notebook showing audio processing
- Images/screenshots from Sam Witteveen’s tutorial

---![Sam Witteveen - Gemini 2 5 Pro for Audio Transcription  LMhe2egLsrQ - 1207x679 - 1m18s](https://github.com/user-attachments/assets/117a624a-6a3b-4c02-b857-25acef20b843)
![Sam Witteveen - Gemini 2 5 Pro for Audio Transcription  LMhe2egLsrQ - 1207x679 - 1m29s](https://github.com/user-attachments/assets/210e9938-4032-4dc8-9227-71facc6413c1)
![Sam Witteveen - Gemini 2 5 Pro for Audio Transcription  LMhe2egLsrQ - 1207x679 - 2m09s](https://github.com/user-attachments/assets/6b7fe94b-e3a6-42f9-82f2-1a6f2da882a6)
![Sam Witteveen - Gemini 2 5 Pro for Audio Transcription  LMhe2egLsrQ - 1207x679 - 2m39s](https://github.com/user-attachments/assets/7d3cea41-3bd1-4767-b913-8d3ed37784d1)
![Sam Witteveen - Gemini 2 5 Pro for Audio Transcription  LMhe2egLsrQ - 1207x679 - 2m59s](https://github.com/user-attachments/assets/f80f561f-6ea9-45fa-803e-72e75224545a)
![Sam Witteveen - Gemini 2 5 Pro for Audio Transcription  LMhe2egLsrQ - 1207x679 - 4m30s](https://github.com/user-attachments/assets/653e4af8-9953-4bc8-8e86-e555370090fa)
![Sam Witteveen - Gemini 2 5 Pro for Audio Transcription  LMhe2egLsrQ - 1207x679 - 7m25s](https://github.com/user-attachments/assets/979a6861-e088-4377-8bd8-c679e6dcefaa)


## 👤 Credits

- Gemini AI by Google DeepMind
- Visuals inspired by Sam Witteveen
- README by Emmanuel Kasigazi

---
