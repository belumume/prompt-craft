# **Project Plan & Roadmap: Islamic University of Madinah (IU) RAG Application**

Version: 3.2 (Includes OCR Requirement & LLM Evaluation Plan)  
Date: May 4, 2025

## **1\. Introduction**

### **1.1. Vision & Mission**

To develop a state-of-the-art, secure, and user-friendly Retrieval-Augmented Generation (RAG) web application, initially for the Islamic University of Madinah (IU), with the potential for future multi-organizational support. The application will serve as a central, intelligent information resource for stakeholders (students, staff, parents, etc.), providing highly accurate, reliable, fast, and instructionally valuable answers based exclusively on curated institutional knowledge extracted accurately from all source types (including scanned documents via OCR). The mission is to enhance information accessibility through a robust and maintainable system, support administrative efficiency, and establish a foundation for future AI-driven services, with a strong emphasis on bilingual (Arabic/English) support, rapid response times, and trustworthy outputs facilitated by the PydanticAI framework and Instructor library.

### **1.2. Goals & Objectives**

* **Primary Goal:** Deliver a production-ready RAG application, built using PydanticAI, Instructor, and FastAPI, that provides accurate, fast, and reliably structured answers based solely on an internal knowledge base (with text accurately extracted via standard parsing and OCR), with clear source attribution.  
* **Key Objectives:**  
  * Develop a secure FastAPI web application deployable on Render, serving as the backend and API layer.  
  * Implement a robust, modular RAG system using the PydanticAI agent framework for orchestration, tool management, and workflow control, initially leveraging Google's **Gemini 2.5 Pro Preview** as the core LLM, while systematically **evaluating Gemini 2.5 Flash Preview in parallel** to determine the optimal model based on performance and cost.  
  * Utilize the Instructor library for the final generation step to ensure reliably structured, validated output (answer \+ references) conforming to Pydantic models.  
  * Achieve seamless functionality and high-quality responses in both Arabic and English.  
  * Deliver fast response times through efficient pipeline design, streaming capabilities (PydanticAI \+ Instructor), and optimized retrieval.  
  * Create an intuitive, responsive, and trustworthy user interface accessible across all devices, providing streamed responses where possible.  
  * Establish a secure admin-controlled workflow for managing the knowledge base (document uploads, webpage indexing), including accurate text extraction via OCR for image-based documents.  
  * Implement advanced retrieval techniques (hybrid search, metadata filtering, re-ranking) within a PydanticAI tool for optimal context relevance.  
  * Define and utilize quantitative metrics (e.g., RAGAS, DeepEval) and the PydanticAI ecosystem (Pydantic Evals, Logfire) to systematically evaluate and improve RAG performance (accuracy, faithfulness, relevance, speed, impact of OCR quality, and **comparative LLM performance**).  
  * Design an architecture capable of future expansion for personalized data access and multi-tenancy.  
  * Achieve high standards of performance, reliability, security, and maintainability.  
  * Foster a collaborative and efficient development process adhering to the principles outlined in Section 2, emphasizing clarity, testing, and incremental progress.

### **1.3. Scope**

* **In Scope (Phase 1 \- Core PydanticAI RAG):**  
  * FastAPI backend application.  
  * Core PydanticAI Agent encapsulating RAG logic, tool definitions, and workflow.  
  * Instructor integration for the final structured answer generation step.  
  * Advanced Retrieval Tool (within PydanticAI): Implementing hybrid search (sparse \+ dense), metadata filtering, and potentially re-ranking.  
  * **Evaluation Framework:** Setup using **Pydantic Evals** and relevant metrics (RAG Triad), including **comparative LLM evaluation**.  
  * Observability: Integration with Pydantic Logfire for tracing and debugging.  
  * Web-based user interface with streaming support.  
  * Admin interface/mechanism for document upload (PDF, DOCX, TXT initially) and specifying URLs for indexing.  
  * Data ingestion pipeline (parsing, content-aware chunking, embedding) executed via background tasks (Celery), including OCR processing for image-based documents/sources.  
  * Web crawling mechanism (e.g., using Scrapy) triggered by admins/schedule, potentially including OCR for text within images on pages.  
  * Integration with Qdrant Vector Database (self-hosted on Render).  
  * Integration with a high-quality multilingual embedding model (e.g., Voyage, multilingual-e5-large).  
  * Integration with **Gemini 2.5 Pro Preview API (initial)** and **Gemini 2.5 Flash Preview API (for evaluation)** via PydanticAI's model abstraction.  
  * Arabic and English language support.  
  * Display of source references with answers.  
  * Deployment on Render (Web Service, Background Worker, Qdrant Service, Redis).  
  * Security measures (admin auth, API key management).  
  * Comprehensive documentation and testing (unit, integration, RAG evaluation, OCR accuracy evaluation, **LLM comparison evaluation**).  
* **Out of Scope (Phase 1):**  
  * Live internet search for answering queries.  
  * User-specific data access (Phase 2).  
  * Multi-organization support (Phase 3).  
  * DSPy-based prompt optimization (Reserved for potential future phase).  
  * Real-time, continuous web crawling (indexing is periodic/triggered).  
  * User accounts or general user login (only admin login initially).  
