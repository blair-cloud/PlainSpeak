# PlainSpeak — Offline Form Explainer

PlainSpeak turns a pasted notice or form into a short explanation, a list of requested actions, and the dates or amounts mentioned in the text. Every extracted detail includes a supporting quote so the reader can check it against the source.

The page also supports fictional examples, importing or dropping `.txt` and `.md` files, a live local-model status indicator, and copying or downloading the generated notes.

The app is designed for local use: the browser sends text to this Python server, which sends it to Ollama on the same computer. PlainSpeak does not store documents. Use public or sample text for demos, and verify important details with the document issuer. This is an explanation aid, not legal, financial, or official advice.

## Requirements

- Python 3.10 or newer
- [Ollama for Windows](https://ollama.com/download/windows) installed and running locally
- A model available in Ollama. The default is `gemma3:1b`.

After installing and opening Ollama, open PowerShell and download the default model:

```powershell
ollama pull gemma3:1b
```

If PowerShell says `ollama` is not recognized, close and reopen PowerShell after installing Ollama. The Ollama app needs to be running in the background.

## Run

```powershell
cd path\to\PlainSpeak
python server.py
```

Open [http://127.0.0.1:8000](http://127.0.0.1:8000). Choose one of the sample documents or paste text and select **Explain this document**.

To use another Ollama model, enter its local model name in the page, or set `OLLAMA_MODEL` before starting the server. For a different local Ollama address, set `OLLAMA_URL`. The app binds to `127.0.0.1` by default so it is not exposed to your network.

## What it does and does not do

- Summarizes only the supplied text.
- Extracts actions, dates, and amounts with evidence quotes.
- Asks the model to avoid filling in details that are not stated.
- Keeps the document in memory for the request; it is not written to a file or included in the server's request log.
- Does not verify whether a notice is genuine, interpret the law, or replace advice from the issuing organization.

The model may still make mistakes. Always compare the output with the source document.

## Project notes

- Python standard library server; no app dependencies to install.
- Open-weight model support through Ollama's local API.
- Sample documents are fictional and intended only for demonstration.
