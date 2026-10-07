# Aletheia

> *A local-first living book for your personal knowledge.*

Inspired by historical commonplace books and the fantasy idea of a tome of infinite knowledge, Aletheia transforms your notes, memories, research, and discoveries into a searchable, conversational archive.

Throughout history, people have kept commonplace books: collections of quotes, observations, ideas, and information that shaped their thinking. These books became personal libraries, but they were limited by paper, organization, and human memory. Modern AI makes it possible to create something closer to the "living books" imagined in fiction.

Unlike traditional note-taking apps or standard AI chat histories, **Aletheia does not simply store information.** It creates a living knowledge archive where an AI librarian helps you rediscover connections between your memories, notes, ideas, research, and experiences. It is a multi-layered approach to information management that allows you to build your own private library—a library that grows with you.

---

## The Aletheia Workflow

The system is built around a deliberate, four-step cycle:

```text
[ Capture ] ──► [ Preserve Faithfully ] ──► [ Store as Durable Knowledge Objects ] ──► [ Retrieve & Explore ]

```

1. **Capture:** Input your raw thoughts, conversations, or excerpts.
2. **Preserve Faithfully:** **The Archivist** converts raw data into structured, self-contained Markdown without distorting meaning.
3. **Store as Durable Knowledge Objects:** **The Binder** (Python script) strips away LLM edge cases, adding immutable IDs, slugs, and precise timestamps before saving them locally.
4. **Retrieve & Explore:** **The Librarian** acts as your conversational interface to navigate, synthesize, and surface connections without rewriting your history.

---

## Why Aletheia is Different (Beyond the Standard RAG Wrapper)

Most modern AI knowledge tools rely on a basic approach: dump raw documents into a vector database, let an LLM parse everything on the fly, and hope for the best. Aletheia is built on a fundamentally different philosophy:

* **The LLM is the Librarian, not the Database:** The AI does not own your knowledge, nor is it the vault itself. It is the intelligent interface that helps you—the owner—navigate your own mind.
* **Complete Data Portability (No Platform Lock-In):** Your knowledge lives on your local machine as clean, standard Markdown files backed by ChromaDB. If you want to switch AI models, swap agent frameworks, or transition to a completely different tool tomorrow, **you do not migrate your knowledge base.** You only change the retrieval and reasoning layer. Your life's accumulated work remains entirely yours, portable and future-proof.
* **Strict Epistemic Fidelity:** The AI is tasked with faithfully retrieving what you recorded, distinguishing carefully between facts, memories, beliefs, and opinions. If an old journal entry states a subjective belief, the Librarian presents it as a belief—it never silently "corrects" your past self with external statistics or training data.
* **Separation of Knowledge and Commentary:** By default, the archive speaks for itself. Any optional external evaluation or analysis is kept strictly separate and only provided when you explicitly ask for it. Retrieval is not commentary.
* **A Note on Responsibility:** Aletheia is designed around the reality that *tools are only as effective as the person wielding them*. It relies on your intentional input and structured prompts to stay accurate.

---

### 1. The Archivist (`archivist.md`)

A strict ingestion engine designed to convert unstructured user input into exactly one self-contained Markdown knowledge document. It expands shorthand for future clarity, categorizes entries cleanly (Fact, Memory, Idea, Quote, etc.), and strips out all conversational noise.

### 2. The Binder (`app.py`)

The deterministic backbone. It takes the Archivist's output, creates filesystem-safe slugs using Python's standard library, generates immutable tracking IDs and ISO timestamps, and writes the final object to disk, preventing LLM-induced file-system errors.

### 3. The Librarian (`librarian.md`)

The custodian and interpreter. It searches the database to answer queries, build chronological timelines, highlight contradictions, and trace patterns across your archive. It anchors every single statement with verifiable document citations (``).

---

## Optional Workflow Recipe: SillyTavern Companion Integration (Experimental)

> *Note: This is an optional, experimental workflow for power users who want a browser-based frontend. Because it involves local server communication between your browser extension, Python, and your file system, make sure your ports and environment match your local configuration.*

For users who want a frictionless experience without manual file-shuffling, Aletheia can be paired with **SillyTavern**:

1. **Install Extension:** Place the 'aletheia-bridge' folder inside the SillyTavern 'public/extensions/' directory
2. **Start The Binder:** Run `app.py` locally to start the ingestion script listener.
3. **Chat with The Archivist:** Load `archivist.md` as a persona in SillyTavern and feed it your raw information.
4. **Capture & Bind:** Use the optional bridge script/extension to pass the generated Markdown text straight to `app.py`. Use the "Archive Last Message" button to do this.
5. **Stored Locally:** The Binder automatically generates slugs, stamps timestamps, and saves the file directly into your `knowledge/` directory.
6. **Query with The Librarian:** Load 'librarian.md' as a seperate persona and then switch over to it in order to search, query, and converse with your living archive (may require revectorizing database, see https://docs.sillytavern.app/usage/core-concepts/data-bank/)

If you need it, there is a "For Dummies" guide on using the SillyTavern Extension: [ST4dum](./guides/ST4dum.md) 

## PLEASE BE AWARE THAT THE PYTHON SCRIPT FOR THE EXTENSION IS DIFFERENT FROM THE ONE IN THE MAIN RELEASE!!!

---

## Getting Started

1. Download the main release and ensure you have Python installed.
2. Load `prompts/archivist.md` and `prompts/librarian.md` into your preferred LLM interface or agent framework.
3. Run `python app.py` to manage your local knowledge objects.

---

## Notes

I understand that manually feeding text files into a python script can be annoying, and I also understand that the provided SillyTavern extension can be a finicky workaround. In the future, I plan on exploring several alternative solutions:

* **Background file watcher daemon (drop-folder ingestion so users never have to manually run the script).
* **Global desktop hotkey capture window.
* **Dedicated browser clipper extension.

I am also open to suggestions!
