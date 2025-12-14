### Automated Recruitment Agent (AI-Powered)
##  Project Overview
This project is an automation system built using n8n that utilizes Artificial Intelligence (AI) to automatically evaluate and score incoming resumes (CVs) against a specific Job Description. The goal is to increase the efficiency of the recruitment process by eliminating manual review of unqualified documents.

## How It Works
The Workflow is a sequential process that is triggered by an event in Google Drive and concludes by storing the data in Google Sheets.

* Trigger: The automation robot monitors a specific folder in Google Drive for new CV files.

* File Retrieval: When a new file (a CV in PDF format) is uploaded, the robot downloads it.

* Text Extraction: The text content of the CV is extracted from the PDF file.

* AI Analysis: The raw CV text is sent to the Groq service (using the llama-3.3-70b-versatile model).

* Scoring: The AI assigns the CV a Score ranging from 1 to 100 and generates a critical Reasoning (Arsyetimi).

* Critical Rule: A strict rule is set in the Prompt that forces the AI to score resumes lacking relevant tech skills or experience between 1 and 10.

* Data Cleaning: The Code in JavaScript node cleans the JSON data returned by the AI, removing unnecessary brackets and quotes.

* Result Storage: The final data (Candidate Name, Score, Reasoning) is automatically added as a new row in Google Sheets.

## Technologies Used
* Automation Platform: n8n

* Artificial Intelligence (AI): Groq API (using the llama-3.3-70b-versatile model)

* Storage & Trigger: Google Drive

* Database (Result Storage): Google Sheets

* Scripting Language (Output Cleanup): JavaScript

## Requirements and Configuration
To execute this workflow, you need the following:

* n8n Instance: An installed and active n8n server.

* Google Account: With full access to Google Drive and Google Sheets.

* Groq API Key: An active API key to connect to the AI model.

## Updating the Prompt
To change the scoring criteria, modify the content section within the HTTP Request (Groq) node. Adjust the Job Description and the critical rule to fit your current recruitment needs.

## How to Use It
* Activate the Workflow: Ensure the toggle switch in n8n is set to Active (Green).

* Upload the CV: Drop the PDF file (the resume) into the Google Drive folder configured as the Trigger (e.g., CV_Inbox).

* View the Result: After 1-2 minutes, the AI's evaluation result will appear as a new row in your linked Google Sheets file.
