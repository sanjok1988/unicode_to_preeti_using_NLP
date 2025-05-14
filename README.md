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

**Recommended for**: 
- Document translation
- Text processing
- Language localization
- Linguistic research
