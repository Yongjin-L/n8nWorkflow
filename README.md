## n8n Workflows for Educators

Sharing reusable n8n workflows tailored for teaching, research, and personal knowledge workflows.

### Workflows
- **AgenticRAGwithOpenAI**: A basic RAG setup using OpenAI embeddings and an OpenAI LLM. Vector storage uses Supabase.
- **SecondBrain**: Uses Zotero notes and highlights as a RAG knowledge base to build a personal second brain. Detailed walkthrough: [Build a second brain from Zotero highlights with n8n and RAG](https://medium.com/@yongjinL/build-a-second-brain-from-zotero-highlights-with-n8n-and-rag-c761c2887fde).

### Repository Contents
- `AgenticRAGwithOpenAI.json`: Exported n8n workflow for the OpenAI + Supabase RAG pipeline.
- `SecondBrain_byPaper_Ollama.json`: Exported n8n workflow for the Zotero-based second brain.
- `SQL_Supabase`: Supporting SQL or notes for Supabase setup (if included).

## How to Use

### 1) Host or run n8n
- **Cloud**: Create a workspace on n8n Cloud and open the Editor.
- **Docker (recommended locally)**: 
  - Install Docker Desktop
  - Run: `docker run -it --rm -p 5678:5678 -v ~/.n8n:/home/node/.n8n n8nio/n8n:latest`
- **Node.js (local)**: `npx n8n@latest`

Then open the Editor UI (usually `http://localhost:5678`) and sign in.

### 2) Import the workflow JSON
1. In the n8n Editor, click the menu (top-right) → Import from file.
2. Choose either `AgenticRAGwithOpenAI.json` or `SecondBrain_byPaper_Ollama.json` from this repo.
3. Click Import. The workflow should appear in the canvas.

### 3) Configure credentials and environment
- **OpenAI**: Add an API credential with your OpenAI API key. Update any `OpenAI` nodes to use this credential.
- **Supabase (for AgenticRAGwithOpenAI)**: Add `SUPABASE_URL` and `SUPABASE_ANON_KEY` (or service role) as credentials or environment variables, and update the relevant nodes.
- **Zotero (for SecondBrain)**: Ensure your Zotero export/source configuration matches the workflow expectations (e.g., notes/highlights source path or API).
- **Model/Embedding settings**: Adjust model names, temperature, and chunking/embedding params inside the workflow as needed.

### 4) Test and run
1. Use the "Execute Node" button to test nodes step-by-step.
2. Once the full run succeeds, save the workflow.
3. Optionally, enable triggers or schedule executions.

## Notes
- If you change table or index names in Supabase, reflect those in the workflow nodes.
- For large documents, consider batching and backoff to respect rate limits.
- Keep secrets in n8n Credentials, not in nodes directly.

## License
See `LICENSE` for details.