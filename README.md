# Unicode to Preeti Font Translator

This repository provides a fine-tuned sequence-to-sequence model for converting Nepali text from **Unicode** encoding to **Preeti** font encoding. The model is based on `Helsinki-NLP/opus-mt-en-ROMANCE` and was trained using a custom phrase-aligned dataset.

---

## 🧾 Dataset Used for Training

The model was trained on a parallel dataset containing aligned phrase pairs of Unicode and Preeti font texts.

- **Download**: [Unicode to Preeti Dataset (Google Drive)](https://drive.google.com/file/d/1d3g9qezi7Y5PRN5zRbBb26A_cHerGLHm/view?usp=sharing)
- **Format**: CSV file
- **Columns**:
  - `unicode`: Nepali sentence in Unicode
  - `preeti`: Corresponding Preeti font encoded sentence
- **Encoding**: UTF-8
- **Sample Size**: ~2688 sentence pairs
- **Use Case**: Designed to convert legacy Preeti-encoded documents into modern Unicode format or vice versa, which is essential for digital archival, OCR correction, and language processing.

---

## 🚀 Model Details

- **Base Model**: `Helsinki-NLP/opus-mt-en-ROMANCE`
- **Architecture**: Transformer (Encoder-Decoder)
- **Framework**: PyTorch + Hugging Face Transformers
- **Trained With**: AdamW optimizer, warmup schedule, max length 128 tokens
- **Checkpoint Format**: `safetensors` for secure and fast model loading

---

## ✨ Inference Example

```python
from transformers import AutoTokenizer, AutoModelForSeq2SeqLM

model = AutoModelForSeq2SeqLM.from_pretrained("your-username/unicode-to-preeti-translator")
tokenizer = AutoTokenizer.from_pretrained("your-username/unicode-to-preeti-translator")

text = "यो एउटा युनिकोड वाक्य हो।"
inputs = tokenizer(text, return_tensors='pt')
outputs = model.generate(**inputs)
preeti_output = tokenizer.decode(outputs[0], skip_special_tokens=True)
print("Preeti:", preeti_output)
---

# Unicode to Preeti Font Converter - Key Features

## 1. Single Text Conversion 🔤

### `convert_single()`
- Convert individual Unicode texts
- Beam search translation
- Robust error handling
- Detailed logging

## 2. Batch Conversion 📚

### `batch_convert()`
- Convert multiple texts simultaneously
- Efficient parallel processing
- Memory-optimized

## 3. CSV File Conversion 📄

### `convert_from_csv()`
- Convert texts from CSV files
- Flexible column selection
- Automatic result generation
- Error-tolerant design

## 4. Key Technical Capabilities

- GPU acceleration
- Supports complex Nepali characters
- Handles single characters, words, phrases
- Configurable translation parameters

## 5. Usage Example

```python
# Initialize converter
converter = UnicodePreetiFontConverter()

# Single text conversion
preeti_text = converter.convert_single("नमस्ते")

# Batch conversion
results = converter.batch_convert(["क", "का", "कि"])

# CSV conversion
converted_df = converter.convert_from_csv("unicode_texts.csv")
```

### Best Practices
- Validate input texts
- Monitor conversion quality
- Use appropriate batch sizes

---

# 📦 Unicode to Preeti Font Conversion Model (Pretrained)

This archive contains all necessary files for loading and using the pretrained **Unicode to Preeti font translation model**. The model is fine-tuned on a sequence-to-sequence architecture and is stored in a format compatible with the Hugging Face 🤗 Transformers library.

---

## 📁 Download

You can download the complete model directory (zipped) from the following link:

🔗 **[Google Drive: unicode-to-preeti-model.zip](https://drive.google.com/file/d/1B_uCSTBzRWJWomDOGOZ3ZSEZZ56B6YEW/view?usp=sharing)**

---

## 📂 Contents of the Model Folder

| File Name                  | Description |
|---------------------------|-------------|
| `config.json`             | Model architecture configuration. Defines encoder-decoder layers, hidden size, dropout rates, etc. |
| `generation_config.json`  | Settings used during text generation (e.g., max length, beam size). |
| `model.safetensors`       | The trained model weights in `safetensors` format (safe and efficient). |
| `source.spm`              | SentencePiece model for encoding input (Unicode). |
| `target.spm`              | SentencePiece model for decoding output (Preeti). |
| `special_tokens_map.json` | Maps special tokens like `<pad>`, `<eos>`, `<unk>` used during training and inference. |
| `tokenizer_config.json`   | Configuration for tokenizer behavior (lowercasing, special tokens, etc.). |
| `vocab.json`              | Token vocabulary used by the SentencePiece tokenizer. |
| `training_metrics_plot.png` | Training progress plot showing loss and accuracy trends per epoch. |

---

## 🔧 How to Load and Use the Model

```python
from transformers import AutoTokenizer, AutoModelForSeq2SeqLM

model = AutoModelForSeq2SeqLM.from_pretrained("path/to/unzipped/folder")
tokenizer = AutoTokenizer.from_pretrained("path/to/unzipped/folder")

text = "यो एउटा युनिकोड वाक्य हो।"
inputs = tokenizer(text, return_tensors='pt')
outputs = model.generate(**inputs)
preeti_output = tokenizer.decode(outputs[0], skip_special_tokens=True)

print("Preeti:", preeti_output)
```

**Recommended for**: 
- Document translation
- Text processing
- Language localization
- Linguistic research
