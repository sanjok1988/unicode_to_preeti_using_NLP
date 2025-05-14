

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
