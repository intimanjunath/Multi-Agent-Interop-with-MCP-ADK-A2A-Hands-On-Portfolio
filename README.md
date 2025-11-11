# MCP + ADK + A2A Codelabs

This repository reproduces three Google codelabs covering the Model Context Protocol (MCP), the Agent Development Kit (ADK), the Agent-to-Agent (A2A) protocol, and Agent Engine deployment. The work is organized into **two** top-level subdirectories to match the assignment requirement.

## Repository Layout (two top-level folders)

### `adk-multi-agent-image-scoring`
- **Codelab 1:** Create a multi-agent system with ADK, deploy to Agent Engine, and enable A2A.
- Contains the agent definition, environment configuration notes, verification screenshots, and a short write-up.

### `a2a`
- **Codelab 2:** Currency Agent (MCP server → ADK agent → A2A endpoint).
- **Codelab 3:** A2A Purchasing Concierge (two seller agents on Cloud Run, ADK client on Agent Engine).
- Contains subfolders for `currency-agent` and `purchasing-concierge`, each with environment notes, verification screenshots, and short write-ups.

A “videos” note/link appears in each codelab section below and at the end of this file.  
A “code” note: all code and files are attached in Drive and linked here.

---

## Prerequisites

- A Google Cloud project with billing enabled and access to Vertex AI and Cloud Run.
- Ability to use Cloud Shell or a local Python environment.
- Basic familiarity with: ADK (agent authoring and deployment), A2A (agent interop endpoints and discovery), MCP (tooling protocol for agents), and Agent Engine (hosting and lifecycle).

---

## Global Setup — Checklist

- Confirm cloud project and region (recommended: `us-central1`).
- Enable core services used across labs: Vertex AI, Cloud Run, Cloud Build, and related IAM/Artifact services (as prompted by each lab).
- Prepare environment configuration values you will use in multiple places:
  - Google Cloud **project ID**
  - Google Cloud **region**
  - Optional: a unique Cloud Storage **bucket** name (if a codelab uses staging/assets)
  - **Model** configuration values used by your agents (e.g., model names)
- Decide on a consistent naming scheme for deployed services to keep screenshots and videos clear.
- Create a local `screenshots` folder inside each codelab directory to store verification evidence.

---

## Codelab 1 — ADK Multi-Agent → Agent Engine → A2A (Image Scoring)

### Goal
Build a small multi-agent system with ADK, run it locally, deploy to Agent Engine, and verify it exposes or participates in A2A.

### Deliverables in `adk-multi-agent-image-scoring`
- A concise README (this file serves as master; include a short per-folder note pointing back here).
- A plain-English environment section listing variables you set (project, region, storage bucket if applicable, model names, thresholds).
- Screenshots proving:
  - Local dev UI or equivalent proof of an ADK run
  - Agent Engine deployment page showing the agent in a healthy state
  - A2A discovery or readiness (for example, an agent card response screenshot)

### Configuration Values to Record
- Project ID, region
- Any storage bucket names used
- Model names or parameters used by the agent
- Any thresholds or constants referenced by the lab

### Validation Steps *(no commands shown)*
- Confirm the local agent experience appears and responds in the ADK dev UI.
- Confirm the agent is registered and deployed in Agent Engine and appears healthy.
- Confirm an A2A discovery page or agent card is reachable and correctly describes the agent, including name, description, and supported actions if applicable.

### Video
- **YouTube:** <https://youtu.be/Ns9y0ER5XYU>
- **Code Files:** <https://drive.google.com/drive/folders/1YBUsg8hDJ8h-mLJDww18oUbyXn3Xcux2?usp=sharing>

---

## Codelab 2 — Currency Agent (MCP + ADK + A2A)

### Goal
Implement a simple MCP server that exposes a currency tool, build an ADK agent that calls the MCP tool, and expose the agent via A2A. Validate with a basic A2A interaction.

### Deliverables inside `a2a/currency-agent`
- A short per-folder README referencing this master file.
- A plain-English environment section listing values you set (project, region, base URL or port values if relevant).
- Screenshots proving:
  - MCP server functionality test (e.g., a successful currency lookup result)
  - The ADK agent producing an answer that clearly incorporates MCP tool output
  - A successful A2A interaction (e.g., “convert 100 USD to CAD” with the returned result)

### Configuration Values to Record
- Project ID, region
- Any base URL/port used for local testing
- Any environment toggles to use Vertex AI via Google GenAI client libraries

### Validation Steps *(no commands shown)*
- Show an MCP tool call working in isolation.
- Show the ADK agent calling the MCP tool as part of its reasoning chain.
- Show an A2A client interaction hitting the agent and returning a correct conversion example.
- Optional: if deployed to Cloud Run, record the public URL and capture the agent card page if applicable.

### Video
- **YouTube:** <https://youtu.be/oFN9Neo0XYE>
- **Code Files:** <https://drive.google.com/drive/folders/1AF-WvlI72k7AuGLod4k2AN-APzy9WCKa?usp=sharing>

---

## Codelab 3 — A2A Purchasing Concierge (Cloud Run + Agent Engine)

### Goal
Deploy two seller agents as A2A servers (e.g., burger and pizza). Configure an ADK client (“Purchasing Concierge”) that talks to both via A2A, optionally with a simple web UI. Validate end-to-end ordering or menu retrieval across both sellers.

### Deliverables inside `a2a/purchasing-concierge`
- A short per-folder README referencing this master file.
- An environment section listing values you set (project, region, any staging bucket, and the two seller agent URLs).
- Screenshots proving:
  - Each seller agent is deployed to Cloud Run and its agent card (discovery) is reachable at a well-known path
  - The Purchasing Concierge client connected to both seller A2A endpoints successfully
  - A short run showing a menu query and a two-item order spanning both sellers

### Configuration Values to Record
- Project ID, region
- Optional staging bucket name (if the client requires temporary storage)
- The two seller agent URLs and confirmation that each agent card loads with the correct metadata
- Any client settings that reference those URLs

### Validation Steps *(no commands shown)*
- Confirm both sellers are reachable and return valid agent cards.
- Confirm the client is configured with those two URLs.
- Demonstrate the happy path:
  - Ask for menus from both sellers
  - Place an order that includes one item from each seller
  - Capture the resulting confirmation or summary

### Video
- **YouTube:** <https://youtu.be/a4m0D82MobM>
- **Code Files:** <https://drive.google.com/drive/folders/1z3XAhk2wl87OZNGpCYARcU_ceoDIIrQW?usp=sharing>

---

*End of document.*
