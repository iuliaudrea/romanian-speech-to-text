# Fine-Tuning Whisper for Romanian ASR

This repository contains scripts for fine-tuning and evaluating OpenAI's Whisper models on Romanian automatic speech recognition (ASR) tasks. The fine-tuning focuses on improving transcription accuracy for specific domains, such as weather forecasts and horoscopes. The models themselves are hosted on Hugging Face, and the repository includes code for fine-tuning, evaluation, and a detailed documentation in Romanian.

## Overview

The fine-tuning process is performed exclusively on domain-specific datasets to enhance Whisper's performance in Romanian for weather and horoscope categories. Models trained in two stages follow a specific naming convention:
```
category1_category2_model
```
where:
- `category1` represents the first fine-tuning dataset.
- `category2` represents the second fine-tuning dataset (if applicable).
- `model` refers to the Whisper model size (tiny, small, base).

## Available Models

| Model | Base Model | Training Datasets | WER | Last Updated |
|-------|-----------|-------------------|-----|--------------|
| [all_data_model_small](https://huggingface.co/iulik-pisik/all_data_model_small) | Whisper Small | Horoscope + Weather | 8.51% | Jul 2, 2024 |
| [all_data_model_base](https://huggingface.co/iulik-pisik/all_data_model_base) | Whisper Base | Horoscope + Weather | 13.61% | Jul 2, 2024 |
| [all_data_model_tiny](https://huggingface.co/iulik-pisik/all_data_model_tiny) | Whisper Tiny | Horoscope + Weather | 17.14% | Jul 2, 2024 |
| [horoscop_vreme_tiny](https://huggingface.co/iulik-pisik/horoscop_vreme_tiny) | Whisper Tiny | Horoscope → Weather | 13.99% | Apr 3, 2024 |
| [horoscop_vreme_small](https://huggingface.co/iulik-pisik/horoscop_vreme_small) | Whisper Small | Horoscope → Weather | 8.87% | Apr 3, 2024 |
| [horoscop_vreme_base](https://huggingface.co/iulik-pisik/horoscop_vreme_base) | Whisper Base | Horoscope → Weather | 11.89% | Apr 3, 2024 |
| [vreme_horoscop_small](https://huggingface.co/iulik-pisik/vreme_horoscop_small) | Whisper Base | Weather → Horoscope | 10.17% | Apr 3, 2024 |
| [vreme_horoscop_base](https://huggingface.co/iulik-pisik/vreme_horoscop_base) | Whisper Base | Weather → Horoscope | 17.66% | Apr 3, 2024 |
| [vreme_horoscop_tiny](https://huggingface.co/iulik-pisik/vreme_horoscop_tiny) | Whisper Base | Weather → Horoscope | 23.33% | Apr 3, 2024 |
| [vreme_model_small](https://huggingface.co/iulik-pisik/vreme_model_small) | Whisper Small | Horoscope | 7.99% | Mar 17, 2024 |
| [vreme_model_base](https://huggingface.co/iulik-pisik/vreme_model_base) | Whisper Base | Horoscope | 11.57% | Mar 17, 2024 |
| [vreme_model_tiny](https://huggingface.co/iulik-pisik/vreme_model_tiny) | Whisper Tiny | Horoscope | 13.91% | Mar 17, 2024 |
| [horoscope_model_base](https://huggingface.co/iulik-pisik/horoscope_model_base) | Whisper Base | Horoscope | 17.03% | Mar 4, 2024 |
| [horoscope_model_tiny](https://huggingface.co/iulik-pisik/horoscope_model_tiny) | Whisper Tiny | Horoscope | 21.85% | Mar 4, 2024 |

## Datasets

The following datasets were collected and used for fine-tuning:

| Dataset | Description | HF Link |
|---------|------------|---------|
| [audio_vreme](https://huggingface.co/iulik-pisik/audio_vreme) | Transcriptions of Romanian weather forecasts | Updated Apr 3, 2024 |
| [horoscop_urania](https://huggingface.co/iulik-pisik/horoscop_urania) | Horoscope transcriptions (Urania) | Updated Mar 7, 2024 |
| [horoscop_neti](https://huggingface.co/iulik-pisik/horoscop_neti) | Horoscope transcriptions (Neti) | Updated Feb 23, 2024 |

## Usage

To use these models in your ASR pipeline:

```python
from transformers import pipeline

asr_pipeline = pipeline("automatic-speech-recognition", model="iulik-pisik/all_data_model_base")
result = asr_pipeline("path/to/audio.wav")
print(result["text"])
```

## Future Work

- **Expanding datasets** – Collecting more domain-specific Romanian speech data.
- **Exploring larger models** – Fine-tuning Whisper medium/large for improved performance.
- **Benchmarking accuracy** – Evaluating models on real-world ASR tasks.

