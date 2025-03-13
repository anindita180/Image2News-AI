# Image-to-News-Report-Pipeline

This project automates the process of generating news reports from images containing text. It utilizes Optical Character Recognition (OCR), text summarization, and a language model to extract text, create summaries, and generate news articles.

## Overview

The pipeline consists of three main steps:

1.  **OCR (Optical Character Recognition):** Extracts text from images.
2.  **Summarization:** Summarizes the extracted text.
3.  **News Report Generation:** Generates news reports from the summaries.

## Project Structure

├── OCR_application.ipynb
├── data/
│   └── images/      # Input images (.png, .jpg, .jpeg)
├── outputs/
│   ├── ocr_results.json       # JSON file containing extracted text
│   ├── summarized_results.json # JSON file containing summarized text
│   └── news_results.json      # JSON file containing generated news reports
└── README.md


## Steps

### 1. OCR (Extracting Text from Images)

* **Technology:** EasyOCR
* **Input:** Images in `data/images/` (.png, .jpg, .jpeg)
* **Output:** `outputs/ocr_results.json` (dictionary of image filenames and extracted text)
* **Implementation:** Inside `OCR_application.ipynb`

### 2. Summarization

* **Technology:** T5-small (Hugging Face Transformers)
* **Input:** `outputs/ocr_results.json`
* **Output:** `outputs/summarized_results.json` (dictionary of image filenames and summarized text)
* **Implementation:** Inside `OCR_application.ipynb`

### 3. News Report Generation

* **Technology:** EleutherAI/gpt-neo-1.3B or distilgpt2 (Hugging Face Transformers)
* **Input:** `outputs/summarized_results.json`
* **Output:** `outputs/news_results.json` (dictionary of image filenames and generated news reports)
* **Implementation:** Inside `OCR_application.ipynb`

**Note:** The initial attempt to use `dolly-v2-3B` resulted in RAM crashes. The project now utilizes smaller models (`EleutherAI/gpt-neo-1.3B` or `distilgpt2`), limits output length, and employs float16 precision to address this issue.

## Setup and Usage

1.  **Clone the repository:**

    ```bash
    git clone [repository_url]
    cd image-to-news-report-pipeline
    ```

2.  **Install dependencies:**

    ```bash
    pip install -r requirements.txt
    ```

3.  **Place your images in the `data/images/` directory.**

4.  **Open and run `OCR_application.ipynb` in a Jupyter Notebook environment (like Google Colab or Jupyter Lab).**

5.  **View the results in the `outputs/` directory.**

## Dependencies

* EasyOCR
* Transformers (Hugging Face)
* Torch
* JSON

## Future Improvements

* Implement error handling and logging.
* Allow for user-configurable model selection and parameters.
* Add options for different output formats (e.g., text files, HTML).
* Improve image preprocessing for better OCR accuracy.
* Explore fine-tuning the language model for better news report generation.
* Add a user interface.
* Add functionality to handle multiple languages.
* Improve the news generation prompt to create more diverse and accurate news reports.
