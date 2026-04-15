# Nexus AI

## Overview

This document describes the architecture of a conversational AI platform that integrates multiple data sources, knowledge base processing, intelligent agents, monitoring, and response storage. The system enables users to create projects, manage data sources, ask questions, and receive responses powered by specialized agents (KB Agent, BI Agent, Monitoring Agent).

The architecture follows a modular, agent-based design with centralized chat history and knowledge storage.

---

## Architecture Diagrams

### System Overview
![](https://qubitnexus-knowledge-base-bucket.s3.us-east-2.amazonaws.com/summary_pdfs/doc-imges/NEXUS+AI+APP.jpeg)

### Data Flow
![](https://qubitnexus-knowledge-base-bucket.s3.us-east-2.amazonaws.com/summary_pdfs/doc-imges/Tect+Data+FLow.jpg)

---

## Component Description

### 1. User Interaction Layer

This layer provides the primary entry points for users:

| Component | Description |
|-----------|-------------|
| **Login** | Authenticates users and grants access to chat and project management features |
| **Chat Page** | Displays chats and connected data sources; central workspace for interaction |
| **Create a Project** | Groups chats and associated configurations; logical container for knowledge and agent settings |
| **Create a New Chat** | Starts a new conversation session; links to selected data sources and projects |
| **Ask a Question** | The user submits a query; initiates agent selection and decision workflow |
| **Additional Prompting (Future)** | Optional input to refine agent behavior; improves contextual accuracy |

### 2. Data Management Layer

**Manage Datasource** (Add, Update, Delete)

Supports ingestion and management of structured and semi-structured data:

- CSV
- Database (e.g., PostgreSQL)
- Excel
- PDF

> **Note:** A selected data source cannot be changed during an active chat session, ensuring consistency and reproducibility of responses.

### 3. Chat & Orchestration Layer

This layer orchestrates user input and system processing.

| Component | Description |
|-----------|-------------|
| **Chat History** | Stores previous interactions; maintains context for multi-turn conversations; used by agents to improve contextual understanding |
| **Store Response** | Persists system-generated responses; may include metadata and decision logs |

### 4. Agent Processing Layer

The system uses specialized agents to handle different types of queries.

#### KB Agent (Knowledge Base Agent)
- Handles document-based and structured knowledge queries
- Retrieves and processes relevant data from the Knowledge Base (KB)
- Stores answers and additional info back into the system

#### BI Agent (Business Intelligence Agent)
- Performs analytical queries
- Executes calculations or structured data operations
- Returns insights derived from data sources

#### Monitoring Agent
- Observes system decisions and responses
- Logs operational metrics
- Validates outputs and ensures compliance or performance tracking

### 5. Knowledge Base (KB)

The KB serves as the structured repository of knowledge.

**Responsibilities:**
- Store processed data from uploaded sources
- Support retrieval operations for KB Agent
- Provide context-aware information to BI Agent if required
- Maintain structured knowledge indexes

### 6. Persistence Layer

The system maintains durable storage for:

- Chat history
- Agent decisions
- Generated answers
- Additional metadata

All responses and relevant context are stored to support:

- Auditability
- Reproducibility
- Continuous improvement
- Context-aware follow-up queries

---

## End-to-End Workflow

| Step | Action |
|------|--------|
| 1 | The user logs in |
| 2 | The user selects or manages a data source |
| 3 | The user creates a project and starts a new chat |
| 4 | The user submits a question |
| 5 | The Decision Engine (for now user chosen) determines the appropriate agent |
| 6 | **Selected Agent processes:**<br>• Retrieves data from KB (if needed)<br>• Applies analysis or reasoning |
| 7 | **Final response is:**<br>• Displayed to the user<br>• Stored in Chat History<br>• Stored in persistent storage |
