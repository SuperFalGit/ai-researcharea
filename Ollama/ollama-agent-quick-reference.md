# Ollama Agent Quick Reference

## NetAssist Agent

### Agent Files

```text
~/ollama-agents/netassist/
```

### Modelfile Location

```text
~/ollama-agents/netassist/Modelfile
```

### Edit the Modelfile

```bash
cd ~/ollama-agents/netassist
nano Modelfile
```

### Rebuild the Model

Only required after making changes to the Modelfile.

```bash
ollama create netassist -f ~/ollama-agents/netassist/Modelfile
```

### Run the Agent

```bash
ollama run netassist
```

---

## NAVI Agent

### Agent Files

```text
~/ollama-agents/navi/
```

### Modelfile Location

```text
~/ollama-agents/navi/Modelfile
```

### Edit the Modelfile

```bash
cd ~/ollama-agents/navi
nano Modelfile
```

### Rebuild the Model

Only required after making changes to the Modelfile.

```bash
ollama create navi -f ~/ollama-agents/navi/Modelfile
```

### Run the Agent

```bash
ollama run navi
```

---

## Useful Ollama Commands

### List Installed Models

```bash
ollama list
```

### Show Model Information

```bash
ollama show netassist
```

```bash
ollama show navi
```

### Remove a Model

```bash
ollama rm netassist
```

```bash
ollama rm navi
```

---

## Typical Workflow

### Create Agent

```bash
nano Modelfile
```

```bash
ollama create <agent-name> -f Modelfile
```

### Use Agent

```bash
ollama run <agent-name>
```

### Update Agent

```bash
nano Modelfile
```

```bash
ollama create <agent-name> -f Modelfile
```

```bash
ollama run <agent-name>
```

---

## Important Note

After a reboot or after closing the terminal, the model does **not** need to be rebuilt.

Simply run:

```bash
ollama run netassist
```

or

```bash
ollama run navi
```

The `ollama create` command is only required when changes are made to the Modelfile.
