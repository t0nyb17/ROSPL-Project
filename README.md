# 🤖 Groq LPU Chatbot: A Full-Stack AI Implementation 🧠

Welcome to the repository for a full-stack, real-time chatbot application! This project features a powerful **Flask REST API** on the backend that communicates with the blazing-fast **Groq LPU Inference Engine** 🚀. The frontend is a sleek, responsive single-page application built from the ground up with **HTML, CSS, and JavaScript**.

---

## 🛠️ Technical Stack

This project is architected with a modern, decoupled frontend and backend. Here’s a look at the technologies that power it:

| Category | Technology / Library | Purpose |
| :--- | :--- | :--- |
| 🐍 **Backend** | **Python 3** | The core language for our powerful server. |
| | **Flask** | A lightweight framework used to build our robust REST API. |
| | **Groq API** | Provides access to the Groq LPU for lightning-fast AI responses. |
| | **python-dotenv** | Manages our environment variables to keep API keys safe and sound. |
| | **Flask-CORS** | Handles Cross-Origin Resource Sharing, letting the frontend and backend talk. |
| 🎨 **Frontend** | **HTML5** | Provides the essential structure and semantics for the app. |
| | **CSS3** | Styles our application with a responsive, glassmorphic design and dynamic themes. |
| | **JavaScript (ES6+)** | Manages the application's state, DOM, and asynchronous API calls. |

---

## ✨ Features

-   **⚡ Real-Time Inferencing:** Leverages the Groq API for incredibly fast, real-time responses from the Llama 3.1 language model.
-   **🧠 Conversation History:** Maintains conversational context by sending the chat history with each new request, allowing for smart, multi-turn dialogues.
-   **🌓 Dynamic Light/Dark Theming:** The UI supports both light and dark modes, and it remembers your choice using `localStorage`.
-   **💎 Glassmorphic UI:** The interface features a modern "frosted glass" effect using the `backdrop-filter` CSS property for a beautiful, layered design.
-   **📱 Responsive Design:** The layout is fully responsive, ensuring a seamless experience on desktops, tablets, and mobile phones.
-   **🌐 Asynchronous Communication:** All communication with the backend is handled asynchronously with the `fetch` API, so the UI never freezes.

---

## 🏗️ System Architecture

### ⚙️ Backend (Flask)

The backend is a monolithic Flask application serving both the static frontend and the core API.

1.  **Static File Serving:** The Flask server is configured to serve the `index.html` and all other static assets (`.css`, `.js`) from the `frontend` directory.
2.  **API Endpoint (`/api/chat`):**
    -   **Method:** `POST`
    -   **Description:** This is the heart of our chatbot. It accepts a JSON payload with the user's message and chat history.
    -   **Process:** It receives the request, constructs a message payload for the Groq API, and sends it off. It then formats the AI's response into a JSON object and sends it back to the frontend.
3.  **Secure Configuration:** The `python-dotenv` library is used to load the `GROQ_API_KEY` from a local `.env` file, keeping our credentials secure.

### 🖥️ Frontend (Vanilla JS)

The frontend is a dynamic Single-Page Application (SPA) that renders all content without ever needing a page reload.

1.  **DOM Manipulation:** The `script.js` file handles all the logic, dynamically creating and appending new message bubbles to the chat window.
2.  **State Management:** A global `conversationHistory` array keeps track of the dialogue, ensuring the AI always knows the context of the conversation.
3.  **API Interaction:** The `sendMessage` function masterfully handles the communication with the backend, sending `POST` requests and processing the JSON responses.
4.  **Polished UX:** Includes a typing indicator while waiting for a response, an auto-resizing textarea, and a theme toggle button that instantly updates the UI.

---

## 🚀 Setup and Installation

Follow these steps to get the project running on your local machine.

### Prerequisites

-   Python 3.8+
-   Git

### 1. Clone the Repository 📂

```bash
git clone [https://github.com/your-username/rospl-project.git](https://github.com/your-username/rospl-project.git)
cd rospl-project
