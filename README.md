# Groq LPU Chatbot: Full-Stack Implementation

This repository contains the source code for a full-stack, real-time chatbot application. The backend is powered by a **Flask REST API** that interfaces with the **Groq LPU Inference Engine**, and the frontend is a responsive single-page application built with vanilla **HTML, CSS, and JavaScript**.

---

## Technical Stack

The project is architected with a decoupled frontend and backend, interacting via a RESTful API.

| Category      | Technology / Library                                       | Purpose                                                                                           |
| :------------ | :--------------------------------------------------------- | :------------------------------------------------------------------------------------------------ |
| **Backend** | **Python 3** | Core programming language for the server.                                                         |
|               | **Flask** | A lightweight WSGI web application framework used to build the REST API.                        |
|               | **Groq API** | Provides access to the Groq LPU Inference Engine for fast language model responses. |
|               | **python-dotenv** | Manages environment variables for secure API key handling.                                  |
|               | **Flask-CORS** | Handles Cross-Origin Resource Sharing to allow the frontend to communicate with the API.    |
| **Frontend** | **HTML5** | Provides the core structure and semantics of the web application.                                 |
|               | **CSS3** | Styles the application, implementing a responsive, glassmorphic design with dynamic theming.      |
|               | **JavaScript (ES6+)** | Manages application state, DOM manipulation, and asynchronous API communication (`fetch`).          |

---

## Features

-   **Real-Time Inferencing:** Leverages the Groq API for fast, real-time responses from the Llama 3.1 language model.
-   **Conversation History Management:** The application maintains conversational context by sending the history with each new request, enabling more coherent multi-turn dialogues.
-   **Dynamic Light/Dark Theming:** The UI supports both light and dark modes, with user preferences saved to `localStorage`. The theme is implemented efficiently using CSS Custom Properties (variables).
-   **Glassmorphic UI:** The interface features a modern "frosted glass" effect using the `backdrop-filter` CSS property, creating a visually appealing, layered design.
-   **Responsive Design:** The layout is fully responsive, ensuring a seamless experience across devices from desktops to mobile phones.
-   **Asynchronous Communication:** All communication with the backend is handled asynchronously using the `fetch` API, preventing the UI from freezing during requests.

---

## System Architecture

### Backend (Flask)

The backend is a monolithic Flask application that serves both the static frontend files and the core API endpoint.

1.  **Static File Serving:** The Flask server is configured to serve the `index.html` file from the `frontend` directory as the root endpoint (`/`). All other static assets (`.css`, `.js`) are served from this same directory.
2.  **API Endpoint (`/api/chat`):**
    -   **Method:** `POST`
    -   **Description:** This is the primary endpoint for all chat interactions. It accepts a JSON payload containing the user's message and the conversation history.
    -   **Process:**
        -   The endpoint receives the request and parses the JSON body.
        -   It invokes the `get_groq_response` utility function, which constructs the message payload for the Groq API.
        -   The `groq` Python client sends the request to the Groq LPU Inference Engine.
        -   Upon receiving a successful response, the backend formats it into a JSON object and returns it to the frontend.
        -   Error handling is in place for API communication failures or missing messages.
3.  **Environment Configuration:** The `python-dotenv` library is used to load the `GROQ_API_KEY` from a `.env` file, keeping sensitive credentials out of the source code.

### Frontend (Vanilla JS)

The frontend operates as a Single-Page Application (SPA), dynamically rendering content without requiring page reloads.

1.  **DOM Manipulation:** The `script.js` file contains all the logic for interacting with the DOM. It dynamically creates and appends new message bubbles to the chat container.
2.  **State Management:** A global `conversationHistory` array stores the dialogue. This array is updated after each successful API response and is sent with every new request to maintain context.
3.  **API Interaction:** The `sendMessage` function orchestrates the communication with the backend. It constructs a `POST` request with the user's message and conversation history, sends it to the `/api/chat` endpoint, and processes the JSON response.
4.  **UI/UX Enhancements:**
    -   A typing indicator is displayed while waiting for the API response.
    -   The textarea for user input automatically resizes based on content.
    -   The theme toggle button updates the `<html>` element's class, which triggers the CSS variable overrides for the dark theme.

---

## Setup and Installation

Follow these steps to run the project locally.

### Prerequisites

-   Python 3.8+
-   Git

### 1. Clone the Repository

```bash
git clone [https://github.com/your-username/rospl-project.git](https://github.com/your-username/rospl-project.git)
cd rospl-project
