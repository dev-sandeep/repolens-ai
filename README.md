## Project outcome

Build a small web app that lets a developer connect a public GitHub repository, ask questions about its code with
file-and-line references, and run a guided issue investigation that produces a proposed fix—not an automatic code
change.

## Designed for
An experienced React/TypeScript engineer who wants demonstrable AI engineering skills, a credible GitHub portfolio,
and something concrete to explain in interviews.

## Important scope note
Twelve hours is enough for a tightly scoped MVP if you keep the repository public, the interface simple, and the
implementation focused. It is not enough to promise a fully production-hardened autonomous coding agent. Treat
deployment, advanced authentication, and broad language support as stretch goals.


### 1. What you are building
Working name: RepoLens AI (rename it if you like).
Primary user: a developer joining an unfamiliar codebase or investigating a bug.
Three core user journeys
■ Understand: paste a public GitHub repository URL and ingest a small, safe subset of its files.
■ Ask: ask a question and receive an answer grounded in retrieved code snippets, with repository paths cited.
■ Investigate: enter a bug report; the assistant searches relevant files, explains likely causes, and suggests a patch or
next steps for a human to review.
Not in the first version
■ No autonomous commits, pull requests, or edits to a real repository.
■ No arbitrary shell commands or running untrusted repository code.
■ No private-repository OAuth integration, team accounts, billing, or complex permissions.
■ No promise that the model always finds the right root cause. Show uncertainty and evidence.

###  2. Recommended architecture
Keep the stack familiar so the AI work—not learning a completely new framework—is the main challenge.
Layer Choice Purpose
Frontend React + TypeScript + Vite Repository URL form, chat, citations, investigation results
Backend Node.js + TypeScript + Express GitHub ingestion, chunking, retrieval, model calls
LLM One provider API with a low-cost model Answer questions and structure investigation results
Retrieval Embeddings + in-memory cosine
similarity for MVP
Find relevant code chunks without operating a vector database
Repository access GitHub REST API or raw files for public
repos
Fetch a limited list of text files; avoid binaries and huge files
Tests Vitest or Jest; pick one Verify chunking, retrieval, and API behavior
Keep costs low: begin with free local development and a public test repository. Model/embedding API calls may cost
money depending on provider and usage. Set a small usage limit, keep API keys on the server, and never commit
secrets.

### 3. Repository structure to aim for
Do not create every folder on day one. Grow toward a structure like this as features arrive:
rep o-lens-ai/
client/ # React + TypeScript UI
server/ # Node + TypeScript API
server/src/ingestion/ # GitHub fetch and file filtering
server/src/rag/ # chunking, embeddings, retrieval
server/src/agent/ # tools and investigation workflow
server/src/routes/ # API routes
docs/architecture.md
README.md
.env.example
.gitignore

###  4. Working rules for all 12 sessions
■ Spend 5 minutes deciding the session's goal; 40 minutes building; 10 minutes testing; 5 minutes writing notes and
committing.
RepoLens AI — 12-session portfolio plan Page 3
■ Keep a working app at the end of each session. If stuck for 15 minutes, reduce scope rather than adding more
libraries.
■ Use one coding assistant if useful, but ask it for small diffs and explanations. Review and run every change.
■ Make a Git commit at the end of each session, even if the feature is small.
■ Do not paste company code, credentials, customer data, or internal documents into public AI tools# repolens-ai
