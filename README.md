## **Nexus AI**
### **Overview**

This document describes the architecture of a conversational AI platform that integrates multiple data sources, knowledge base processing, intelligent agents, monitoring, and response storage. The system enables users to create projects, manage data sources, ask questions, and receive responses powered by specialized agents (KB Agent, BI Agent, Monitoring Agent).

The architecture follows a modular, agent-based design with centralized chat history and knowledge storage.

![](https://qubitnexus-knowledge-base-bucket.s3.us-east-2.amazonaws.com/summary_pdfs/doc-imges/NEXUS+AI+APP.jpeg)

![](https://qubitnexus-knowledge-base-bucket.s3.us-east-2.amazonaws.com/summary_pdfs/doc-imges/Tect+Data+FLow.jpg) 

#### **Component Description**
* **User Interaction Layer**  
  * This layer provides the primary entry points for users:  
* **Login** 
  * Authenticates users.  
  * Grants access to chat and project management features.  
* **Chat Page**  
  * Displays chats and connected data sources.  
  * Central workspace for interaction.  
* **Create a Project** 
  * Group chats and associated configurations.  
  * Logical container for knowledge and agent settings.  
* **Create a New Chat** 
  * Starts a new conversation session.  
  * Links to selected data sources and projects.  
* **Ask a Question** 
  * The user submits a query.  
  * Initiates agent selection and decision workflow.  
* **Additional Prompting (Future)**  
  * Optional input to refine agent behavior.  
  * Improves contextual accuracy.

    
* Data Management Layer  
  Manage Datasource (Add, Update, Delete)  
   Supports ingestion and management of structured and semi-structured data:  
    * CSV  
    * Database (e.g., PostgreSQL)  
    * Excel  
    * PDF

  **Note: A selected data source cannot be changed during an active chat session, ensuring consistency and reproducibility of responses.**

* **Chat & Orchestration Layer**  
  This layer orchestrates user input and system processing.  
* **Chat History**  
  * Stores previous interactions.  
  * Maintains context for multi-turn conversations.  
  * Used by agents to improve contextual understanding.  
* **Store Response**  
  * Persists system-generated responses.  
  * May include metadata and decision logs.  
      
* Agent Processing Layer

The system uses specialized agents to handle different types of queries.

* KB Agent (Knowledge Base Agent)  
  * Handles document-based and structured knowledge queries.  
  * Retrieves and processes relevant data from the Knowledge Base (KB).  
  * Stores answers and additional info back into the system.  
* BI Agent (Business Intelligence Agent)  
  * Performs analytical queries.  
  * Executes calculations or structured data operations.  
  * Returns insights derived from data sources.  
* Monitoring Agent  
  * Observes system decisions and responses.  
  * Logs operational metrics.  
  * Validates outputs and ensures compliance or performance tracking.

* Knowledge Base (KB)  
  The KB serves as the structured repository of knowledge.  
  Responsibilities:  
* Store processed data from uploaded sources.  
* Support retrieval operations for KB Agent.  
* Provide context-aware information to BI Agent if required.  
* Maintain structured knowledge indexes.

* Persistence Layer

The system maintains durable storage for:

* Chat history  
* Agent decisions  
* Generated answers  
* Additional metadata

All responses and relevant context are stored to support:

* Auditability  
* Reproducibility  
* Continuous improvement  
* Context-aware follow-up queries

**End-to-End Workflow**

1. The user logs in.  
2. The user selects or manages a data source.  
3. The user creates a project and starts a new chat.  
4. The user submits a question.  
5. The Decision Engine (for now user choosen) determines the appropriate agent.  
6. Selected Agent processes:  
   * Retrieves data from KB (if needed).  
   * Applies analysis or reasoning.  
7. Final response is:  
   * Displayed to the user.  
   * Stored in Chat History.  
   * Stored in persistent storage.
