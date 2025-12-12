# 🏗️ Core Agentic Patterns

> Fundamental architectural patterns used across all agentic frameworks

While the landscape of agentic frameworks (like LangChain, CrewAI, AutoGPT, etc.) is diverse, several fundamental architectural patterns appear consistently. These patterns represent common solutions to core challenges in agent development, including extending capabilities, improving reasoning, and enabling self-correction.

Understanding these core patterns is crucial for security, as they often introduce specific control points and potential vulnerabilities regardless of the overarching framework used.

---

## 📋 Table of Contents

- [Capability Extension Patterns](#capability-extension-patterns)
  - [Tool Use Pattern](#tool-use-pattern)
  - [Retrieval Augmented Generation (RAG) Pattern](#retrieval-augmented-generation-rag-pattern)
- [Self-Improvement Patterns](#self-improvement-patterns)
  - [Reflection Pattern](#reflection-pattern)
- [Security Patterns](#security-patterns)
  - [User Privilege/Auth Assumption Pattern](#user-privilegeauth-assumption-pattern)

---

## Capability Extension Patterns

### Tool Use Pattern

**Concept**

Equips agents with the ability to use external tools, APIs, or functions to extend their capabilities beyond internal knowledge or LLM reasoning. The agent delegates tasks such as data retrieval, calculations, or actions to the appropriate tools.

**Key Components**

- Tool definitions
- Agent reasoning loop capable of selecting and invoking tools
- Integration mechanisms

**Interaction Flow**

*[Figure 1 - Tool Use Pattern Interactions will be inserted here]*

---

### Retrieval Augmented Generation (RAG) Pattern

**Concept**

Enhances LLM-based agents by first retrieving relevant information from an external knowledge base (vector store, database, etc.) based on the user query, and then providing this retrieved context to the LLM along with the original query to generate a more informed and accurate response.

**Key Components**

- Retriever module
- Knowledge base/vector store
- Integration with the LLM prompt

**Interaction Flow**

*[Figure 3 - RAG Pattern will be inserted here]*

---

## Self-Improvement Patterns

### Reflection Pattern

**Concept**

Enables agents to introspect, evaluate their past actions, decisions, or outputs against goals or metrics, and use this self-assessment to refine future strategies or correct errors.

**Key Components**

- Feedback loops
- Evaluation logic
- Mechanisms for the agent to modify its behavior or knowledge

**Interaction Flow**

*[Figure 2 - Reflection Pattern will be inserted here]*

---

## Security Patterns

### User Privilege/Auth Assumption Pattern

Two primary authentication and authorization patterns for secure agent execution:

---

#### Pattern 1: Direct Model Interaction

**Use Case**

When an agent is executing against an API, database, or entity that has a concept of granular user permissions.

**Implementation**

The agent should assume the permission of the user who invoked the agent. This will:
- Enforce granular security controls on the agent
- Prevent it from returning information the user shouldn't have access to
- Block access to other user data or data not relevant to the current action
- Support Just-In-Time (JIT) access and ephemeral access use cases

**Additional Considerations**

If user privileges are not already restricted by a strong "Chinese Wall" model (to prevent information in records from leaking to unrelated records), the agent should track the boundary of the context it is operating on.

**Key Components**

- LLM brain (KC1)
- Execution system for an API (KC6.1, KC6.3, KC6.4)
- Authentication/authorization/IAM system

**Interaction Flow**

*[Figure 4 - User Assumption in Direct Model Interaction will be inserted here]*

---

#### Pattern 2: Direct User Interaction

**Use Case**

When an AI agent is executing tasks that require interaction with a user's browser or computer, and these tasks demand authentication.

**Implementation**

The agent should either:
1. Prompt the user for credentials out-of-band, OR
2. Securely integrate with a trusted password manager

**Benefits**

- Prevents the agent from storing or exposing sensitive credentials
- Ensures that actions taken by the agent are authorized by the user

**Interaction Flow**

*[Figure 5 - Direct User Interaction will be inserted here]*

---

## 🔍 Pattern Selection Guide

| Pattern | Purpose | Security Considerations |
|:--------|:--------|:------------------------|
| **Tool Use** | Extend agent capabilities with external functions | Tool validation, input sanitization, privilege management |
| **RAG** | Enhance responses with external knowledge | Data leakage, context poisoning, unauthorized access |
| **Reflection** | Enable self-correction and improvement | Feedback loop manipulation, goal hijacking |
| **User Auth Assumption** | Secure execution with proper permissions | Privilege escalation, context boundary violations |

---

## 🛡️ Security Best Practices

When implementing these patterns:

1. **Tool Use Pattern**
   - Validate all tool inputs and outputs
   - Implement proper tool access controls
   - Log all tool invocations for audit trails

2. **RAG Pattern**
   - Secure the vector store/knowledge base
   - Implement access controls on retrieved data
   - Validate retrieval results before use

3. **Reflection Pattern**
   - Validate feedback mechanisms
   - Prevent manipulation of evaluation criteria
   - Monitor for goal drift or hijacking

4. **User Auth Patterns**
   - Always enforce least privilege
   - Track context boundaries strictly
   - Never store credentials in agent memory
   - Use secure credential management systems
