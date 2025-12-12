# ⚙️ Agentic Application Key Components (OWASP-Based)

This section provides a quick-reference guide to the core components of agentic architectures, based on the **OWASP Securing Agentic Applications Guide**. Understanding these components is crucial for applying appropriate security controls.

---

## 🧭 Quick Navigation

| Component | Role | Description |
|-----------|------|-------------|
| [KC1](#kc1-generative-language-models) | 🧠 **Brain** | The cognitive engine for reasoning and response generation |
| [KC2](#kc2-orchestration-control-flow-mechanisms) | 🎮 **Control System** | Orchestrates agent behavior and information flow |
| [KC3](#kc3-reasoning--planning-paradigm) | 💭 **Strategic Thinking** | Enables multi-step problem solving and planning |
| [KC4](#kc4-memory-modules) | 💾 **Memory** | Retains context and past interactions |
| [KC5](#kc5-tool-integration-frameworks) | 🔌 **Extensions** | Connects to external APIs, functions, and data |
| [KC6](#kc6-operational-environment-agencies) | 🌍 **Environment** | Defines interaction with the external world |

---

## KC1 Generative Language Models

### 🧠 The Brain: Understanding and Reasoning

The **"brain"** (Cognitive Engine) of the agent, responsible for **understanding, reasoning, planning, and generating responses**.

#### Components:

**KC1.1 Large Language Models (LLMs)**
- The core engine (e.g., GPT, Claude, Gemini)
- Used for general reasoning and generation
- Primarily guided by prompt engineering

**KC1.2 Multimodal LLMs (MLLMs)**
- LLMs capable of processing multiple data types
- Supports: text, images, audio
- Enables broader task variety

**KC1.3 Small-Language Models (SLMs)**
- Smaller, specialized models with fewer parameters
- Trained on focused datasets
- Optimized for specific tasks

**KC1.4 Fine-tuned Models**
- LLMs/MLLMs with additional specialized training
- Enhanced performance on specific data
- Personality and behavior customization

---

## KC2 Orchestration (Control Flow Mechanisms)

### 🎮 The Control System: Behavior and Flow

Mechanisms that **dictate the agent's overall behavior, information flow, and decision-making**.

#### Orchestration Types:

**KC2.1 Workflows**
- Pre-defined sequence of tasks
- Can be: linear, conditional, or iterative
- Guides agents toward specific goals

**KC2.2 Hierarchical Planning**
- Multiple agents with central **Orchestrator (Router)**
- Decomposes complex tasks
- Routes sub-tasks to specialized agents

**KC2.3 Multi-agent Collaboration**
- Multiple agents working together
- Active communication and coordination
- Achieve common, complex goals

---

## KC3 Reasoning / Planning Paradigm

### 💭 Strategic Thinking: Problem Solving

Methods used by agents to solve complex, multi-step tasks using **strategic thinking and logical planning**.

#### Reasoning Approaches:

**KC3.1 Structured Planning / Execution**
- Formal task decomposition
- Defined action sequences
- Example: Plan-and-Execute pattern

**KC3.2 ReAct (Reason + Act)**
- Dynamically interleave reasoning with actions
- Tool calls based on reasoning results
- Feedback-driven reasoning updates

**KC3.3 Chain of Thought (CoT)**
- Step-by-step thinking before conclusions
- Enhanced reasoning transparency
- Improved accuracy and interpretability

**KC3.4 Tree of Thoughts (ToT)**
- Explores **multiple reasoning paths** in parallel
- Lookahead and self-evaluation
- Generalizes Chain of Thought approach

---

## KC4 Memory Modules

### 💾 Information Retention: Context and History

Enables the agent to **retain information** (past interactions, knowledge) for coherent and personalized interactions.

#### Memory Types & Security Considerations:

| Memory Type | Scope | Risk Level | Notes |
|---|---|---|---|
| **KC4.1 In-agent Session** | Single agent, single session | 🟢 Low | Compromises limited to current session |
| **KC4.2 Cross-agent Session** | Multiple agents, single session | 🟡 Medium | Compromised agent affects same-session agents |
| **KC4.3 In-agent Cross-session** | Single agent, multiple sessions | 🟡 Medium | Compromised session affects agent across sessions |
| **KC4.4 Cross-agent Cross-session** | Multiple agents, multiple sessions | 🔴 High | Broadest compromise impact |
| **KC4.5 In-agent Cross-user** | Single agent, multiple users | 🔴 High | Data leakage between users |
| **KC4.6 Cross-agent Cross-user** | Multiple agents, multiple users | 🔴 Critical | Maximum compromise scope |

**💡 Note:** Retrieval-Augmented Generation (RAG) using a vector database is a common mechanism for implementing long-term memory.

---

## KC5 Tool Integration Frameworks

### 🔌 Extending Capabilities: Tools and Integrations

Allow agents to **extend their capabilities** beyond text by using external **tools** (APIs, functions, data stores) and managing their selection and use.

#### Integration Approaches:

**KC5.1 Flexible Libraries / SDK Features**
- Code-level building blocks (LangChain, CrewAI)
- High control over implementation
- Requires more development effort

**KC5.2 Managed Platforms / Services**
- Vendor-provided solutions (Amazon Bedrock Agents)
- Simplified setup and infrastructure management
- Handles orchestration automatically

**KC5.3 Managed APIs**
- Vendor-hosted services (OpenAI's Assistants API)
- State management via API calls
- Tool orchestration handled by provider

---

## KC6 Operational Environment (Agencies)

### 🌍 Real-World Interaction: External Systems

The agent's ability to **interact with, gather, and process information from external environments** through tools and function calls.

#### Environmental Access Types:

**KC6.1 API Access**
```
├── Limited API Access: LLM generates some parameters to predefined calls
└── Extensive API Access: LLM generates entire API calls (URL, body, traversal)
```

**KC6.2 Code Execution**
```
├── Limited Code Execution: LLM generates some function parameters
└── Extensive Code Execution: Agent runs arbitrary LLM-generated code
```

**KC6.3 Database Execution**
```
├── Limited DB Execution: Parameterized queries with restricted permissions
├── Extensive DB Execution: All CRUD operations with broad permissions
└── Agent Memory / Context: Retrieval/updates for RAG context data
```

**KC6.4 Web Access Capabilities (web-use)**
- Agent operates with a browser
- Risks from untrusted web content
- Requires careful authorization controls

**KC6.5 Controlling PC Operations (PC-use)**
- Agent operates with local operating system
- File system access and manipulation
- Significant security implications

**KC6.6 Operating Critical Systems (e.g., SCADA)**
- Agent controls critical infrastructure
- Unauthorized actions can cause catastrophic failures
- Requires extreme security precautions

**KC6.7 Access to IoT Devices**
- Unauthorized control over connected IoT devices
- Operational environment security risks
- Device-level authorization required

---