# Ollama Setup Guide — Ubuntu Desktop

> A quick guide to installing and running Ollama on an Ubuntu desktop machine.

**Tested on:**

| Component | Spec |
|-----------|------|
| Machine | HP ProBook 450 G4 |
| OS | Ubuntu Desktop |
| RAM | 8 GB |
| CPU | Intel i5 |

---

## Prerequisites

Open a terminal with:

```
Ctrl + Alt + T
```

---

## 1. Install curl

Some Ubuntu installations do not include curl by default.

**Update package lists:**

```bash
sudo apt update
```

**Install curl:**

```bash
sudo apt install curl -y
```

**Verify installation:**

```bash
curl --version
```

---

## 2. Install Ollama

Run the official installation script:

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

**Verify Ollama is installed:**

```bash
ollama --version
```

---

## 3. Download and Run Your First Model

### Llama 3.2 — Recommended for 8 GB RAM

```bash
ollama run llama3.2:3b
```

> The first run downloads the model automatically. Once downloaded, you can begin chatting immediately.

**Example prompts to try:**

```
Explain how Linux permissions work.
Write a Bash script that monitors disk usage.
Teach me Python basics.
```

---

### Mistral — Alternative Model

```bash
ollama run mistral
```

Compare responses and performance with Llama.

---

## 4. Manage Models

**List all downloaded models:**

```bash
ollama list
```

Example output:

```
NAME              ID              SIZE
llama3.2:3b       xxxxxxxx        2.0 GB
mistral:latest    xxxxxxxx        4.1 GB
```

**Update a model to the latest version:**

```bash
ollama pull llama3.2
```

```bash
ollama pull mistral
```

**Remove a model:**

```bash
ollama rm model-name
```

---

## 5. Exit a Chat Session

Press `Ctrl + D` or type:

```
/bye
```

---

## System Information Commands

Useful for checking your hardware before choosing a model.

```bash
# CPU
lscpu | grep "Model name"

# RAM
free -h

# Graphics hardware
lspci | grep -E "VGA|3D|Display"

# Ubuntu version
cat /etc/os-release
```

---

## Recommended Next Steps

**[Open WebUI](https://openwebui.com)** — a ChatGPT-style web interface for your local models.

**Useful things to try with local AI:**

- Linux administration
- Bash scripting
- Learning Python
- Summarising documents
- Offline AI assistance
- Private note-taking

---

## Notes for 8 GB RAM Systems

| Category | Models |
|----------|--------|
| **Recommended** | Llama 3.2 3B, small Gemma models, small Qwen models |
| **Usable (slower)** | Mistral 7B, other 7B class models |
| **Not recommended** | 14B+ models, multiple models simultaneously |

---

## Cheat Sheet

| Action | Command |
|--------|---------|
| Install Ollama | `curl -fsSL https://ollama.com/install.sh \| sh` |
| Run a model | `ollama run llama3.2:3b` |
| List models | `ollama list` |
| Update a model | `ollama pull llama3.2` |
| Remove a model | `ollama rm model-name` |
| Check version | `ollama --version` |
