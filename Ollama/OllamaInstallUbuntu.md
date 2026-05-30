
Ollama Setup Guide for Ubuntu Desktop

A quick guide to installing and running Ollama on an Ubuntu desktop machine.

Tested on:

* HP ProBook 450 G4
* Ubuntu Desktop
* 8 GB RAM
* Intel i5 CPU

⸻

Prerequisites

Open a terminal:

Ctrl + Alt + T

⸻

Install curl

Some Ubuntu installations do not include curl by default.

Update package lists:

sudo apt update

Install curl:

sudo apt install curl -y

Verify installation:

curl --version

⸻

Install Ollama

Run the official installation script:

curl -fsSL https://ollama.com/install.sh | sh

Verify Ollama is installed:

ollama --version

⸻

Download and Run Your First AI Model

Llama 3.2 (Recommended for 8 GB RAM)

ollama run llama3.2:3b

The first run downloads the model automatically.

Once downloaded, you can begin chatting immediately.

Example prompts:

Explain how Linux permissions work.
Write a Bash script that monitors disk usage.
Teach me Python basics.

⸻

Try the Mistral Model

Download and run:

ollama run mistral

Compare responses and performance with Llama.

⸻

View Installed Models

List all downloaded models:

ollama list

Example output:

NAME              ID              SIZE
llama3.2:3b       xxxxxxxx        2.0 GB
mistral:latest    xxxxxxxx        4.1 GB

⸻

Exit a Chat Session

Press:

Ctrl + D

or type:

/bye

⸻

Update a Model

Download the latest version of a model:

ollama pull llama3.2

or

ollama pull mistral

⸻

System Information Commands

Check CPU

lscpu | grep "Model name"

Check RAM

free -h

Check Graphics Hardware

lspci | grep -E "VGA|3D|Display"

Check Ubuntu Version

cat /etc/os-release

⸻

Recommended Next Steps

Install Open WebUI

Provides a ChatGPT-style web interface for local models.

https://openwebui.com

Useful Uses for Local AI

* Linux administration
* Bash scripting
* Learning Python
* Summarising documents
* Offline AI assistance
* Private note-taking

⸻

Notes for 8 GB RAM Systems

Recommended:

* Llama 3.2 3B
* Small Gemma models
* Small Qwen models

Usable but slower:

* Mistral 7B
* Other 7B class models

Not recommended:

* Large 14B+ models
* Multiple AI models running simultaneously

⸻

Ollama Cheat Sheet

Install:

curl -fsSL https://ollama.com/install.sh | sh

Run model:

ollama run llama3.2:3b

List models:

ollama list

Update model:

ollama pull llama3.2

Remove model:

ollama rm model-name

Check version:

ollama --version


