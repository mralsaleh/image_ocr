# OCR with LiteLLM and Gemini

A simple Python project that extracts text from images using Google's Gemini AI model through the LiteLLM interface.

## Features

- Extract text from images using OCR (Optical Character Recognition)
- Supports multiple image formats: PNG, JPEG, JPG, WebP, GIF
- Uses Google Gemini 1.5 Flash for fast and accurate text extraction
- Simple and easy-to-use API
- Base64 image encoding for secure processing

## Prerequisites

- Python 3.7 or higher
- Google Gemini API key

## Installation

1. Clone this repository or download the source code

2. Install the required dependencies:

```bash
pip install litellm
```

## Getting Your API Key

1. Visit [Google AI Studio](https://makersuite.google.com/app/apikey)
2. Sign in with your Google account
3. Click "Create API Key"
4. Copy your API key

## Configuration

You can set your API key in two ways:

### Option 1: Environment Variable (Recommended)

```bash
export GEMINI_API_KEY="your_api_key_here"
```

For Windows:
```cmd
set GEMINI_API_KEY=your_api_key_here
```

### Option 2: Pass Directly to Function

```python
extracted_text = extract_text_from_image("image.png", api_key="your_api_key_here")
```

## Usage

### Basic Example

```python
from ocr_litellm_gemini import extract_text_from_image

# Extract text from an image
image_path = "document.png"
text = extract_text_from_image(image_path)
print(text)
```

### Running the Main Script

1. Update the `image_path` variable in the `main()` function
2. Set your API key (via environment variable or in the code)
3. Run the script:

```bash
python ocr_litellm_gemini.py
```

## Example Output

```
Extracted Text:
--------------------------------------------------
This is the text extracted from your image.
It can include multiple lines and paragraphs.
--------------------------------------------------
```

## Supported Image Formats

- PNG (.png)
- JPEG (.jpg, .jpeg)
- WebP (.webp)
- GIF (.gif)

## Error Handling

The script includes error handling for:
- Missing image files
- Invalid API keys
- API connection issues
- Unsupported file formats

## Project Structure

```
.
├── ocr_litellm_gemini.py    # Main OCR script
├── README.md                 # This file
└── your_image.png           # Your test image (not included)
```

## How It Works

1. The image is read and encoded to base64 format
2. The encoded image is sent to Gemini via LiteLLM
3. Gemini's vision model analyzes the image and extracts text
4. The extracted text is returned as a string

## Troubleshooting

### "GEMINI_API_KEY not found" error
- Make sure you've set the API key environment variable or passed it as a parameter

### "Image file not found" error
- Check that the image path is correct
- Use absolute paths if relative paths don't work

### Poor OCR results
- Ensure the image has good quality and contrast
- Try with a clearer or higher resolution image
- Make sure the text in the image is readable

## API Costs

Gemini 1.5 Flash has a free tier with generous limits. Check [Google AI Pricing](https://ai.google.dev/pricing) for current rates.

## License

MIT License - feel free to use this project for personal or commercial purposes.

## Contributing

Contributions are welcome! Feel free to submit issues or pull requests.

## Acknowledgments

- Built with [LiteLLM](https://github.com/BerriAI/litellm)
- Powered by [Google Gemini](https://deepmind.google/technologies/gemini/)

## Contact

For questions or support, please open an issue in the repository.
