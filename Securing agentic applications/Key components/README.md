# ⚙️ Agentic Application Key Components (OWASP-Based)

This section provides a quick-reference guide to the core components of agentic architectures, based on the **OWASP Securing Agentic Applications Guide**. Understanding these components is crucial for applying appropriate security controls.

## 🧭 Navigation

| Key Component | Description |
| :--- | :--- |
| [KC1 Generative Language Models](#kc1-generative-language-models) | The "brain" responsible for reasoning and generation. |
| [KC2 Orchestration (Control Flow Mechanisms)](#kc2-orchestration-control-flow-mechanisms) | Dictates the agent's overall behavior, flow, and decision-making. |
| [KC3 Reasoning / Planning Paradigm](#kc3-reasoning--planning-paradigm) | Enables strategic thinking and multi-step task solving. |
| [KC4 Memory Modules](#kc4-memory-modules) | Retains short-term and long-term context for coherent interactions. |
| [KC5 Tool Integration Frameworks](#kc5-tool-integration-frameworks) | Extends capabilities by using external APIs, functions, and data stores. |
| [KC6 Operational Environment (Agencies)](#kc6-operational-environment-agencies) | Defines the agent's ability to interact with the external world (e.g., APIs, code, databases). |

---

## KC1 Generative Language Models

The **"brain"** (Cognitive Engine) of the agent, responsible for **understanding, reasoning, planning, and generating responses**.

* **KC1.1 Large Language Models (LLMs):** The core engine (e.g., GPT, Claude, Gemini) used for general reasoning and generation, primarily guided by prompt engineering.
* **KC1.2 Multimodal LLMs (MLLMs):** LLMs capable of processing and/or generating multiple data types (text, images, audio) for broader task variety.
* **KC1.3 Small-Language Model (SLMs):** Smaller, specialized models with fewer parameters, trained on focused datasets for specific tasks.
* **KC1.4 Fine-tuned Models:** LLMs/MLLMs that undergo additional training on specific data to specialize their capabilities, enhance performance, or adopt a persona.

## KC2 Orchestration (Control Flow Mechanisms)

Mechanisms that **dictate the agent's overall behavior, information flow, and decision-making**. 

* **KC2.1 Workflows:** A structured, pre-defined sequence of tasks or steps the agent follows to achieve a goal (linear, conditional, or iterative).
* **KC2.2 Hierarchical Planning:** Multiple agents collaborating via a central **Orchestrator (Router)** that decomposes a complex task and routes sub-tasks to specialized agents.
* **KC2.3 Multi-agent Collaboration:** Multiple agents working together, communicating and coordinating actions to achieve a common, complex goal.

## KC3 Reasoning / Planning Paradigm

Methods used by agents to solve complex, multi-step tasks using **strategic thinking and logical planning**.

* **KC3.1 Structured Planning / Execution:** Decomposing tasks into a formal plan, defining action sequences, and executing them (e.g., Plan-and-Execute).
* **KC3.2 ReAct (Reason + Act):** Dynamically interleaving reasoning steps with actions (tool calls) and updating the reasoning based on feedback.
* **KC3.3 Chain of Thought (CoT):** Enhances reasoning by prompting the LLM to generate step-by-step **thoughts** before arriving at a conclusion.
* **KC3.4 Tree of Thoughts (ToT):** Generalizes CoT by exploring **multiple reasoning paths** in parallel with lookahead and self-evaluation.

## KC4 Memory Modules

Enables the agent to **retain information** (past interactions, knowledge) for coherent and personalized interactions.

| Memory Type | Scope | Security Risk Consideration |
| :--- | :--- | :--- |
| **KC4.1 In agent session** | Single agent, single session | Limits compromise to the current session. |
| **KC4.2 Cross-agent session** | Multiple agents, single session | Compromised agent could affect multiple agents in that session. |
| **KC4.3 In agent cross-session** | Single agent, multiple sessions | Compromised session could compromise the agent's state across sessions. |
| **KC4.4 Cross-agent cross-session** | Multiple agents, multiple sessions | Highest risk: compromise can affect multiple agents and sessions. |
| **KC4.5 In agent cross-user** | Single agent, multiple users | Compromised agent could leak data across multiple users. |
| **KC4.6 Cross-agent cross-user** | Multiple agents, multiple users | Highest risk: compromise can affect multiple agents and users. |

* *Note: Retrieval-Augmented Generation (RAG) using a vector database is a common mechanism for implementing long-term memory.*

## KC5 Tool Integration Frameworks

Allow agents to **extend their capabilities** beyond text by using external **tools** (APIs, functions, data stores) and managing their selection and use.

* **KC5.1 Flexible Libraries / SDK Features:** Code-level building blocks (e.g., LangChain, CrewAI) offering high control but requiring more coding effort.
* **KC5.2 Managed Platforms / Services:** Vendor-provided solutions (e.g., Amazon Bedrock Agents) that simplify setup, handle infrastructure, and manage orchestration.
* **KC5.3 Managed APIs:** Vendor-hosted services (e.g., OpenAI's Assistants API) that manage state and tool orchestration via high-level API calls.

## KC6 Operational Environment (Agencies)

The agent's ability to **interact with, gather, and process information from external environments** through tools and function calls.

* **KC6.1 API Access:**
    * **Limited API Access:** LLM generates *some* parameters to a predefined API call.
    * **Extensive API Access:** LLM generates the *entire* API call (e.g., URL, body, or interactive traversal).
* **KC6.2 Code Execution:**
    * **Limited Code Execution:** LLM generates *some* parameters to a predefined function.
    * **Extensive Code Execution:** Agent runs arbitrary code generated by the LLM.
* **KC6.3 Database Execution:**
    * **Limited DB Execution:** Agent runs specific, parameterized queries with limited permissions (e.g., read-only, limited write scope).
    * **Extensive DB Execution:** Agent generates and runs all CRUD operations with broad permissions.
    * **Agent Memory / Context Data Sources (RAG):** Agent retrieves or updates records in external sources used for RAG context.
* **KC6.4 Web Access Capabilities (web-use):** Agent operates with a browser (risk from untrusted web content and excessive authorization).
* **KC6.5 Controlling PC Operations (PC-use):** Agent operates with the local operating system, including the file system.
* **KC6.6 Operating Critical Systems (e.g., SCADA):** Agent uses LLM to operate systems where unauthorized actions can cause catastrophic failures.
* **KC6.7 Access to IoT Devices:** Unauthorized control over connected IoT devices in the operational environment.

---