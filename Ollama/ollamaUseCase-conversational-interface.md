# Ollama User Case — Conversational Interface Setup

### 🦙 Ollama — [/ollama](./ollama/)

A lightweight conversational web interface for interacting with Ollama running locally on an Ubuntu desktop device. No Docker required — designed as a simple test setup for personal use.

---

## Overview

The chosen use case for Ollama on the Ubuntu desktop is a **conversational interface** — a web-based frontend that allows you to send queries to Ollama and receive responses, running entirely locally without any cloud dependency.

---

## Setup (No Docker)

Since this is a personal test setup, we skip the Docker container entirely and run everything directly on the Ubuntu machine.

### Step 1 — Install Python

Python should already be present on Ubuntu, but if not:

```bash
sudo apt-get update
sudo apt-get install python3
```

### Step 2 — Install dependencies

Install Flask, which will serve as the frontend framework:

```bash
pip3 install Flask
```

### Step 3 — Create the app

Create a new file called `app.py` and add the following:

```python
from flask import Flask, request, jsonify

app = Flask(__name__)

@app.route('/converse', methods=['POST'])
def converse():
    user_query = request.json['query']
    # Process the user query using the Ollama conversational AI model
    # Return a response to the frontend
    return jsonify({'response': 'Hello! How can I help you today?'})

if __name__ == '__main__':
    app.run(debug=True)
```

### Step 4 — Create the frontend

Create an `index.html` file for the user interface:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Conversational Interface</title>
</head>
<body>
    <h1>Conversational Interface</h1>
    <input type="text" id="query" placeholder="Type a question or message...">
    <button id="submit">Submit</button>

    <script src="script.js"></script>
</body>
</html>
```

### Step 5 — Create the request handler

Create a `script.js` file to handle sending queries to the API and displaying responses:

```javascript
const queryInput = document.getElementById('query');
const submitButton = document.getElementById('submit');

submitButton.addEventListener('click', (e) => {
    e.preventDefault();
    const userQuery = queryInput.value;
    fetch('/api/converse', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({ query: userQuery })
    })
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error(error));
});
```

### Step 6 — Run the app

Start the Flask server:

```bash
python3 app.py
```

The server will start on port 5000. Open a browser and navigate to:

```
http://localhost:5000/converse
```

---

## Status

🟡 In progress — basic setup documented, further development ongoing

---

## Notes & next steps

- [ ] Wire up the Flask backend to actually call the Ollama API instead of returning a placeholder response
- [ ] Improve the frontend UI
- [ ] Explore adding conversation history / context

---

*Part of [ai-researcharea](../README.md) · Built with Ollama on Ubuntu*
