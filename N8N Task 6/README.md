# AI Text-to-Image Generator | n8n Automation

An AI-powered text-to-image generation system built with **n8n**, **Google Gemini**, and **Cloudflare Workers AI**. Users can submit a simple idea through a web form, select an image style, and automatically receive their generated image through email.

The workflow transforms short text prompts into detailed AI image prompts, generates images, uploads them to Google Drive, configures sharing permissions, and emails the image link to the user.

## Project Overview

This project demonstrates how AI services and workflow automation can be integrated to build a simple, user-friendly image-generation application without developing a traditional frontend or backend from scratch.

Users only need to:
1. Open the image-generation form.
2. Enter an image idea or a few keywords.
3. Select their preferred image style.
4. Enter their email address.
5. Submit the form.

The system handles the remaining process automatically.

## Features

- **Simple Web Form:** Users can generate images using a straightforward form.
- **AI Prompt Enhancement:** Google Gemini expands short user inputs into detailed, creative image-generation prompts.
- **Multiple Image Styles:** Users can select from six available styles:
  - Realistic
  - Anime
  - 3D Render
  - Cyberpunk
  - Cartoon
  - Cinematic
- **AI Image Generation:** Cloudflare Workers AI with FLUX.1 Schnell generates images from the enhanced prompts.
- **Automatic File Conversion:** Converts the generated Base64 image data into an image file.
- **Google Drive Integration:** Automatically uploads generated images to Google Drive.
- **Automatic Sharing Permissions:** Configures image access as Anyone with the link – Viewer.
- **Email Delivery:** Automatically sends the generated image link to the email address provided in the form.
- **End-to-End Automation:** The complete process runs automatically after form submission.

## Workflow Architecture

The automation follows this sequence:

```text
User Opens Web Form
        |
        v
   Form Trigger
        |
        v
      AI Agent
   (Google Gemini)
        |
        v
  Prompt Enhancement
        |
        v
   HTTP Request
 (Cloudflare Workers AI)
        |
        v
  Image Generation
 (FLUX.1 Schnell)
        |
        v
   Convert to File
        |
        v
    Upload File
   (Google Drive)
        |
        v
     Share File
 (Anyone - Viewer)
        |
        v
  Send a Message
      (Gmail)
        |
        v
 User Receives Image Link
```

## Technologies Used

| Technology | Purpose |
|---|---|
| n8n | Workflow automation and integration |
| Google Gemini | AI prompt enhancement |
| Cloudflare Workers AI | AI image generation |
| FLUX.1 Schnell | Text-to-image generation model |
| Google Drive | Image storage and hosting |
| Gmail | Automated email delivery |
| VS Code | Project development and documentation |
| GitHub | Version control and project hosting |

## How It Works

### 1. User Input
The Form Trigger collects three inputs:
- Image prompt
- Preferred image style
- Email address

### 2. AI Prompt Enhancement
The AI Agent uses Google Gemini to transform the user's short idea into a detailed image-generation prompt while following the selected visual style.

### 3. Image Generation
An HTTP Request node sends the enhanced prompt to the Cloudflare Workers AI API, which generates an image using FLUX.1 Schnell.

### 4. Image File Conversion
The generated image is initially returned as Base64 data. The Convert to File node converts it into a downloadable image file.

### 5. Google Drive Upload
The generated image is automatically uploaded to the connected Google Drive account.

### 6. Automatic Sharing
The Share File node configures the file permissions:
- Access type: Anyone
- Permission: Reader (Viewer)

This allows recipients to open and download the image using its link without requesting access.

### 7. Email Delivery
The Gmail node sends an automated email to the address submitted through the form, containing the generated image link.

## Requirements

To recreate this project, you need:

- An n8n account or self-hosted n8n installation.
- A Google Gemini API key.
- A Cloudflare account with access to Workers AI.
- A Google account for Google Drive integration.
- A Gmail account for email delivery.

## Setup Instructions

1. Clone or download this repository.
2. Open the project in n8n.
3. Import the exported workflow JSON file.
4. Configure your Google Gemini credentials.
5. Configure the Cloudflare Workers AI API credentials and endpoint.
6. Connect your Google Drive account.
7. Connect your Gmail account.
8. Test the workflow using the form.
9. Activate the workflow and share its production form URL.

**Important:** Configure your own API credentials. Never publish API keys, access tokens, passwords, or private credentials on GitHub.

## Example Use Case

A user submits:

**Image Prompt:** A girl

**Image Style:** Anime

**Email Address:** user@example.com

The AI Agent expands the short idea into a detailed prompt, Cloudflare generates the image, and n8n automatically uploads and shares the image before emailing the link to the user.

## Important Notes

- Generated images are stored in the Google Drive account connected to the workflow.
- Images use the Anyone with the link – Viewer permission, meaning anyone who obtains the link can access the image.
- Google Drive storage is consumed by generated images.
- API usage may be subject to the respective service providers' limits, pricing, and policies.
- The workflow requires valid API credentials and connected Google services to operate.

## Future Improvements

Potential enhancements include:

- Direct email delivery of generated images without Google Drive storage.
- Temporary image hosting with automatic expiration.
- More image-generation models and styles.
- Image resolution and aspect-ratio selection.
- User-specific image history.
- Improved error handling and retry mechanisms.
- Image generation progress notifications.

## Author

**Noorwali Khan**
BS in Computer Science
FUUAST Islamabad, Pakistan

## License

This project is available for educational and personal portfolio purposes. Add a license file if you intend to specify reuse, modification, or distribution permissions.
