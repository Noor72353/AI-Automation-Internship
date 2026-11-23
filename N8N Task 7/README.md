# AI Text-to-Video Generator | n8n Automation

An AI-powered text-to-video automation workflow built using **n8n**, **Google Gemini**, and the **Agnes AI Video API**.

Users submit a video idea, select a preferred visual style, and provide their email address. The workflow enhances the video prompt using an AI agent and sends it to a video-generation service. Once a video is generated, the workflow is designed to upload it to Google Drive, create a shareable link, and email that link to the user.

## Project Overview

This project demonstrates how AI models and workflow automation can be combined to build an automated text-to-video generation system.

Instead of manually writing detailed video prompts and managing generated files, users can submit their ideas through a form.

## Features

- **User Input Form:** Collects the user's video description, preferred visual style, and email address.
- **AI Prompt Enhancement:** Uses Google Gemini through an AI Agent to transform simple ideas into detailed video-generation prompts.
- **Multiple Video Styles:** Supports the following styles:
  - Realistic / Cinematic
  - 3D Animation
  - Anime
  - Cartoon
  - Documentary
  - Fantasy
  - Sci-Fi
  - Slow Motion
- **AI Video Generation:** Sends the enhanced prompt to the Agnes AI Video API.
- **Generation Status Checking:** Checks the video-generation task status using an API request.
- **Automated Video Download:** Downloads the generated video when the task is completed.
- **Google Drive Integration:** Uploads the video to Google Drive and creates a shareable link.
- **Email Notification:** Sends the generated video link to the user's submitted email address.

## Workflow Architecture

```text
Form Submission
       |
       v
    AI Agent
       |
       v
Google Gemini Chat Model
       |
       v
Agnes AI Video API (POST)
       |
       v
      Wait
       |
       v
Check Video Status (GET)
       |
       v
     Switch
       |
       +---- Completed
       |        |
       |        v
       |   Download Video
       |        |
       |        v
       |   Upload to Google Drive
       |        |
       |        v
       |   Share Google Drive File
       |        |
       |        v
       |   Send Email
       |
       +---- Failed
       |
       +---- Still Processing
                |
                v
               Wait
```

## Technologies Used

| Technology | Purpose |
|---|---|
| n8n | Workflow automation |
| Google Gemini API | AI prompt enhancement |
| Agnes AI API | Video generation |
| Google Drive API | Video storage and sharing |
| Gmail | Email notifications |
| JSON | Workflow export and configuration |

## Video Generation Configuration

The current workflow is configured to use:

- **Model:** `agnes-video-2.5-flash`
- **Generation Mode:** Text-to-Video
- **Duration:** 5 seconds
- **Resolution:** 720P
- **Aspect Ratio:** 16:9

## Project Structure

```text
N8N Task 7/
│
├── AI-Text-to-Video-Generator.json
└── README.md
```

*The JSON filename above is an example. Use the actual exported workflow filename in your folder.*

## Setup Instructions

1. Install or access an n8n instance.
2. Open the n8n editor.
3. Import the workflow JSON file.
4. Configure the required credentials and API connections.
5. Configure the form fields and workflow settings.
6. Save the workflow.
7. Test the workflow after confirming that the video-generation API is available and its pricing is suitable.

### Required Credentials

The workflow may require:

- Google Gemini API credentials.
- Agnes AI API key.
- Google Drive credentials.
- Gmail credentials.

**Important:** API keys and credentials must be configured privately in n8n. Never publish API keys, passwords, or private tokens in a public GitHub repository.

## Current Project Status

**Development status: Prototype / Testing**

The n8n workflow structure and integrations have been configured. However, the Agnes AI video-generation endpoint has returned a `video queue is full` error during testing.

Successful end-to-end video generation and delivery have therefore not yet been verified.

The workflow requires further testing when the video-generation service is available.

## Future Improvements

- Integrate a reliable video-generation API with suitable free-tier access.
- Add retry handling and maximum polling limits.
- Improve error handling and failure notifications.
- Add more video styles and generation options.
- Improve the user interface and form experience.
- Verify complete automated video delivery.

## Author

**Noorwali Khan**
BS in Computer Science
FUUAST Islamabad, Pakistan

**Project:** AI Text-to-Video Generator
**Platform:** n8n Workflow Automation
