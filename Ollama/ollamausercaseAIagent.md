# 🧠 Ollama IT Network Assistant Agent

This repository documents the design and development of a local AI agent built using **Ollama** on Ubuntu.

The goal is to create a **domain-restricted AI assistant** focused specifically on IT networking and Linux system administration.

---

## 🎯 Purpose

The purpose of this project is to build a local AI assistant that:

- Runs fully offline using Ollama
- Specialises only in IT networking and Linux
- Acts as a focused technical assistant rather than a general chatbot
- Helps with learning, troubleshooting, and system administration tasks

---

## 🧩 Core Concept

Instead of using a general-purpose AI model, this project creates a **restricted-domain AI agent** that only responds to:

- Linux (Ubuntu system administration)
- Networking (IP, DNS, routing, ports, firewall rules)
- System diagnostics and troubleshooting
- Command-line tools and system utilities

If the user asks anything outside this scope, the agent should refuse and redirect back to relevant topics.

---

## 🛠️ Phase 1: Basic System Prompt Agent

The simplest version of the agent is created by applying a system prompt directly in Ollama.

Example usage:

ollama run llama3.2:3b

Then apply a system instruction:

You are a strict IT network assistant.

You must ONLY discuss:
- Linux (Ubuntu)
- Networking (IP addresses, DNS, routing, firewalls)
- System administration
- Troubleshooting system and network issues

If the user asks anything outside this scope:
- Politely refuse
- Redirect them back to networking or Linux topics

Keep responses concise, practical, and command-line focused.

---

## 🏗️ Phase 2: Custom Ollama Model (Recommended)

To make the agent reusable and persistent, we define a custom model using a Modelfile.

Modelfile:

FROM llama3.2:3b

SYSTEM """
You are NetAssist, a Linux and networking-focused AI assistant.

Rules:
- Only answer questions about:
  - Linux (Ubuntu system administration)
  - Networking (IP, DNS, routing, firewall configuration)
  - System diagnostics and troubleshooting

- If asked anything outside this scope:
  - Politely refuse
  - Redirect the user back to relevant IT/networking topics

Be concise, practical, and command-line focused.
"""

---

Build the model:

ollama create netassist -f Modelfile

---

Run the model:

ollama run netassist

---

## 🧠 Agent Behaviour Design

This agent is designed to behave as:

- A Linux system administrator assistant
- A networking troubleshooting expert
- A command-line focused IT support tool

It is NOT intended to:

- Provide general knowledge or entertainment
- Answer unrelated topics
- Act as a general-purpose chatbot

---

## 🔒 Scope Control Philosophy

This project explores AI constraint design, where:

- The model is intentionally restricted in scope
- Behaviour is controlled through system prompts
- Outputs are guided toward technical usefulness
- Responses outside domain are discouraged

This creates a more focused and practical AI tool for IT learning and troubleshooting.

---

## 🚀 Future Improvements

Planned enhancements include:

- Integration with Python system diagnostic scripts
- Local knowledge base (RAG system using documents)
- Web UI interface using Open WebUI
- Logging and tracking of network troubleshooting sessions
- Multi-agent system (network specialist, Linux specialist, security assistant)

---

## 📌 Status

Early development phase  
Experimental AI agent design  
Built using Ollama + local LLMs on Ubuntu

---

## 🧭 Goal

To build a local offline IT assistant capable of:

- Diagnosing network issues
- Explaining Linux system behaviour
- Assisting with system administration tasks
- Supporting hands-on learning and experimentation

---

## 📎 Notes

This project is actively evolving. Initial versions focus on prompt-based control, with future upgrades moving toward more advanced agent architectures and system integrations.
