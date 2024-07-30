# Paxil Voice Assistant Kitty

## Overview
Paxil Voice Assistant Kitty is a speech recognition-based assistant that helps users find information about products in an inventory. The assistant can check stock, provide prices, and give volume information. The project uses Google Text-to-Speech (gTTS), Gradio, and fuzzy string matching to improve product name recognition.

## Setup

### Prerequisites
- Python 3.10
- Required Python libraries:
  - speech_recognition
  - gtts
  - playsound
  - nltk
  - csv
  - os
  - gradio
  - fuzzywuzzy
  - python-Levenshtein

### Installation
1. Clone this repository.
2. Navigate to the project directory.
3. Create and activate a virtual environment:
    ```bash
    python -m venv dev
    source dev/bin/activate
    ```
4. Install the required packages:
    ```bash
    pip install speech_recognition gtts playsound nltk gradio fuzzywuzzy python-Levenshtein
    ```

## Usage
1. Ensure the `final_inventory.csv` file is in the `Resources` folder.
2. Run the Python script:
    ```bash
    python speech_recognition_v4.py
    ```
3. Access the Gradio interface through the provided local or public URL.
4. Use the microphone input to ask questions about product stock, price, or volume.

## Code Description

### Load Inventory
```python
def load_inventory(file_path):
    inventory = {}
    with open(file_path, mode='r') as file:
        reader = csv.DictReader(file)
        for row in reader:
            product = row["product"]
            inventory[product] = {
                "quantity": int(row["quantity"]),
                "volume": row["volume"],
                "price": float(row["price"])
            }
    return inventory
```
- Loads product data from a CSV file and returns it as a dictionary.

### Listen Function
```python
def listen(audio_file_path):
    print(f"Received audio file path: {audio_file_path}")
    recognizer = sr.Recognizer()
    try:
        with sr.AudioFile(audio_file_path) as source:
            audio = recognizer.record(source)
            text = recognizer.recognize_google(audio)
            print(f"Recognized text: {text}")
            return text
    except sr.UnknownValueError:
        print("Error: Could not understand the audio")
        return "Sorry, I did not understand that."
    except sr.RequestError:
        print("Error: Could not request results from Google Speech Recognition service.")
        return "Sorry, the service is down."
    except AssertionError as e:
        print(f"AssertionError: {e}")
        return "Sorry, the audio file is not valid."
```
- Converts audio input to text using Google Speech Recognition.

### Speak Function
```python
def speak(text):
    if not text:
        text = "Sorry, I have nothing to say."
    tts = gTTS(text=text, lang='en')
    filename = "response.mp3"
    tts.save(filename)
    try:
        playsound.playsound(filename)
        print(f"Playing sound: {filename}")
    except Exception as e:
        print(f"Error playing sound: {e}")
    return filename
```
- Converts text to speech and plays the generated audio.

### Process Command
```python
def process_command(command):
    print(f"Processing command: {command}")
    tokens = word_tokenize(command.lower())
    product_name = extract_product_name(command)

    if "hello" in tokens or "Paxil" in tokens:
        response = "Hello, I am Paxil your voice assistant kitty. I am here to help you find information?"
    elif "check" in tokens and "stock" in tokens:
        if product_name in inventory:
            item = inventory[product_name]
            response = f"We have {item['quantity']} {product_name}(s) in stock."
        else:
            response = f"Sorry, we don't have {product_name} in our inventory."
    elif "price" in tokens:
        if product_name in inventory:
            response = f"The price of {product_name} is ${inventory[product_name]['price']}."
        else:
            response = f"Sorry, we don't have {product_name} in our inventory."
    elif "volume" in tokens:
        if product_name in inventory:
            response = f"The volume of {product_name} is {inventory[product_name]['volume']}."
        else:
            response = f"Sorry, we don't have {product_name} in our inventory."
    elif "thank you" in tokens or "goodbye" in tokens:
        response = "You're welcome, please proceed to check out."
    else:
        response = "I'm sorry, I didn't understand that. Can you please repeat?"
    print(f"Response: {response}")
    return response
```
- Processes spoken commands and generates appropriate responses.

### Extract Product Name
```python
def extract_product_name(command):
    command = command.lower()
    best_match, best_score = process.extractOne(command, inventory.keys(), scorer=fuzz.partial_ratio)
    if best_score > 80:
        print(f"Best match: {best_match} with score {best_score}")
        return best_match
    else:
        print(f"No suitable match found for command: {command}")
        return ""
```
- Uses fuzzy string matching to find the best match for the product name in the inventory.

### Assistant Function
```python
def assistant(audio_file_path):
    print(f"Assistant received audio file path: {audio_file_path}")
    command = listen(audio_file_path)
    response = process_command(command)
    audio_response = speak(response)
    return response, audio_response
```
- Main function that coordinates listening, processing, and responding.

### Gradio Interface
```python
iface = gr.Interface(
    fn=assistant,
    inputs=gr.Audio("microphone", type="filepath"),
    outputs=[gr.Textbox(), gr.Audio(type="filepath")]
)
iface.launch(share=True)
```
- Sets up the Gradio interface for the assistant.

## Documentation

### Fuzzy Matching and String Similarity

#### FuzzyWuzzy:
- [Official Documentation: FuzzyWuzzy](https://pypi.org/project/fuzzywuzzy/)
- [Real Python Tutorial: Fuzzy String Matching in Python](https://realpython.com/fuzzy-string-matching-python/)

#### Python-Levenshtein:
- [Official Documentation: python-Levenshtein](https://pypi.org/project/python-Levenshtein/)
- [Stack Abuse Tutorial: Introduction to Fuzzy Matching in Python](https://stackabuse.com/introduction-to-fuzzy-matching-in-python/)

### Speech Recognition and Natural Language Processing

#### SpeechRecognition Library:
- [Official Documentation: SpeechRecognition Library Documentation](https://realpython.com/python-speech-recognition/)
- [Real Python Tutorial: Speech Recognition Python](https://realpython.com/python-speech-recognition/)

#### Natural Language Processing with NLTK:
- [Official Documentation: NLTK Documentation](https://www.nltk.org/)
- [NLTK Book: Natural Language Processing with Python](https://www.nltk.org/book/)

### Text-to-Speech Conversion

#### gTTS (Google Text-to-Speech):
- [Official Documentation: gTTS Documentation](https://gtts.readthedocs.io/en/latest/)
- [Medium Article: Convert Text to Speech in Python](https://towardsdatascience.com/text-to-speech-in-python-64f41f87a4b2)

### Playing Sound in Python

#### Playsound Library:
- [Official Documentation: Playsound Documentation](https://pypi.org/project/playsound/)

### Loading and Working with CSV Files in Python

#### Python CSV Module:
- [Official Documentation: CSV Documentation](https://docs.python.org/3/library/csv.html)
- [Real Python Tutorial: Reading and Writing CSV Files in Python](https://realpython.com/python-csv/)

### Putting It All Together

#### Real Python:
- [Guide on Building Voice Assistants: Python Voice Assistant Guide](https://realpython.com/python-voice-assistant/)

#### Medium Articles:
- [How to Build a Speech Recognition System in Python: Building a Speech Recognition System in Python](https://towardsdatascience.com/building-a-speech-recognition-system-from-scratch-a-beginners-guide-768420dd3e58)
- [Creating a Voice Assistant with Python: Creating a Voice Assistant](https://towardsdatascience.com/build-your-first-voice-assistant-using-python-65d0f2e9992a)
