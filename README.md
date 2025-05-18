# Personal Discovery Chat Hub

A beautiful, labyrinth-themed chat interface created with love for my wife to explore and discover new knowledge through conversation.

![Discovery Chat Hub](https://placeholder-for-screenshot.com)

## Overview

This project provides a simple yet elegant chat interface that connects to an n8n webhook to create a personalized discovery assistant. The web application features:

- A beautiful labyrinth-themed design
- Intuitive chat interface
- Integration with n8n workflows for AI-powered responses
- Responsive design that works on desktop and mobile devices
- Fallback implementation to ensure compatibility across browsers

## Features

- **Elegant UI**: Clean, modern interface with a purple labyrinth theme
- **Responsive Design**: Works seamlessly on all device sizes
- **n8n Integration**: Connects to an n8n webhook for smart responses
- **Fallback Mechanism**: Custom implementation as a backup if the n8n chat widget fails to load
- **Error Handling**: Graceful handling of connection issues and various response formats

## Setup

### Prerequisites

- Web server to host the static files
- An n8n instance with a configured webhook
- Your webhook URL (currently configured to use a Railway-hosted instance)

### Installation

1. Clone this repository to your local machine or server:
   ```
   git clone https://github.com/yourusername/chats.git
   ```

2. Navigate to the project directory:
   ```
   cd chats
   ```

3. Deploy the `site` folder to your web server of choice (Vercel, Netlify, GitHub Pages, etc.)

### Configuration

To configure the chat to use your own n8n webhook:

1. Open `site/index.html`
2. Locate the webhook URL in the JavaScript section:
   ```javascript
   webhookUrl: 'https://primary-production-5417.up.railway.app/webhook/a889d2ae-2159-402f-b326-5f61e90f602e/chat'
   ```
3. Replace it with your own n8n webhook URL

## n8n Workflow Setup

For the chat to function properly, you need an n8n workflow that:

1. Accepts a webhook input with a JSON body containing:
   ```json
   {
     "action": "sendMessage",
     "chatInput": "User's message here"
   }
   ```

2. Processes the request (typically through an AI service like OpenAI, Claude, etc.)

3. Returns a JSON response with one of these properties containing the answer:
   - `response`
   - `text`
   - `message`
   - `content`
   - `answer`
   - Or nested under `result.text` or `data.text`

## Usage

Once set up, simply:

1. Open the website in a browser
2. Type your question in the chat input field
3. Press enter or click the send button
4. Receive a response from the configured n8n workflow

## Browser Compatibility

The chat interface uses a dual-approach for maximum compatibility:

1. It first attempts to load the official n8n chat widget
2. If that fails (due to CORS issues or other browser restrictions), it automatically falls back to a custom implementation that provides the same core functionality

## Customization

You can customize the look and feel by modifying:

- The color scheme in the CSS variables at the top of the HTML file
- The theme properties in the chat widget configuration
- The welcome messages and UI text

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgements

- Made with love for my wonderful wife
- Powered by n8n for workflow automation
- Special thanks to all who helped make this possible
