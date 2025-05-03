MediBot: ChatDoctor QA
Overview
MediBot is a medical question-answering chatbot built in Python using a Jupyter notebook. It leverages the chatdoctor_icliniq dataset from Hugging Face to provide answers to medical queries based on fuzzy string matching. The chatbot features a command-line interface, supports multiple exit commands, displays matching scores for transparency, and includes debugging output for the dataset.
Features

Dataset Inspection: Prints the first 10 rows (0–9) of the chatdoctor_icliniq dataset, showing instruction, input, and output fields (truncated for readability).
Fuzzy Matching: Uses fuzzywuzzy to match user questions to dataset entries, with a threshold of 50 for relevant matches.
Score Display: Shows the fuzzy matching score (0–100) for each response.
Flexible Exit Commands: Supports exiting with commands like exit, thank you, bye, quit, done, or thanks (case-insensitive).
Varied Farewell Messages: Randomly selects from messages like "Take care!", "Stay healthy!", or "Farewell!" when exiting.
Error Handling: Robust handling for dataset iteration, type mismatches, and keyboard interrupts.

Prerequisites

Python 3.7+
Jupyter Notebook (or Google Colab for cloud-based execution)
Dependencies:
datasets
fuzzywuzzy
python-Levenshtein (optional, for faster fuzzy matching)
sys
random (standard library)



Installation

Clone the Repository:
git clone https://github.com/your-username/your-repo.git
cd your-repo


Install Dependencies:In a terminal or Colab cell, run:
pip install datasets fuzzywuzzy python-Levenshtein


Open the Notebook:

In Jupyter: jupyter notebook MediBot.ipynb
In Colab: Upload MediBot.ipynb to /content or Google Drive.



Usage

Run the Notebook:

Open MediBot.ipynb in Jupyter or Colab.
Execute the cells in order:
Cell 1: Import libraries.
Cell 2: Load and print rows 0–9 of the dataset.
Cell 3: Define the fuzzy matching function.
Cell 4: Define the chatbot interface.
Cell 5: Run the chatbot.
Cell 6 (optional): Clean notebook metadata for GitHub compatibility.




Interact with the Chatbot:

After running Cell 5, you’ll see:Welcome to MediBot: ChatDoctor-iCliniq QA! Type 'exit', 'thank you', 'bye', 'quit', 'done', or 'thanks' to quit.
Your question:


Enter a medical question (e.g., "I had mumps and now my testes hurt").
The chatbot responds with the match score, matched question (if score > 50), and answer, or a fallback message.
Example:Your question: I had mumps and now my testes hurt
Match Score: 85
Matched Question: Hello doctor,I had mumps five months ago and after that, I started to have an infection in my left testes...
Answer: Hello, Welcome to Chat Doctor forum. I can understand your concern...

Your question: bye
Stay healthy!




Exit the Chatbot:

Type exit, thank you, bye, quit, done, or thanks to exit with a random farewell message.
Press Ctrl+C to interrupt, which outputs "Interrupted by user. Take care!".



Dataset

Source: Malikeh1375/medical-question-answering-datasets, chatdoctor_icliniq split.
Structure:
instruction: Typically "Answer this question truthfully".
input: User’s medical question.
output: Doctor’s response.


Usage: The notebook loads the train split and prints rows 0–9 for inspection.

Google Colab Notes

Saving the Notebook:
Save to /content: File > Save, then File > Download > Download .ipynb and upload to /content.
Save to Google Drive: File > Save a copy in Drive, then copy to /content:from google.colab import drive
drive.mount('/content/drive')
!cp "/content/drive/My Drive/Colab Notebooks/MediBot.ipynb" /content/




Fixing GitHub Rendering:
If you encounter a metadata.widgets error when uploading to GitHub, run this cell to clean the notebook:import json
import os

notebook_file = 'MediBot.ipynb'
if not os.path.exists(notebook_file):
    print(f"Error: File '{notebook_file}' not found in {os.getcwd()}")
    print("Files in directory:", os.listdir())
else:
    with open(notebook_file, 'r') as f:
        nb = json.load(f)
    if 'widgets' in nb.get('metadata', {}):
        del nb['metadata']['widgets']
        print("Removed metadata.widgets")
    else:
        print("No metadata.widgets found")
    with open(notebook_file, 'w') as f:
        json.dump(nb, f, indent=2)
        print(f"Saved cleaned notebook to {notebook_file}")


Download the cleaned notebook and upload to GitHub.



Saving and Pushing to GitHub

Save Files:

Save MediBot.ipynb and README.md to /content in Colab.
Download both: File > Download > Download .ipynb for the notebook, and save README.md as a text file.


Local Machine Push:

Transfer MediBot.ipynb and README.md to your local machine.
Initialize a Git repository:cd /path/to/your/project
git init
git add MediBot.ipynb README.md
git commit -m "Added MediBot chatbot and README"
git remote add origin https://github.com/your-username/your-repo.git
git push -u origin main




Colab GitHub Integration:

Save to Google Drive:from google.colab import drive
drive.mount('/content/drive')
!cp /content/MediBot.ipynb "/content/drive/My Drive/Colab Notebooks/"


Use File > Save a copy in GitHub for the notebook.
Manually upload README.md via GitHub’s web interface.


Verify:

Visit https://github.com/your-username/your-repo.
Ensure MediBot.ipynb renders and README.md displays correctly.



Contributing

Issues: Report bugs or suggest features via GitHub Issues.
Pull Requests:
Fork the repository.
Make changes in a new branch.
Submit a pull request with a clear description.


Ideas:
Add semantic matching for better question-answering.
Implement a widget-based UI with ipywidgets.
Expand farewell messages or exit commands.



License
This project is licensed under the MIT License. See LICENSE for details.
Acknowledgments

Dataset: Provided by Malikeh1375.
Libraries: Thanks to datasets, fuzzywuzzy, and the Python community.

