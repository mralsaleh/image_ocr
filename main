import os
import base64
from litellm import completion

def encode_image(image_path):
    """Encode image to base64 string"""
    with open(image_path, "rb") as image_file:
        return base64.b64encode(image_file.read()).decode('utf-8')

def extract_text_from_image(image_path, api_key=None):
    """
    Extract text from image using Gemini via LiteLLM
    
    Args:
        image_path: Path to the image file
        api_key: Google API key (or set GEMINI_API_KEY env variable)
    
    Returns:
        Extracted text from the image
    """
    # Set API key if provided
    if api_key:
        os.environ["GEMINI_API_KEY"] = api_key
    
    # Encode image to base64
    base64_image = encode_image(image_path)
    
    # Determine image type
    image_ext = image_path.lower().split('.')[-1]
    mime_type = f"image/{image_ext}" if image_ext in ['png', 'jpeg', 'jpg', 'webp', 'gif'] else "image/jpeg"
    
    # Create message with image
    messages = [
        {
            "role": "user",
            "content": [
                {
                    "type": "text",
                    "text": "Extract all text from this image. Return only the text content, nothing else."
                },
                {
                    "type": "image_url",
                    "image_url": f"data:{mime_type};base64,{base64_image}"
                }
            ]
        }
    ]
    
    # Call Gemini via LiteLLM
    response = completion(
        model="gemini/gemini-1.5-flash",
        messages=messages
    )
    
    # Extract and return text
    return response.choices[0].message.content

def main():
    # Example usage
    image_path = "your_image.png"  # Replace with your image path
    api_key = "YOUR_GEMINI_API_KEY"  # Replace with your API key or set env variable
    
    try:
        extracted_text = extract_text_from_image(image_path, api_key)
        print("Extracted Text:")
        print("-" * 50)
        print(extracted_text)
        print("-" * 50)
    except FileNotFoundError:
        print(f"Error: Image file '{image_path}' not found.")
    except Exception as e:
        print(f"Error: {e}")

if __name__ == "__main__":
    main()