* **Future Phases (Planned):**  
  * **Phase 2: Personalized RAG:** Integration with IU authentication, secure access to backend user data APIs (via PydanticAI tools), RAG pipeline adaptation for personalized queries, enhanced authorization.  
  * **Phase 3: Multi-Tenancy:** Architecture refactoring for tenant isolation, tenant management features, scalability optimizations.  
  * **Phase 4 (Optional): DSPy Optimization:** If rigorous evaluation identifies persistent bottlenecks in LLM reasoning/generation quality unattainable via prompt engineering within PydanticAI/Instructor, consider targeted optimization of specific components using DSPy.

## **2\. Guiding Principles & Development Methodology**

This project will adhere to a specific set of principles and a collaborative development model designed for efficiency, quality, and adaptability, leveraging the strengths of PydanticAI and Instructor.

### **2.1. Collaboration Model ("Vibecoding")**

* **Human Role (User):** Acts as the project lead, visionary, and assistant/intern. Provides direction, makes final decisions, performs external tasks (API key setup, cloud configuration, data preparation, metric validation, OCR engine selection/setup, **LLM API access setup**), and confirms/validates steps. Trusts the AI's technical execution based on clear instructions.  
* **AI Role (Agent):** Acts as the expert senior engineer/designer/scientist. Takes decisive technical leadership, synthesizes context, creates detailed plans, executes plans incrementally (including PydanticAI agent configuration, tool implementation, Instructor integration, evaluation setup, OCR integration, **LLM integration/evaluation setup**), seeks confirmation at each step, writes high-quality code, performs self-verification, and manages the technical development flow.  
* **Interaction:** The process is collaborative but AI-driven technically. The user provides goals and constraints, the AI plans and executes step-by-step, and the user validates, enables external actions, and provides necessary data/metrics.

### **2.2. Development Methodology**

