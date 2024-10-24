# GRID 6.0 - Fruit & Vegetable Detection and Freshness Analysis

## Overview

GRID 6.0 is a project that detects fruits and vegetables in images and analyzes their freshness. Additionally, it processes non-fruit/vegetable images using OCR to extract details such as product name, brand, pack size, manufacturing date, expiry date, and MRP. The project utilizes a Flask backend, a MobileNet-based object detection model, a fine-tuned freshness detection model, and AWS OCR for text extraction.

## Features

- **Fruit & Vegetable Detection**: Identifies whether the object in the image is a fruit or vegetable.
- **Freshness Analysis**: Classifies the freshness of supported fruits and vegetables on a graded scale from "Super Fresh" (A+) to "Rotten" (D).
- **OCR Processing**: For non-fruit/vegetable images, it extracts key information such as product name, brand, expiry date, etc using AWS Textract.
- **Real-Time Image Detection**: The frontend allows users to capture an image, which is analyzed in real-time and results are displayed.
- **Integration with OpenAI**: Extracted OCR details are enhanced with the help of OpenAI's language models to refine and categorize product information.

## Tech Stack

- **Frontend**: Tailwind CSS, HTML
- **Backend**: Flask with WebSockets (via Socket.IO)
- **Models**:
  - Base MobileNet model for object identification
  - Fine-tuned MobileNet model for fruit and vegetable classification and freshness detection
- **OCR**: AWS OCR for text extraction and OpenAI for product details analysis
- **Image Processing**: OpenCV and PIL for handling image formats

## Supported Classes for Freshness Detection

The following fruits and vegetables are supported for freshness detection:

- **Fruits**: Apple, Banana, Grape, Guava, Mango, Orange, Pomegranate, Strawberry
- **Vegetables**: Bell Pepper, Carrot, Cucumber, Ladyfinger, Potato, Tomato

### Freshness Grading Scale:

- **A+ (Super Fresh)**: 90% <= Freshness <= 100%
- **A (Fresh)**: 80% <= Freshness < 90%
- **B (Medium Fresh)**: 60% <= Freshness < 80%
- **C (Stale)**: 40% <= Freshness < 60%
- **D (Rotten)**: Freshness < 40%

## Installation and Setup

1. **Clone the repository**:
    ```bash
    git clone https://github.com/Dev-Reddy/FLIPKART_GRID_6.0_ROBOTICS.git
    cd FLIPKART_GRID_6.0_ROBOTICS
    ```

2. **Install dependencies**:
    Create a virtual environment and install required dependencies:
    ```bash
    python3 -m venv venv
    source venv/bin/activate
    pip install -r requirements.txt
    ```

3. **Run the Flask App**:
    ```bash
    python app.py
    ```

4. **Access the Application**:
    Open your browser and go to `http://localhost:3100/` to use the detection interface.

## Usage

### Detection Flow

1. **Click an Image** on the `/detect` page.
2. The image is sent to the Flask backend via WebSocket.
3. **Object Detection**: The image is first processed using a base MobileNet model and a fine-tuned model to determine if it is a fruit/vegetable.
4. **Freshness Analysis**: If a fruit or vegetable is detected, the freshness is classified based on the predefined scale.
5. **OCR Analysis**: If the object is not a fruit/vegetable, the image undergoes OCR for extracting product details.
6. The combined **results are displayed** on the `/results` page.

### API Endpoints

- **Home**: `GET /` - Loads the homepage.
- **Detect**: `GET /detect` - Opens the camera feed and detection page.
- **Results**: `GET /results` - Displays the results of the image analysis.
- **Analyze**: `POST /analyze` - Analyzes the uploaded image for object detection, freshness, and OCR.

## Code Structure

- `app.py`: The main Flask application file, handling routes and WebSocket connections.
- `analyzer.py`: Processes the input image, performing object detection, freshness analysis, or OCR, and returns results.
- `src/scripts/identify_object.py`: Contains logic for identifying fruits/vegetables using MobileNet.
- `src/scripts/freshness_detection.py`: Contains logic for detecting the freshness of fruits/vegetables.
- `src/scripts/ocr_aws.py`: Implements AWS OCR functionality.
- `src/scripts/ocr_details_openai.py`: Fetches product details from extracted OCR text using OpenAI.

## Future Improvements

- Extend the freshness detection to support more classes of fruits and vegetables.
- Improve OCR accuracy and support multiple OCR engines for redundancy.
- Optimize the performance of the detection and analysis pipeline for faster real-time results.

## Contributors

- [Dev Reddy](https://www.linkedin.com/in/devreddy07)
- [Sharad Chandra Reddy](https://www.linkedin.com/in/sharad-chandra-reddy/)

## License

This project is licensed under the MIT License.

## Acknowledgements

- **MobileNet** for object detection
- **AWS OCR** for text recognition
- **OpenAI** for text analysis
- **Tailwind CSS** for frontend design

## References

Data sets:

1. [Fresh and Stale Classification](https://www.kaggle.com/datasets/swoyam2609/fresh-and-stale-classification)
2. [Fruits and Vegetables Dataset](https://www.kaggle.com/datasets/muhriddinmuxiddinov/fruits-and-vegetables-dataset/data)
3. [Fresh and Stale Images of Fruits and Vegetables](https://www.kaggle.com/datasets/raghavrpotdar/fresh-and-stale-images-of-fruits-and-vegetables/data)
4. [Fruits Fresh and Rotten for Classification](https://www.kaggle.com/datasets/sriramr/fruits-fresh-and-rotten-for-classification)
5. [Mango Detector (Fresh or Rotten)](https://universe.roboflow.com/philippines-mango-classification-4-types-rotten-or-fresh/mango-detector-fresh-or-rotten/dataset/2/download)
6. [NIAID Dataset](https://data.niaid.nih.gov/resources?id=ZENODO_7224689)
7. [Mendeley Dataset - Freshness Detection](https://data.mendeley.com/datasets/xkbjx8959c/1)
8. [Freshness Article - ScienceDirect](https://www.sciencedirect.com/science/article/pii/S2352340922007594)
9. [Mendeley Dataset - Fruits and Vegetables](https://data.mendeley.com/datasets/bdd69gyhv8/1)
10. [Random Images Dataset](https://www.kaggle.com/datasets/ezzzio/random-images)
11. [Random Image Sample Dataset](https://www.kaggle.com/datasets/pankajkumar2002/random-image-sample-dataset?select=data)
12. [Supermarket Groceries Image Dataset](https://www.kaggle.com/datasets/aashithakanagala/supermarket-groceries-image-dataset?select=IMG_20220318_180707.jpg)
13. [Grocery Dataset](https://universe.roboflow.com/new-workspace-wfzw3/grocery-dataset-q9fj2/dataset/5)