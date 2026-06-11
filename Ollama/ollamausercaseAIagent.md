# Building My First Ollama AI Agent (NetAssist)

## Overview

This guide documents the process used to create my first custom AI agent using Ollama on Ubuntu.

The objective was to create a specialised AI assistant called **NetAssist** that focuses on:

* Linux system administration
* Networking
* System diagnostics
* Troubleshooting

Rather than creating a completely new Large Language Model (LLM), Ollama allows us to create a custom model which layers instructions and behaviour on top of an existing base model.

In this case:

```text
llama3.2:3b
+
Custom System Prompt
=
NetAssist
```

---

# Prerequisites

Ubuntu Desktop with Ollama installed and working.

Verify installation:

```bash
ollama --version
```

Verify the Ollama service is running:

```bash
ollama list
```

---

# Step 1 - Create Project Directory

Create a dedicated location for custom Ollama agents:

```bash
mkdir -p ~/ollama-agents/netassist
```

Move into the directory:

```bash
cd ~/ollama-agents/netassist
```

Confirm location:

```bash
pwd
```

Expected output:

```text
/home/<username>/ollama-agents/netassist
```

---

# Step 2 - Create the Modelfile

Create a new file called `Modelfile`:

```bash
nano Modelfile
```

> **Important:** The file name is exactly `Modelfile` and has no file extension.

---

# Step 3 - Define the Agent

Paste the following content into the Modelfile:

```text
from llama3.2:3b

system """
You are NetAssist, a Linux and networking-focused AI assistant.

Rules:

- Only answer questions about:
  - Linux (Ubuntu system administration)
  - Networking (IP, DNS, routing, firewall configuration)
  - System diagnostics and troubleshooting

- If asked anything outside this scope:
  - Politely refuse.
  - Redirect the user back to Linux, networking, or troubleshooting topics.

Guidelines:

- Prefer command-line solutions.
- Explain commands before giving them.
- Keep answers concise and practical.
- Use Ubuntu examples whenever possible.
- When troubleshooting, work step-by-step and gather evidence before suggesting fixes.
"""
```

Save the file:

```text
Ctrl + O
Enter
Ctrl + X
```

---

# Step 4 - Verify the Modelfile

Check the file contents:

```bash
cat Modelfile
```

or

```bash
cat -n Modelfile
```

The first line should be:

```text
from llama3.2:3b
```

---

# Step 5 - Build the Custom Model

Create the custom Ollama model:

```bash
ollama create netassist -f ~/ollama-agents/netassist/Modelfile
```

Successful output looks similar to:

```text
gathering model components
using existing layer ...
creating new layer ...
writing manifest
success
```

---

# Step 6 - Verify the Model Exists

List installed models:

```bash
ollama list
```

Example output:

```text
NAME                ID              SIZE
netassist:latest    xxxxxxxxxxxx    2.0 GB
llama3.2:3b         xxxxxxxxxxxx    2.0 GB
```

---

# Understanding the Model Size

At first glance it appears that NetAssist is another 2 GB model.

This is not actually the case.

Ollama reuses the underlying model layers.

Conceptually:

```text
llama3.2:3b
      +
NetAssist Instructions
      =
netassist
```

The base model weights are shared, and only a small configuration layer is added.

---

# Step 7 - Run the Agent

Start NetAssist:

```bash
ollama run netassist
```

The custom system instructions are now automatically loaded.

---

# Step 8 - Test the Agent

Example networking question:

```text
How do I find my IP address on Ubuntu?
```

Example DNS question:

```text
How do I check which DNS server Ubuntu is using?
```

Example out-of-scope question:

```text
Who won the 2022 World Cup?
```

Desired behaviour:

```text
I am focused on Linux and networking topics.
Please ask a question related to Ubuntu, networking, or system administration.
```

---

# Future Enhancements

* Stronger scope restrictions
* Network troubleshooting workflows
* Integration with Python diagnostic scripts
* Retrieval-Augmented Generation (RAG)
* Open WebUI integration
* Multi-agent architecture

---

# Lessons Learned

* Ollama custom models are built using Modelfiles.
* Custom models do not duplicate the underlying LLM.
* The base model is reused through shared layers.
* System prompts can be used to create specialised AI agents.
* Building and rebuilding custom agents is fast and lightweight.

---

# Project Status

* ✅ Ollama installed
* ✅ Custom NetAssist model created
* ✅ Agent successfully built and running
* 🚧 Future work planned around diagnostics, automation and RAG integration