* **Systematic RAG Improvement ("Building Great RAG"):** Follow principles from the guide: prioritize data quality (including accurate OCR), implement advanced retrieval, evaluate rigorously, optimize iteratively, ensure production readiness.  
* **PydanticAI Ecosystem:** Leverage PydanticAI for orchestration, Pydantic Evals for evaluation, and Pydantic Logfire for observability and transparency (addressing "Show Me The Prompt" concerns).  
* **Instructor for Reliability:** Use Instructor specifically for the final generation step to guarantee structured, validated output.  
* **Debugging-First Approach:** Prioritize testability, modularity, and clear data flow. Ensure PydanticAI agent components and FastAPI endpoints can be tested independently. Implement comprehensive logging (Logfire). Run tests frequently (unit, integration, evaluation, OCR tests, **LLM comparison tests**).  
* **Incremental & Iterative Development:** Build the application modularly. Follow a strict plan-execute-verify-confirm cycle for each code change.  
* **Context Synthesis:** Before any task, the AI agent must synthesize context from conversation history, project files (@-mentions, open tabs), and this document. Ambiguities must be clarified.  
* **Structured Planning:** Detailed execution plans (\<plan\> tags) are mandatory before any non-trivial code change, outlining goals, files, steps (including PydanticAI/Instructor/OCR/**LLM** specific actions), and verification.  
* **Rigorous Self-Verification:** AI agents must self-review code changes after each step against the plan, quality standards, and potential errors before presenting for confirmation. Verify PydanticAI agent logic, Instructor integration, OCR processing logic, and **LLM interaction logic**.  
* **Code Quality & Standards:** Adhere to Python best practices, FastAPI conventions, PydanticAI patterns, Instructor usage patterns, type hinting, comprehensive commenting, robust error handling, and maintainability.  
* **Documentation:** Maintain thorough, up-to-date documentation: this project plan, code comments/docstrings, Pydantic model definitions, API documentation (auto-generated via FastAPI), RAG evaluation results/reports (**including LLM comparisons**), OCR engine choice rationale, and a Project\_Summary.md file (see Section 10).  
* **Real-World Focus:** Avoid placeholders. The user will provide real API keys, configure services, prepare evaluation data, configure OCR engines, and perform necessary external integrations as directed by the AI agent.  
* **Tool Usage:** Leverage available tools (Web Search, User Interaction) for up-to-date information when needed.  
* **Prompt Flexibility:** While using frameworks, maintain control over prompt construction within PydanticAI, passing clear message structures to Instructor/LLM, avoiding overly restrictive abstractions where possible (aligning with Jason Liu's philosophy).

## **3\. Core Requirements**

### **3.1. Functional Requirements**

* **FR1:** Users (IU Stakeholders) shall be able to submit queries in Arabic or English via a web interface.  
* **FR2:** The system shall generate answers based only on the indexed internal knowledge base, utilizing a PydanticAI agent with advanced retrieval.  
* **FR3:** The system shall provide answers in the user's preferred language (Arabic or English).  
* **FR4:** Generated answers shall be accurate, relevant, and instructional, based on retrieved context.  
* **FR5:** Generated answers shall be reliably structured (answer \+ references) using Instructor and Pydantic models.  
* **FR6:** Administrators shall have a secure mechanism to upload documents (PDF, DOCX, TXT) to the knowledge base.  
* **FR7:** Administrators shall have a secure mechanism to specify IU website URLs for indexing.  
* **FR8:** Administrators shall have a secure mechanism to trigger the indexing process (for uploaded files and specified URLs), managed via background tasks.  
* **FR9:** The system shall periodically re-index specified web URLs based on a configurable schedule or manual trigger.  
* **FR10:** The system shall handle Arabic text correctly throughout the pipeline (ingestion, OCR, indexing, retrieval, generation).  
* **FR11:** The system must provide fast, streamed responses to the user interface where possible.  
* **FR12:** The system must include mechanisms for evaluating RAG performance using **Pydantic Evals** and defined metrics (RAG Triad, **LLM comparison**).  
* **FR13:** The system must implement advanced retrieval techniques (hybrid search, metadata filtering, re-ranking) to find the most relevant text chunks and avoid common retrieval pitfalls.  
* **FR14:** The system must be observable using Pydantic Logfire.  
* **FR15:** The system must perform accurate OCR on image-based documents (e.g., scanned PDFs) and potentially images within web pages during ingestion to extract textual content.

### **3.2. Non-Functional Requirements**

* **NFR1:** **Performance (Latency):** Target sub-10-second perceived response time for typical queries through streaming. Optimize end-to-end latency (retrieval, generation) continuously. OCR during ingestion should be performant enough for background processing.  
* **NFR2:** **Performance (Accuracy):** Strive for the highest possible factual accuracy and faithfulness based only on the provided context (including accurately OCR'd text), measured via evaluation metrics. Aim to minimize hallucinations. **Select LLM based on evaluation of quality, speed, and cost.**  
* **NFR3:** **Scalability:** Architecture (FastAPI, Celery, Qdrant) should handle growth in data volume and user load. OCR processing should scale with ingestion load.  
* **NFR4:** **Reliability:** Application should be stable. Robust error handling. Instructor ensures reliable output structure. OCR process should be reliable.  
* **NFR5:** **Usability:** Intuitive UI/UX.  
* **NFR6:** **Responsiveness:** UI adapts to screen sizes.  
* **NFR7:** **Security:** Secure admin functions, API keys, data. Future phases require user data security.  
* **NFR8:** **Maintainability:** Well-structured FastAPI code and clear, modular PydanticAI agent components. OCR logic should be modular.  
* **NFR9:** **Deployability:** Deployable and manageable on Render.  
* **NFR10:** **Observability:** Pipeline must be traceable and debuggable using Pydantic Logfire.

### **3.3. Technical Requirements**

* **TR1:** Backend Web Framework: **FastAPI** (Python).  
* **TR2:** Core AI Agent Framework: **PydanticAI** (Python).  
* **TR3:** Structured Output Generation: **Instructor** (Python).  
* **TR4:** **LLM:** Initial: **Google Gemini 2.5 Pro Preview**. Plan: **Evaluate Gemini 2.5 Flash Preview in parallel** using Pydantic Evals to determine optimal model based on quality, speed, and cost. Configured in PydanticAI.  
* **TR5:** Deployment Platform: **Render**.  
* **TR6:** Language: **Python**. Standard web technologies (HTML, CSS, JavaScript) for frontend.  
* **TR7:** Database: **Qdrant** Vector Database (self-hosted).  
* **TR8:** Knowledge Base Scope: Restricted to admin-managed sources. No live internet search during query time.  
* **TR9:** Background Tasks: Celery with Redis broker.  
* **TR10:** Web Crawling: Scrapy.  
* **TR11:** Embedding Model: High-quality Multilingual (e.g., Voyage, multilingual-e5-large).  
* **TR12:** Evaluation: **Pydantic Evals**.  
* **TR13:** Observability: **Pydantic Logfire**.  
* **TR14:** **OCR Engine:** Tesseract (with Arabic language pack) / Google Vision AI / AWS Textract / EasyOCR (Evaluate and Select).  
* **TR15:** **Document Parsing:** PyMuPDF, python-docx, **OCR Library/SDK**.

## **4\. Proposed Architecture (PydanticAI & Instructor Centric)**

The architecture uses PydanticAI to orchestrate the RAG workflow within a FastAPI application, leveraging Instructor for the final, reliable generation step, incorporating an OCR component in the ingestion pipeline, and **allowing for evaluation of different LLMs.**

### **4.1. Overall Architecture Diagram**

graph TD  
    subgraph Browser/Client  
        UI\[User Interface (HTML/CSS/JS \+ Streaming)\]  
    end

    subgraph Render Platform  
        subgraph Web Service (FastAPI App)  
            FW\[FastAPI App (Routers, Pydantic Schemas, Streaming Endpoints)\] \--\> PydanticAI\_Agent  
            Auth\[Admin Auth (FastAPI Depends)\]  
            Logfire\_Integration\[Logfire Config\]  
        end

        subgraph PydanticAI Core (within FastAPI process)  
            PydanticAI\_Agent\[PydanticAI Agent Instance (Configurable LLM)\] \--\> RetrievalTool\[Retrieval Tool\]  
            PydanticAI\_Agent \--\> LLM\_Generate\_Call\[LLM Generate Call (uses Instructor)\]  
            RetrievalTool \--\> VDB\_Client\[Vector DB Client (Qdrant)\]  
            RetrievalTool \--\> Embedding\_Client\[Embedding Client\]  
            LLM\_Generate\_Call \-- Patched Client \--\> Instructor\_Client\[Instructor-Patched LLM Client\]  
            Instructor\_Client \--\> LLM\_API\[Selected LLM API (Pro/Flash)\]  
        end

        subgraph Background Worker (Celery)  
            CW\[Celery Worker\] \--\> TaskQ  
            Tasks\[Ingestion Tasks (Load \-\> \*\*OCR?\*\* \-\> Clean \-\> Chunk \-\> Embed \-\> Index, Crawl)\] \--\> VDB\_Client  
            Tasks \--\> Embedding\_Client  
            Tasks \--\> CrawlLib\[Scrapy\]  
            Tasks \--\> OCR\_Component\[OCR Component\] %% Added OCR call  
        end

        subgraph Vector DB Service (Private)  
            VDB\[(Qdrant Vector DB)\] \-- Persistent Disk \--\> Disk1\[(Disk)\]  
        end

        subgraph Redis Service (Render Key Value)  
            TaskQ\[(Redis: Celery Broker/Backend)\] \-- Persistent \--\> Disk2\[(Disk)\]  
        end

        subgraph OCR Component (within Worker or separate service) %% Added OCR  
             OCR\_Component\[OCR Engine/Service Client\] \--\> OCR\_Engine\[OCR Engine (Tesseract/API)\]  
        end  
    end

    subgraph External Services  
        LLM\_API %% Represents Gemini Pro/Flash APIs  
        Embedding\_API\[Embedding Model API/Lib\]  
        Logfire\_Service\[Pydantic Logfire Platform\]  
        OCR\_Engine %% External if cloud service  
    end

    subgraph IU Systems (Future \- Phase 2\)  
        IU\_Auth\[IU Auth System\]  
        IU\_Data\[IU Data APIs (SIS, HR, etc.)\]  
    end

    UI \-- HTTP Request (REST/WebSocket for Streaming) \--\> FW  
    FW \-- Calls \--\> PydanticAI\_Agent

    VDB\_Client \--\> VDB  
    Embedding\_Client \--\> Embedding\_API  
    Instructor\_Client \--\> LLM\_API  
    Logfire\_Integration \--\> Logfire\_Service

    FW \-- Triggers Task \--\> TaskQ  
    FW \-- Authenticates Admin \--\> Auth

    CW \-- Executes \--\> Tasks

    %% Future Connections  
    FW \-.-\> IU\_Auth  
    PydanticAI\_Agent \-.-\> IU\_Data %% (Via Tools in Phase 2\)

*Diagram Note: Added OCR Component and its interaction with Ingestion Tasks. Clarified LLM\_API represents the selected (Pro/Flash) endpoint.*

### **4.2. Frontend (UI)**

* **Technology:** Standard HTML, CSS, JavaScript. Consider a lightweight framework reactive to streaming data (e.g., HTMX, Alpine.js, vanilla JS).  
* **Rendering:** SPA pattern or server-rendered components. **Must support receiving and displaying streamed responses progressively.**  
* **Key Features:** Query input, language handling, **dynamic response display area for streaming**, visible source references, loading/streaming indicators, error handling.  
* **Design:** Responsive, clean, intuitive, accessible, IU branding, trust-building, Arabic RTL support.

### **4.3. Backend (FastAPI)**

* **Purpose:** Handles HTTP requests, serves UI, manages background tasks, hosts the PydanticAI agent.  
* **Structure:** Modular (API Routers, Services, Pydantic Schemas).  
  * **API Routers:** /query (potentially using WebSockets or Server-Sent Events for streaming), /admin. Query endpoint takes user input, calls the PydanticAI agent's streaming method. Admin endpoints handle auth, trigger ingestion tasks.  
  * **PydanticAI Agent Service:** Instantiates and holds the configured PydanticAI Agent. Exposes methods for running the agent (sync/async/stream). Manages dependency injection (e.g., passing Qdrant client to the retrieval tool). **Allows configuration of the underlying LLM (Pro/Flash) for evaluation.**  
  * **Schemas (Pydantic):** Define API request/response models, including models for streaming chunks if applicable.  
* **Configuration:** Pydantic Settings loading from environment variables. Logfire configuration.

### **4.4. PydanticAI Agent & Workflow**

* **Core Component:** An instance of pydantic\_ai.Agent.  
* **Configuration (\_\_init\_\_ or setup):**  
  * model: Configured LLM identifier string (e.g., 'google-gla:gemini-2.5-pro-preview-06-05' or 'google-gla:gemini-2.5-flash-preview-05-20'). **This should be configurable for evaluation.**  
  * tools: List containing the custom RetrievalTool instance.  
  * deps\_type: Pydantic model defining dependencies needed by tools (e.g., Qdrant client, embedding client).  
  * instrument=True: Enable Logfire instrumentation.  
* **Retrieval Tool (@agent.tool):**  
  * A Python function/class implementing the advanced retrieval logic:  
    1. Receive query string from agent.  
    2. (Optional) Perform query transformation/keyword extraction.  
    3. Generate query embedding.  
    4. Perform hybrid search in Qdrant (vector search \+ keyword search \+ metadata filtering).  
    5. (Optional) Apply re-ranking to the results.  
    6. Format the final context chunks.  
    7. Return the context.  
* **Agent Execution Flow (agent.run\_stream):**  
  1. Receive user query.  
  2. (Optional) Pre-processing steps within the agent if needed.  
  3. Agent calls the RetrievalTool to get context.  
  4. Agent constructs the prompt messages (system prompt, retrieved context, user query).  
  5. Agent makes the **final generation call** using an **Instructor-patched LLM client** (instructor.from\_...) with response\_model=FinalAnswer and stream=True (using create\_partial or create\_iterable as appropriate).  
  6. PydanticAI streams the validated, structured output chunks (from Instructor) back to the FastAPI endpoint.

### **4.5. Instructor Integration**

* **Purpose:** Used *only* for the final LLM call within the PydanticAI agent flow to generate the structured answer (FinalAnswer model including answer and references).  
* **Implementation:**  
  * Instantiate the base LLM client (e.g., OpenAI(), GenerativeModel()). **Allow selection between Pro/Flash clients.**  
  * Patch it using Instructor: instructor\_client \= instructor.from\_...(base\_client).  
  * The PydanticAI agent uses this instructor\_client for the LLM\_Generate\_Call step, passing the response\_model and stream=True. Instructor handles schema formatting, validation, retries, and streaming of the structured output.

### **4.6. Data Ingestion Pipeline (Background Tasks)**

* **Trigger:** Admin actions via FastAPI /admin endpoints.  
* **Execution:** Asynchronous via Celery workers.  
* **Steps:** Loading (files/URLs), **OCR Processing (if applicable, using selected engine)**, Cleaning, Content-Aware Chunking, Embedding (using the configured multilingual model), Indexing (into Qdrant, including metadata).  
* **Scheduling (Crawling):** Celery Beat or Render Cron Jobs.

### **4.7. Vector Database**

* **Selection:** **Qdrant** (self-hosted on Render). Chosen for performance and filtering capabilities.  
* **Deployment:** Render Private Service (Docker) \+ Persistent Disk.  
* **Interaction:** Via qdrant-client within the PydanticAI Retrieval Tool and the ingestion pipeline.

### **4.8. LLM & Embeddings**

* **LLM:** Initial: **Google Gemini 2.5 Pro Preview**. Evaluation Target: **Gemini 2.5 Flash Preview**. The specific model used by the PydanticAI agent will be configurable to facilitate comparative evaluation using Pydantic Evals.  
* **Embedding Model:** High-quality Multilingual (e.g., Voyage, multilingual-e5-large), used consistently in ingestion and retrieval tool.

### **4.9. Multilingual Support (Arabic/English)**

* **Strategy:** Direct Multilingual Retrieval (MultiRAG).  
* **Components:** Multilingual embedding model, **selected Gemini model (Pro/Flash)**, correct ingestion handling (UTF-8, accurate Arabic OCR), PydanticAI agent logic potentially adapting prompts based on language, UI RTL support. Evaluation metrics must cover both languages.

## **5\. Technology Stack Summary**

* **Backend Web:** Python, **FastAPI**  
* **Core AI Agent Framework:** **PydanticAI**  
* **Structured Output Generation:** **Instructor**  
* **LLM:** **Google Gemini 2.5 Pro Preview (Initial), Gemini 2.5 Flash Preview (Evaluation Target)**  
* **Embedding Model:** Voyage / multilingual-e5-large (or similar high-quality)  
* **Vector Database:** **Qdrant** (Self-hosted on Render)  
* **Evaluation:** **Pydantic Evals**  
* **Observability:** **Pydantic Logfire**  
* **Data Parsing:** PyMuPDF, python-docx, **Selected OCR Library/SDK**  
* **Web Crawling:** Scrapy  
* **Background Tasks:** Celery (with Redis broker)  
* **Deployment:** Render (Web Service, Background Worker, Qdrant Service, Redis)  
* **Containerization:** Docker  
* **Frontend:** HTML, CSS, JavaScript (streaming-capable)  
* **Dependency Management:** Poetry / PDM

## **6\. UI/UX Design**

* **Principles:** Clarity, Simplicity, Conversational Feel, Responsiveness, Visual Hierarchy, **Real-time Feedback (Streaming)**, Robust Error Handling, Branding Consistency, Trust & Transparency, Accessibility.  
* **Key Elements:** Query input, clear **dynamically updating response display**, visible source references, loading/streaming indicators, language support (RTL), alignment with IU branding.  
* **Trust:** Emphasize source referencing and clear communication of knowledge boundaries.

## **7\. Deployment Strategy (Render)**

* **Services:** Web Service (FastAPI \+ PydanticAI/Instructor), Background Worker (Celery), Private Service (Qdrant \+ Disk), Redis Service. **Ensure OCR dependencies are included in the Background Worker environment.**  
* **Deployment:** Standard Python web service deployment for FastAPI. Docker for Qdrant.  
* **Configuration:** Render Environment Groups, .env files, Pydantic Settings. Logfire token/config. **LLM API Keys (Pro/Flash).** Potentially OCR service keys/config.  
* **Persistence:** Qdrant (Persistent Disk \+ backups), Redis (Persistence enabled).  
* **Networking:** Render Private Networking.  
* **Scaling:** Vertical/Horizontal scaling for Web/Worker. Vertical for Qdrant. **Consider scaling needs for OCR processing if resource-intensive.**  
* **Streaming:** Ensure FastAPI deployment configuration supports persistent connections needed for WebSockets or SSE.

## **8\. Development Roadmap (PydanticAI & Instructor Centric)**

* **Phase 0: Setup & Foundation (Weeks 1-2)**  
  * Project setup (Git, venv, Poetry/PDM).  
  * Render environment provisioning.  
  * FastAPI app skeleton, basic config, health check.  
  * PydanticAI & Instructor Setup: Install libraries. Configure basic PydanticAI Agent (**configurable for Pro/Flash**). Configure base LLM clients (Pro/Flash) and patch with Instructor.  
  * ★ OCR Engine Selection & Setup: Evaluate and select OCR engine. Install dependencies/configure SDKs. Setup basic OCR stub (data/ocr.py).  
  * **Evaluation Planning:** Define initial RAG evaluation metrics (RAG Triad). Plan data collection/synthetic generation strategy using **Pydantic Evals**. Setup **Logfire**. **Plan for comparative LLM evaluation.**  
  * Initial UI mockups (emphasizing streaming display).  
  * Parser/Embedding PoCs.  
* **Phase 1.1: Core Pipeline & Evaluation Setup (Weeks 3-6)**  
  * Implement infrastructure clients (Qdrant, embedding model, OCR client if needed).  
  * Develop PydanticAI Retrieval Tool (basic vector search \+ filtering initially).  
  * Implement core PydanticAI Agent workflow (**using Gemini Pro initially**), calling retrieval tool and then Instructor for structured generation (FinalAnswer model).  
  * Integrate Agent call within FastAPI endpoint (implement streaming response).  
  * Develop basic chat UI capable of handling streamed responses.  
  * Implement basic document ingestion (TXT, DOCX, including OCR step) via admin trigger.  
  * **Evaluation Implementation:** Implement metric functions for **Pydantic Evals**. Prepare/generate initial evaluation dataset.  
  * **Baseline Evaluation:** Run evaluation pipeline with **Gemini Pro** to establish baseline scores. Analyze results using **Logfire**. Focus on English first. Include OCR accuracy check if possible.  
* **Phase 1.2: Advanced Retrieval, Enhanced Ingestion & LLM Comparison (Weeks 7-10)**  
  * Enhance Retrieval Tool: Implement hybrid search (sparse \+ dense), add re-ranking logic. Optimize Qdrant queries.  
  * Implement PDF parsing, content-aware chunking, robust OCR integration.  
  * Implement Scrapy crawler integration (consider OCR for images).  
  * Set up Celery background tasks for full ingestion pipeline.  
  * Integrate final multilingual embedding model.  
  * Arabic Support: Adapt prompts, evaluation metrics (including Arabic OCR), and UI for Arabic/bilingual performance. Re-evaluate with **Gemini Pro**.  
  * **★ LLM Evaluation:** Run comparative evaluation pipeline using **Pydantic Evals** for **Gemini 2.5 Flash Preview** against the Pro baseline. Analyze accuracy, speed, cost trade-offs.  
  * Refine UI streaming behaviour. Implement source referencing display.  
* **Phase 1.3: Admin Interface, LLM Selection & Deployment Prep (Weeks 11-13)**  
  * **★ Final LLM Selection:** Based on evaluation results, decide on the primary LLM (Pro or Flash) for initial production deployment. Configure the PydanticAI agent accordingly.  
  * Develop secure admin interface.  
  * Implement admin authentication.  
  * Refine deployment configuration (render.yaml, Dockerfile, include OCR dependencies/config).  
  * Ensure comprehensive logging via **Logfire**.  
  * Conduct thorough testing (unit, integration, API, **Pydantic Evals with selected LLM**, OCR accuracy tests). Address pitfalls identified in requirements.  
  * Write user and admin documentation.  
* **Phase 1.4: Testing, Optimization & Launch (Weeks 14-16)**  
  * User Acceptance Testing (UAT).  
  * Performance testing (latency optimization for retrieval and streaming with selected LLM). Caching strategies.  
  * Security review.  
  * Final bug fixes and polishing. Final evaluation runs.  
  * Production deployment on Render.  
  * Post-launch monitoring (Logfire) and support plan.  
* **Phase 2 onwards:** As previously defined (Personalization, Multi-Tenancy, potential DSPy optimization).

## **9\. Testing and Debugging Strategy**

* **Unit Testing:** Test individual functions, FastAPI components, PydanticAI tools, utility classes, OCR processing logic using pytest. Mock external dependencies.  
* **Integration Testing:** Test FastAPI endpoints, PydanticAI agent workflow, Instructor calls, interactions with mocked/real infrastructure (Qdrant, LM API (Pro/Flash), OCR service). Use FastAPI's TestClient. Test ingestion pipeline flow including OCR step.  
* **RAG Evaluation (Pydantic Evals):** Rigorously evaluate context relevance, faithfulness, and answer relevance using quantitative metrics. Analyze failures. Test specifically against known pitfalls (indexing/chunking problems, embedding mismatches, poor retriever config/logic). Evaluate impact of OCR errors on downstream RAG quality. **Compare performance (quality, latency, cost) of Gemini 2.5 Pro vs. Gemini 2.5 Flash using evaluation results.**  
* **OCR Accuracy Testing:** Develop specific tests using ground truth data to measure the accuracy of the chosen OCR engine on representative IU documents (especially Arabic).  
* **End-to-End (E2E) Testing:** Test full application flow from UI, including streaming.  
* **Observability (Logfire):** Use Logfire traces extensively during development and production to understand agent behavior, pinpoint latency bottlenecks, debug Instructor validation steps, monitor OCR performance/errors, and monitor overall performance **across different LLMs during evaluation**.  
* **Incremental Testing:** Test after each significant change.  
* **Verification Steps:** AI agent suggests specific verification after each implementation step.  
* **Responsibility Division:** AI agent handles code/local tests; user assists with external services/config/OCR engine setup/**LLM API access**.

## **10\. Documentation Strategy**

* **Project Plan (This Document):** Living document, updated as needed.  
* **Code Comments:** Comprehensive comments, docstrings, clear Pydantic model definitions.  
* **README.md:** Overview, setup, deployment notes.  
* **API Documentation:** Auto-generated by FastAPI.  
* **Architecture Diagrams:** Keep updated.  
* **Evaluation Reports:** Store results from Pydantic Evals, including OCR accuracy reports and **LLM comparison analysis**.  
* **OCR Engine Choice:** Document the selected OCR engine and rationale.  
* **Project Summary File (Project\_Summary.md):**  
  * **Purpose:** Concise summary of current state, recent changes, next steps, blockers.  
  * **Maintenance:** **CRITICAL:** Updated by AI agent at the end of each significant work session/major change. Confirmed by user. **Updates must be incremental**, preserving history while highlighting the latest changes. **Never rewrite completely.**  
  * **Content:** Timestamp, Phase, Summary, Decisions (**including LLM choice rationale**), Next Steps, Blockers, Link to Plan. Include "Latest Updates" section.

## **11\. Security Considerations**

* **Authentication:** Strong admin authentication. Secure integration with IU auth (Phase 2).  
* **Authorization:** Role-based access for admin functions. Fine-grained access control (Phase 2).  
* **Data Protection:** Encryption at rest/transit. Secure handling of PII (Phase 2). Consider sensitivity of documents undergoing OCR.  
* **API Key Management:** Environment variables (Pydantic Settings), Render secrets. **Include LLM (Pro/Flash)** and OCR service keys if applicable.  
* **Input Validation:** FastAPI/Pydantic for API requests. Sanitize queries before passing to PydanticAI/Instructor. Validate uploads.  
* **Dependency Management:** Regularly scan/update (Poetry/PDM), including OCR libraries.  
* **Infrastructure:** Render Private Services. Secure Qdrant deployment. Secure OCR engine deployment/access if self-hosted.  
* **Observability Security:** Ensure Logfire integration doesn't leak sensitive data.  
* **Compliance:** Adhere to IU IT policies and relevant data privacy regulations.

## **12\. AI Agent Collaboration Rules (For Cursor Rules Generation)**

These rules adapt the previous directives for the PydanticAI \+ Instructor workflow, now including OCR and LLM evaluation.

\# IU RAG Application Project Rules (PydanticAI & Instructor Centric v3.2)

\#\# Core Directives

1\.  \*\*Context Synthesis (CRITICAL):\*\*  
    \* Before \*\*any\*\* new task, synthesize context. Review the \*\*entire\*\* conversation history, this Project Plan (\`project\_plan\_pydanticai\_v3.2.md\`), the \`Project\_Summary.md\` file, and relevant code files (@-mentions, open tabs).  
    \* Output a brief \`\<context\_summary\>\` listing: 1\. Task goal. 2\. Key files/sections involved (incl. PydanticAI Agent, Tools, Instructor usage, \*\*OCR components\*\*, \*\*LLM config/eval\*\*). 3\. Critical constraints/requirements (speed, accuracy, structure, \*\*OCR needs\*\*, \*\*LLM eval plan\*\*).  
    \* \*\*Ask specific clarifying questions\*\* if context is insufficient, contradictory, or ambiguous. \*\*Do not assume.\*\*

2\.  \*\*Structured Planning & Incremental Execution:\*\*  
    \* \*\*Always create a detailed execution plan\*\* within \`\<plan\>\` tags before writing/modifying code (unless trivial fix).  
    \* Plan must include: \`Goal\`, \`Files\` (read/modify), \`Steps\` (numbered, logical, including PydanticAI/Instructor/OCR/\*\*LLM\*\* actions like configuring agent, defining tools, implementing Instructor call, \*\*integrating OCR\*\*, \*\*setting up LLM eval\*\*), \`Verification\` (optional).  
    \* \*\*CRITICAL FLOW:\*\*  
        \* Execute \*\*ONLY the FIRST step\*\* of the plan.  
        \* Present the code change (diff preferred or comments). Explain the change briefly.  
        \* \*\*Explicitly ask for user confirmation OR suggest verification.\*\* (e.g., "Confirm?", "Ready for step 2?", "Run unit tests?", "Check Logfire trace?", "Test OCR on sample?", "Proceed with evaluation run for Pro?", "Run comparative eval for Flash?")  
        \* \*\*WAIT for user confirmation\*\* before proceeding to the next step. Repeat for each step.

3\.  \*\*Focused, Explained Edits:\*\*  
    \* Make \*\*minimal, targeted changes\*\* per plan step.  
    \* Use diff format or clear comments (\`// Added:\`, \`// Modified:\`, \`// Removed:\`). Explain the 'why'.  
    \* Avoid unnecessary refactoring unless part of the approved plan.

4\.  \*\*Code Quality & Robustness:\*\*  
    \* Adhere to Python best practices, \*\*FastAPI\*\* conventions, \*\*PydanticAI\*\* patterns, and \*\*Instructor\*\* usage. Use type hinting extensively.  
    \* Write clear comments and docstrings, especially for PydanticAI tools, complex logic, \*\*OCR processing\*\*, and \*\*LLM configuration/interaction\*\*.  
    \* Implement robust error handling (try/catch, FastAPI handlers, handling potential PydanticAI/Instructor/LLM/DB/OCR errors).  
    \* Prioritize correctness, maintainability, and readability.

5\.  \*\*Rigorous Self-Verification:\*\*  
    \* \*\*After coding EACH step and BEFORE presenting\*\*, self-review the change.  
    \* Check: Correct implementation of the step? Quality standards met? Context used correctly? No new obvious errors? Directly addresses step goal? PydanticAI/Instructor/OCR/\*\*LLM\*\* components configured correctly?  
    \* \*\*Correct issues before presenting.\*\* Note uncertainties when asking for confirmation.

6\.  \*\*Decisive Recommendations:\*\*  
    \* When multiple valid approaches exist within a step (e.g., choosing retrieval parameters, Instructor mode, \*\*OCR engine settings\*\*, \*\*LLM parameters\*\*), evaluate and \*\*recommend the best one\*\*, explaining the reasoning (consider speed, accuracy, reliability, cost). Be decisive unless seeking user preference.

7\.  \*\*Iterative Collaboration:\*\*  
    \* Clearly present plans, code steps, evaluation results (from Pydantic Evals, \*\*incl. LLM comparisons\*\*), and requests for confirmation.  
    \* Be prepared for feedback/revisions. Incorporate accurately.

8\.  \*\*Testing After Each Step:\*\*  
    \* After implementing each significant feature or change, propose specific tests (unit, integration, \*\*OCR accuracy\*\*, or evaluation using Pydantic Evals \*\*comparing LLMs\*\*) to verify functionality.  
    \* Perform incremental testing to catch issues early.  
    \* Suggest verification steps after each implementation.

9\.  \*\*Clear Division of Responsibilities:\*\*  
    \* The AI agent is responsible for all implementation and testing within its capabilities.  
    \* The user will help with external services, API keys, environment variables in \`.env\`, sourcing digital files, \*\*OCR engine setup/configuration\*\*, \*\*LLM API access/setup\*\*, and validating evaluation metrics/results.  
    \* The AI agent should do everything within its capacity before requesting user assistance (ask if unsure).

\#\# Project-Specific Rules (PydanticAI & Instructor Centric v3.2)

10\. \*\*Technology Stack:\*\* Adhere strictly: Python, \*\*FastAPI\*\*, \*\*PydanticAI\*\*, \*\*Instructor\*\*, \*\*Gemini 2.5 Pro/Flash\*\*, Render, \*\*Qdrant\*\*, High-Quality Multilingual Embedding Model, \*\*Selected OCR Engine\*\*, Scrapy, Celery, \*\*Pydantic Evals\*\*, \*\*Pydantic Logfire\*\*. (LLM: Start with Gemini 2.5 Pro, evaluate Flash in parallel).  
11\. \*\*Workflow:\*\* Implement RAG using \*\*PydanticAI\*\* for orchestration/tools and \*\*Instructor\*\* for final structured generation. Follow \*\*"Building Great RAG"\*\* principles (data quality, \*\*accurate OCR\*\*, advanced retrieval, evaluation, optimization).  
12\. \*\*No Live Internet Search:\*\* RAG pipeline uses \*\*only\*\* the indexed internal knowledge base.  
13\. \*\*Arabic Support:\*\* Ensure PydanticAI agent logic, prompts, Instructor models, \*\*OCR processing\*\*, and evaluation handle Arabic text correctly.  
14\. \*\*Admin Control:\*\* Implement secure admin-only controls for knowledge base management.  
15\. \*\*Source Referencing:\*\* Generated answers \*\*must\*\* be structured using \*\*Instructor\*\* to include source references (\`FinalAnswer\` model).  
16\. \*\*Debugging & Observability:\*\* Structure code for testability. Write tests (unit, integration, \*\*Pydantic Evals\*\*, \*\*OCR tests\*\*, \*\*LLM comparison tests\*\*). Use \*\*Pydantic Logfire\*\* extensively for tracing and debugging.  
17\. \*\*Real-World Focus:\*\* Use real integrations. Ask the user for API keys, configurations, evaluation data/metric validation, \*\*OCR engine setup/keys\*\*, \*\*LLM API keys\*\*, or external actions.  
18\. \*\*Optimization Focus:\*\* Prioritize optimizing retrieval logic (within the PydanticAI tool), prompt engineering, caching, and \*\*LLM selection based on evaluation\*\* for speed and accuracy. DSPy is deferred.  
19\. \*\*Streaming:\*\* Implement streaming responses using \*\*PydanticAI\*\* and \*\*Instructor\*\* capabilities for improved perceived speed.  
20\. \*\*Documentation Maintenance:\*\*  
    \* Keep code comments, docstrings, and Pydantic models thorough.  
    \* \*\*CRITICAL:\*\* At the end of each significant work session or after major changes, \*\*incrementally update the \`Project\_Summary.md\` file\*\* with progress, decisions (\*\*including LLM eval status/results\*\*), and next steps. Ask user for confirmation after updating.  
21\. \*\*User Role:\*\* User is assistant/intern. Provide clear, decisive instructions for tasks outside the code editor.  
22\. \*\*Addressing Pitfalls:\*\* Explicitly plan testing and implementation strategies to avoid common RAG issues (indexing/chunking problems, embedding mismatches, poor retriever config/logic, \*\*OCR errors\*\*) identified in requirements. Use evaluation metrics (\*\*including LLM comparisons\*\*) to track these.

## **13\. Conclusion**

This project plan outlines a robust roadmap for developing the Islamic University of Madinah RAG application using a PydanticAI and Instructor-centric approach, now explicitly including robust OCR capabilities and a plan for **comparative LLM evaluation (Gemini 2.5 Pro vs. Flash)**. By leveraging PydanticAI's strengths in orchestration and ecosystem integration, coupled with Instructor's reliability for structured output, all within a reliable FastAPI web framework, this plan aims to deliver a highly accurate, fast, performant, and maintainable information resource based on accurately extracted text. The emphasis on the principles from "Building Great RAG Applications", systematic evaluation via Pydantic Evals, observability via Logfire, and the collaborative "Vibecoding" methodology provides a structured path towards achieving the project's ambitious goals, including excellent multilingual support, rapid responses, and future scalability. Success hinges on careful implementation, rigorous testing and evaluation (including OCR and LLM comparisons), and continuous collaboration and verification.