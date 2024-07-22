# Project 3 Speech to text inventory queries
Project Overview: Voice-Activated Store Assistant
Objective: The primary objective of this project is to create a voice-activated assistant capable of handling various product-related queries for a paint store. The assistant can recognize spoken commands, process them, and provide relevant information about the products, including stock levels, prices, and general product details.
Key Features:
Speech Recognition: Utilizing the SpeechRecognition library, the assistant can listen to and understand spoken commands from the user.
Natural Language Processing (NLP): Using the NLTK library, the assistant processes the spoken commands to extract meaningful information and identify relevant actions.
Text-to-Speech: The assistant responds to user queries by converting text responses into speech using the gTTS library.
CSV Inventory Management: Product information is stored in a CSV file, which the assistant reads to retrieve product details like stock levels and prices.
Technologies Used:
SpeechRecognition: For recognizing and transcribing spoken commands.
NLTK: For tokenizing and processing natural language commands.
gTTS: For converting text responses to speech.
Playsound: For playing the generated speech responses.
CSV Module: For reading and managing product inventory data.
Project Structure:
CSV Generation Script: A script that generates a mock inventory CSV file with product names, quantities, and prices.
Voice-Activated Assistant Script: A script that initializes the assistant, listens for commands, processes them, and provides spoken responses based on the product inventory.
Detailed Project Description:
1. CSV Generation Script:
Objective: Create a mock inventory CSV file containing product information.
Process:
Generate random quantities and prices for a predefined list of products.
Write the product information to a CSV file in a specified directory.
2. Voice-Activated Assistant Script:
Objective: Develop an assistant that listens to user commands and responds with relevant product information.
Key Functions:
Listen: Uses the SpeechRecognition library to capture and transcribe spoken commands.
Speak: Converts text responses to speech using the gTTS library and plays them using Playsound.
Process Command: Tokenizes and processes the transcribed commands to determine the user’s intent and extract product names.
Extract Product Name: Matches tokens from the command with product names in the inventory to identify the relevant product.
Respond to Queries: Provides information on product stock levels, prices, and general details based on the processed commands.
Example Commands:
"Find product Regal Interior Flat"
"Check stock of Regal Interior Matte"
"Check price of Regal Interior Flat"
"How much is Regal Interior Flat"
"Give me information about Nylon Polyester Angle 1/4 inch"
Benefits:
Efficiency: Streamlines the process of checking inventory and product information through voice commands.
User-Friendly: Provides a hands-free way to interact with the inventory system.
Scalable: Can be expanded to include more complex queries and additional functionalities.
Potential Enhancements:
Integration with Actual Inventory System: Connect the assistant to a live inventory database for real-time updates.
Expanded NLP Capabilities: Use more advanced NLP techniques to handle a wider range of queries and more complex language structures.
User Authentication: Implement user authentication to restrict access to certain inventory information based on user roles.

## data / processing

## observations



## required library installs
pip install SpeechRecognition
pip install pyaudio
pip install gtts
pip install playsound
pip install nltk

If you encounter issues with pyaudio, you may need to install portaudio first:

- Speech Recognition and Natural Language Processing
- SpeechRecognition Library:
- Official Documentation: SpeechRecognition Library Documentation
- Real Python Tutorial: Speech Recognition Python
- Natural Language Processing with NLTK:
- Official Documentation: NLTK Documentation
- NLTK Book: Natural Language Processing with Python
- Text-to-Speech Conversion
- gTTS (Google Text-to-Speech):
- Official Documentation: gTTS Documentation
- Medium Article: Convert Text to Speech in Python
- Playing Sound in Python
- Playsound Library:
- Official Documentation: Playsound Documentation
- Loading and Working with CSV Files in Python
- Python CSV Module:
- Official Documentation: CSV Documentation
- Real Python Tutorial: Reading and Writing CSV Files in Python
- Putting It All Together
- Real Python:
- Guide on Building Voice Assistants: Python Voice Assistant Guide
- Medium Articles:
- How to Build a Speech Recognition System in Python: Building a Speech Recognition System in Python
- Creating a Voice Assistant with Python: Creating a Voice Assistant
- Courses and Tutorials
- Coursera:
- Natural Language Processing Specialization: NLP Specialization
- edX:
- AI Programming with Python: AI Programming with Python
- Udemy:
- Build a Virtual Assistant with Python: Virtual Assistant Course
- PyPIPyPI
- SpeechRecognition
- Library for performing speech recognition, with support for several engines and APIs, online and offline. (7 kB)
https://pypi.org/project/SpeechRecognition/

PyPIPyPI
playsound
Pure Python, cross platform, single function module with no dependencies for playing sounds. (7 kB)
https://pypi.org/project/playsound/

Python documentationPython documentation
csv — CSV File Reading and Writing
Source code: Lib/csv.py The so-called CSV (Comma Separated Values) format is the most common import and export format for spreadsheets and databases. CSV format was used for many years prior to att...


