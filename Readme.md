# Voice-Activated Store Assistant

## Overview
The Voice-Activated Store Assistant is a project designed to streamline the process of querying inventory and product information in a paint store using voice commands. The assistant utilizes speech recognition, natural language processing, and text-to-speech technologies to provide a seamless user experience.

## Features
- **Speech Recognition**: Converts spoken commands into text using the `SpeechRecognition` library.
- **Natural Language Processing**: Processes commands and extracts relevant product information using `NLTK` and `fuzzywuzzy` for accurate product name matching.
- **Text-to-Speech**: Responds to user queries with spoken responses using `gTTS` and `playsound`.
- **Inventory Management**: Retrieves and manages inventory data from a CSV file.

## Technologies Used
- Python
- `SpeechRecognition`
- `gTTS`
- `playsound`
- `NLTK`
- `fuzzywuzzy`
- `gradio`
- CSV

## Installation
1. **Clone the repository**:
   ```sh
   git clone https://github.com/your-repo/voice-activated-store-assistant.git
   cd voice-activated-store-assistant
   ```

2. **Create and activate a virtual environment**:
   ```sh
   python -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   ```

3. **Install dependencies**:
   ```sh
   pip install -r requirements.txt
   ```

## Running the Assistant
1. **Ensure the CSV file with inventory data is in the `Resources` folder**:
   - Example file: `final_inventory.csv`

2. **Run the script**:
   ```sh
   python assistant.py
   ```

3. **Open the Gradio interface**:
   - Follow the link provided in the terminal to access the web interface.
   - Use the microphone to give commands like:
     - "Check stock of WOODLUXE RESTORE"
     - "What is the price of WOODLUXE STAIN REM?"
     - "What is the volume of WOODLUXE CLEAN?"

## Project Structure
- `assistant.py`: Main script containing the assistant logic.
- `requirements.txt`: List of dependencies.
- `Resources/final_inventory.csv`: Sample inventory data.

## Contributing
1. **Fork the repository**.
2. **Create a new branch**: `git checkout -b feature/your-feature`
3. **Commit your changes**: `git commit -m 'Add some feature'`
4. **Push to the branch**: `git push origin feature/your-feature`
5. **Open a pull request**.



---

This README covers the project's key aspects, including setup, usage, and contribution guidelines. Make sure to update any placeholder text (like repository URLs and contact information) with actual details relevant to your project.
