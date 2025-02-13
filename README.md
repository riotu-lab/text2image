# Arabic OCR Dataset Generation Pipeline

This repository provides a pipeline for generating an Arabic OCR dataset. The pipeline processes textual data, converts it into various font styles, generates PDF and image representations, and stores the output in a structured format suitable for OCR training.

## Features
- **Text Preprocessing**: Splits Arabic text into manageable chunks.
- **Font Variations**: Supports multiple Arabic fonts (Sakkal Majalla, Amiri, Arial, Calibri, Scheherazade New).
- **DOCX Generation**: Creates formatted Microsoft Word documents.
- **PDF Conversion**: Converts DOCX files to PDFs using LibreOffice.
- **Image Extraction**: Converts PDFs to high-resolution images.
- **Base64 Encoding**: Stores images in Base64 format for easy integration.
- **Dataset Management**: Uploads processed files to Hugging Face datasets.
- **State Persistence**: Saves processing state to allow resumption from the last processed record.

## Requirements

### Python Dependencies
Install the required Python libraries using:
```sh
pip install datasets python-docx pdf2image PIL requests huggingface_hub
```

## Usage
### 1. Prepare Your Hugging Face Dataset
Ensure your dataset is available on Hugging Face and update the script with:
- `DATASET_NAME`: Your dataset name.
- `repo_id`: Your Hugging Face dataset repository ID.
- `YOUR_API_TOKEN`: Your Hugging Face API token.

### 2. Run the Script
Execute the script to process text and generate the dataset:
```sh
python text2image.py
```

### 3. Resume Processing
If the script stops, it will resume from the last processed index using `processing_state.json`.

## Output Format
Each batch of processed data is stored as a CSV file with the following columns:

```csv
image_name,chunk,font_name,image_base64
dataset_1.png,Sample text,Amiri,Base64 string
```


