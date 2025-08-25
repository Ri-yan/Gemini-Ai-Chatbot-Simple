# Gemini-Ai-Chatbot-Simple

## Overview
This project is a **Node.js-based web application** that combines a backend server with real-time communication features. It uses **Express.js** to serve the frontend and **WebSockets** for live, bidirectional communication between client and server.

## Features
- 🚀 **Express.js Server** – Handles API requests and serves static frontend files.  
- 🔌 **WebSocket Integration** – Enables real-time updates using `wss.js`.  
- 💻 **Frontend UI** – Located in `public/index.html`, demonstrating client interaction.  
- 📦 **Modular Codebase** – Core logic split across `main.js`, `server.js`, and `wss.js`.  

## Project Structure
```
.
├── main.js            # Main entry point of the application
├── server.js          # Express.js server configuration
├── wss.js             # WebSocket server implementation
├── public/
│   └── index.html     # Frontend client UI
├── package.json       # Project metadata and dependencies
├── package-lock.json  # Dependency lock file
└── README.md          # Project documentation
```

## Installation
1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd project
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

## Usage
Start the server with:
```bash
node server.js
```

The application will be available at:  
👉 `http://localhost:3000`

---

## Example Usage

### 1. Starting the WebSocket Server
Inside **wss.js**, the WebSocket server handles connections like this:
```js
const WebSocket = require('ws');
const wss = new WebSocket.Server({ port: 8080 });

wss.on('connection', (ws) => {
  console.log('New client connected');
  
  ws.on('message', (message) => {
    console.log(`Received: ${message}`);
    ws.send(`Echo: ${message}`);
  });

  ws.on('close', () => console.log('Client disconnected'));
});
```

### 2. Connecting from the Client (index.html)
In your **public/index.html**, you can connect to the WebSocket server:
```html
<script>
  const socket = new WebSocket("ws://localhost:8080");

  socket.onopen = () => {
    console.log("Connected to WebSocket server");
    socket.send("Hello Server!");
  };

  socket.onmessage = (event) => {
    console.log("Message from server:", event.data);
  };
</script>
```

This will send messages to the server and display responses in the browser console.

---

## Scripts
Add custom npm scripts in `package.json`. Example:
```json
"scripts": {
  "start": "node server.js",
  "dev": "nodemon server.js"
}
```

Run with:
```bash
npm start   # Start normally
npm run dev # Start with auto-reload (requires nodemon)
```

## Technologies Used
- **Node.js**
- **Express.js**
- **WebSockets**
- **HTML5 / JavaScript**





Checkout the original one too : 
https://live.revoltmotors.com/



