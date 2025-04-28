# Voice Timesheet Automation

A Python application that uses speech recognition to automate timesheet entries.

## Features

- Record audio descriptions of your work activities
- Transcribe speech to text using OpenAI's Whisper model (locally)
- Extract timesheet data (date, time, task) using GPT-4
- Handle multiple activities in a single transcription
- Calculate time elapsed between start and end times
- Save entries to an Excel spreadsheet
- Calculate daily totals automatically
- Fully automated with smart defaults (no manual input required)
- Robust error handling for reliable operation

## Requirements

- Python 3.8+
- Required packages:
  - openai
  - pandas
  - openpyxl
  - sounddevice
  - scipy
  - openai-whisper

## Installation

1. Clone this repository
2. Install the required packages:

```
pip install openai pandas openpyxl sounddevice scipy openai-whisper
```

3. Set up your OpenAI API key:
   - Create a `.env` file based on `.env.example`
   - Add your OpenAI API key

## Usage

1. Run the application:

```
python timesheet.py
```

2. Press Enter to start recording
3. Speak your timesheet entry, for example:
   - "Today is 15-03-25, Friday. I worked from 9.30AM to 5.00PM on the database migration project."
   - "I attended a meeting from 6:00 AM to 8:00 AM, did a project from 9:00 AM to 12:00 PM, and talked with Ashwin from 1:00 PM to 2:00 PM."

4. The application will:
   - Transcribe your speech using Whisper (locally)
   - Extract the date, day, start time, end time, and task using GPT-4
   - Detect multiple activities if present in your transcription
   - Calculate the time elapsed for each activity
   - Add all entries to the Excel file
   - If any information is missing, smart defaults will be used

5. Additional commands:
   - Type "view" to see the current timesheet
   - Type "exit" to quit the application

## Example

Input (speech): "I attended a meeting from 6:00 AM to 8:00 AM, did a project from 9:00 AM to 12:00 PM, and talked with Ashwin from 1:00 PM to 2:00 PM."

Output (Excel entries):
- Entry 1:
  - Date: 15-03-25
  - Day: Saturday
  - Start Time: 6:00 AM
  - End Time: 8:00 AM
  - Time Elapsed: 2hrs
  - Task: Attended a meeting

- Entry 2:
  - Date: 15-03-25
  - Day: Saturday
  - Start Time: 9:00 AM
  - End Time: 12:00 PM
  - Time Elapsed: 3hrs
  - Task: Did a project

- Entry 3:
  - Date: 15-03-25
  - Day: Saturday
  - Start Time: 1:00 PM
  - End Time: 2:00 PM
  - Time Elapsed: 1hr
  - Task: Talked with Ashwin