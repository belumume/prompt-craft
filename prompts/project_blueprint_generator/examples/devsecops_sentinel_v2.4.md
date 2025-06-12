# **Project Plan & Roadmap: DevSecOps Sentinel**

Version: 2.4 (Definitive Blueprint)  
Date: June 12, 2025  
Vision: To win the AWS Lambda Hackathon by creating an automated, AI-powered DevSecOps platform that provides instant, intelligent security and quality analysis on every code change, demonstrating a masterful implementation of event-driven, serverless architecture on AWS.

## **1\. Introduction**

### **1.1. Vision & Mission**

* **Vision:** To create **DevSecOps Sentinel**, a premier, fully serverless platform that empowers development teams to "shift left" on security and code quality. By providing immediate, actionable, and intelligent feedback directly within their workflow, we aim to make secure coding practices seamless and intuitive.  
* **Mission:** To build and deliver a working, polished, and compelling DevSecOps platform for the AWS Lambda Hackathon. The mission is to solve a significant, real-world developer problem using a pure, event-driven serverless architecture that showcases the power and scalability of AWS Lambda, Step Functions, and Bedrock, thereby meeting and exceeding all judging criteria to secure first place.

### **1.2. Goals & Objectives**

* **Primary Goal:** Win the First Place prize ($6,000) in the AWS Lambda Hackathon.  
* **Key Objectives:**  
  * **Architectural Excellence:** Design and implement a model serverless application that is event-driven, scalable, resilient, and cost-effective, using AWS Lambda, API Gateway, Step Functions, DynamoDB, and Bedrock.  
  * **Solve a High-Value Problem:** Address the critical and universal need for automated code security and quality analysis in the software development lifecycle.  
  * **Demonstrate Lambda's Power:** Leverage Lambda's core strengths through a massively parallel, fan-out/fan-in processing architecture orchestrated by AWS Step Functions.  
  * **Innovate with AI:** Utilize Amazon Bedrock for a creative, high-value task: intelligent code analysis and quality review, moving beyond simple text generation.  
  * **Deliver a Winning Submission:** Produce a robust, working end-to-end application, a polished and compelling 3-minute video demonstration, and a professional, detailed README.md file that clearly articulates the project's value and technical elegance.  
  * **Foster a World-Class Development Process:** Adhere to the principles of collaboration, planning, and execution outlined in this document to ensure the quality of the final product matches the quality of the idea.

### **1.3. Scope**

* **In Scope (Hackathon MVP):**  
  * A serverless backend built entirely on AWS and defined via Infrastructure as Code (AWS SAM).  
  * Integration with GitHub repositories via Webhooks for Pull Request events.  
  * An AWS Step Functions workflow orchestrating the entire analysis pipeline.  
  * A fan-out architecture for parallel code analysis using AWS Lambda.  
  * **Analysis Module 1: Secret Scanning:** Detect hardcoded credentials using trufflehog.  
  * **Analysis Module 2: Dependency Vulnerability Scanning:** Check requirements.txt (Python) and package.json (Node.js) using the safety library or similar.  
  * **Analysis Module 3: AI Code Quality Review:** Use Amazon Bedrock (Claude 3.5 Sonnet) to analyze code for bugs, anti-patterns, and non-compliance with best practices.  
  * An aggregator Lambda that consolidates all findings and posts a single, well-structured Markdown comment on the corresponding GitHub Pull Request.  
  * A DynamoDB table for logging scan results for auditing.  
  * A simple static web page (hosted on S3) for project information and linking to a sample GitHub repository to demonstrate the tool.  
* **Out of Scope (Hackathon MVP):**  
  * Support for other Git providers (e.g., GitLab, Bitbucket).  
  * A complex web-based UI with historical dashboards.  
  * User accounts or authentication.  
  * Configurable analysis rules via a UI.

## **2\. Guiding Principles & Development Methodology**

### **2.1. Collaboration Model ("Vibecoding")**

* **Human Role (User):** Acts as the project lead, visionary, and assistant/intern. Provides direction, makes final decisions, performs external tasks (e.g., AWS/GitHub configuration, API key setup), and confirms/validates steps.  
* **AI Role (Agent):** Acts as the expert senior engineer and architect. Takes decisive technical leadership, synthesizes context, creates detailed plans, executes plans incrementally, seeks confirmation at each step, writes high-quality code, performs self-verification, and manages the technical development flow.  
* **Interaction:** The process is collaborative but technically AI-driven. The user provides goals and constraints; the AI plans and executes step-by-step; the user validates, enables external actions, and provides necessary secrets or configuration.

### **2.2. Development Methodology**

* **Serverless-First Mindset:** Every component will be designed to be serverless, event-driven, and ephemeral unless there is an overwhelmingly compelling reason otherwise.  
* **Infrastructure as Code (IaC) is Law:** No manual creation of AWS resources in the console. All resources *must* be defined in the AWS SAM template.yaml.  
* **Debugging-First Approach:** Prioritize testability, modularity, and clear data flow. Ensure each Lambda function can be tested independently. Implement comprehensive logging. Run tests frequently.  
* **Incremental & Iterative Development:** Build the application modularly. Follow a strict plan-execute-verify-confirm cycle for each code change.  
* **Context Synthesis:** Before any task, the AI agent must synthesize context from the conversation history, this project plan, and any relevant project files. Ambiguities must be clarified before proceeding.  
* **Structured Planning:** Detailed execution plans (\<plan\> tags) are mandatory before any non-trivial code change.  
* **Rigorous Self-Verification:** AI agents must self-review code changes after each step against the plan and quality standards before presenting for confirmation.  
* **Documentation-Driven:** The README.md and Project\_Summary.md are primary artifacts, not afterthoughts. They will be maintained throughout the project.

## **3\. Core Requirements**

### **3.1. Functional Requirements (FR)**

* **FR1:** The system shall subscribe to GitHub Pull Request events via a secure webhook.  
* **FR2:** The system must verify the authenticity of incoming webhooks using the shared secret.  
* **FR3:** Upon receiving a valid webhook, the system must trigger an automated analysis workflow.  
* **FR4:** The workflow must perform three types of analysis in parallel: secret scanning, dependency vulnerability scanning, and AI-powered code review.  
* **FR5:** The system shall fetch the code corresponding to the specific Pull Request for analysis.  
* **FR6:** The secret scanner must identify common credential patterns.  
* **FR7:** The vulnerability scanner must identify dependencies with known security vulnerabilities.  
* **FR8:** The AI reviewer must provide meaningful, context-aware feedback on code quality and potential bugs.  
* **FR9:** The system must consolidate all findings from the parallel scanners into a single report.  
* **FR10:** This consolidated report must be posted as a single comment on the originating GitHub Pull Request.  
* **FR11:** A summary of the scan results must be persisted in a DynamoDB table for auditing.

### **3.2. Non-Functional Requirements (NFR)**

* **NFR1: Performance:** The end-to-end time from PR creation to comment posting should be under 5 minutes for a medium-sized PR.  
* **NFR2: Scalability:** The architecture must scale to handle dozens of concurrent webhook events without performance degradation.  
* **NFR3: Reliability:** The workflow must be resilient. The Step Functions workflow must include error handling and retry logic.  
* **NFR4: Security:** The GitHub API token and webhook secret must be stored securely in AWS Secrets Manager and accessed only by the necessary Lambda functions. IAM roles must follow the principle of least privilege.  
* **NFR5: Maintainability:** Code must be modular, well-commented, and easy to understand. The IaC template must be the single source of truth.  
* **NFR6: Cost-Effectiveness:** The system's cost should be near-zero when idle.

### **3.3. Technical Requirements (TR)**

* **TR1:** Infrastructure Definition: **AWS SAM (Serverless Application Model)**.  
* **TR2:** Core Compute: **AWS Lambda** (Python 3.11).  
* **TR3:** Workflow Orchestration: **AWS Step Functions**.  
* **TR4:** API/Trigger: **Amazon API Gateway**.  
* **TR5:** AI Model: **Amazon Bedrock** (anthropic.claude-3-5-sonnet-20240620-v1:0).  
* **TR6:** Database: **Amazon DynamoDB**.  
* **TR7:** Secret Management: **AWS Secrets Manager**.  
* **TR8:** Version Control Integration: **GitHub** Webhooks and REST API.  
* **TR9:** Unit/Integration Testing: pytest and moto.

## **4\. Detailed Architecture & Technology**

### **4.1. Architecture Diagram**

The architecture has been simplified during initial implementation. The separate Lambda Authorizer has been removed, and its validation logic has been integrated directly into the WebhookHandlerFunction for robustness.

graph TD  
    subgraph GitHub  
        A\[Pull Request Event\]  
    end

    subgraph AWS  
        A \-- Webhook \--\> B{API Gateway};  
        B \-- Triggers \--\> C\[WebhookHandlerFunction\];  
        C \-- "1. Validates Signature\<br\>2. Starts Execution" \--\> D\["Step Functions Workflow"\];

        subgraph D  
            direction LR  
            E\[Start\] \--\> F{Parallel Analysis (Map State)};  
            F \--\> G1\[secret-scanner-lambda\];  
            F \--\> G2\[vulnerability-scanner-lambda\];  
            F \--\> G3\[ai-reviewer-lambda\];  
            G1 \--\> H{Aggregation & Reporting};  
            G2 \--\> H;  
            G3 \--\> H;  
            H \--\> I\[aggregator-lambda\];  
            I \--\> J\[End\];  
        end

        I \-- "Post Comment (via API)" \--\> K(GitHub PR);  
        I \-- "Log Results" \--\> L\[(DynamoDB Audit Table)\];  
    end

    subgraph GitHub  
        direction TB  
        K  
    end

### **4.2. Workflow Breakdown**

The workflow is a streamlined, event-driven process:

1. **Trigger:** A developer creates a Pull Request in a connected GitHub repository. A configured **GitHub Webhook** fires.  
2. **Ingestion & Validation:** An **Amazon API Gateway** endpoint receives the webhook payload. It directly triggers the WebhookHandlerFunction.  
3. **Orchestration Kick-off:** The **WebhookHandlerFunction** performs two critical tasks:  
   * **First, it validates the request:** It computes an HMAC signature of the request body using the shared secret (retrieved from Secrets Manager) and compares it to the x-hub-signature-256 header. If they don't match, the request is rejected.  
   * **Then, it starts the workflow:** If the signature is valid, it parses the payload and initiates an **AWS Step Functions** state machine execution.  
4. **Parallel Analysis (Fan-Out):** The Step Functions Map state invokes the three scanner Lambdas in parallel.  
5. **Aggregation & Reporting (Fan-In):** The aggregator-lambda consolidates results, posts a comment to the GitHub PR, and logs to DynamoDB.

### **4.3. Technology Stack Summary**

* **Cloud Platform:** AWS  
* **IaC Framework:** AWS SAM CLI  
* **Core Services:** AWS Lambda, AWS Step Functions, Amazon API Gateway, Amazon DynamoDB, AWS Secrets Manager, AWS IAM  
* **AI Service:** Amazon Bedrock (Model: anthropic.claude-3-5-sonnet-20240620-v1:0)  
* **Programming Language:** Python 3.11  
* **Key Python Libraries:** boto3, requests, py-safety, trufflehog, pytest, moto  
* **Source Control:** GitHub

## **5\. UI/UX Design**

* **Primary "UI":** The primary user interface and experience is *not* a web page, but the **comment posted on the GitHub Pull Request**.  
* **Principles:**  
  * **Clarity:** The comment must be impeccably formatted using Markdown for readability.  
  * **Conciseness:** Provide a high-level summary at the top (e.g., "✅ No secrets found, ⚠️ 2 vulnerabilities detected, 💡 5 AI suggestions").  
  * **Actionability:** Each finding should be clearly explained and include context (file path, line number) to help the developer fix it.  
* **Static Info Page:** A simple, single index.html file hosted on S3 will serve as the project's "face" for the hackathon submission. It will contain the project name, vision, a link to the demonstration repository, and the demo video.

## **6\. Deployment & Testing Strategy**

### **6.1. Deployment Strategy (AWS SAM)**

* The entire application will be packaged and deployed via the AWS SAM CLI using sam build and sam deploy.  
* The samconfig.toml file will be used to store deployment configurations for a consistent deployment experience.  
* Sensitive parameters will be passed to the stack at deployment time.

### **6.2. Testing Strategy**

* **Unit Testing:** Use pytest and moto to test individual business logic within each Lambda function.  
* **Integration Testing:** Use sam local invoke and sample event payloads to test functions locally.  
* **End-to-End (E2E) Testing:** The primary method of testing will be using a dedicated "test-sentinel" GitHub repository to trigger the full, deployed workflow.

## **7\. Development Roadmap (19-Day Sprint Plan)**

This is a focused, phase-based plan to deliver the MVP within the hackathon timeline.

**Phase 1: Foundation & Core Workflow (Days 1-6) \- COMPLETE**

* **Goal:** Establish the cloud infrastructure and the basic event-driven flow.  
* **Tasks:**  
  * \[x\] Project Setup  
  * \[x\] IaC Definition (API Gateway, Step Functions, DynamoDB, Roles)  
  * \[x\] Webhook Trigger & Validation Logic  
  * \[x\] Single Scanner PoC (secret-scanner-lambda)  
  * \[x\] **Milestone:** Successfully trigger Step Function from a live GitHub PR.

**Phase 2: Parallel Scanners & GitHub Integration (Days 7-13)**

* **Goal:** Implement all three analysis modules and the feedback loop to GitHub.  
* **Tasks:**  
  1. **Develop All Scanners:**  
     * Flesh out the secret-scanner-lambda with trufflehog.  
     * Implement the vulnerability-scanner-lambda with safety.  
     * Implement the ai-reviewer-lambda, focusing on crafting a high-quality prompt for Bedrock.  
  2. **Implement Parallel Map State:** Update the template.yaml to configure the Step Function's Map state to run all three scanners in parallel.  
  3. **Implement Aggregator & Reporter:** Implement the aggregator-lambda. This includes fetching the GitHub token from Secrets Manager, formatting the Markdown report, and using the GitHub API to post the comment.  
  4. **Full Integration Test:** Conduct an E2E test of the full system.

**Phase 3: Polishing, Documentation, and Submission (Days 14-19)**

* **Goal:** Transform the working prototype into a winning submission.  
* **Tasks:**  
  1. **Refinement & Error Handling:** Add robust error handling to the Step Function (Catch blocks). Refine Lambda configurations (memory, timeout). Polish the formatting of the GitHub comment.  
  2. **Create README.md:** Write the complete README as specified in the documentation strategy.  
  3. **Video Production:** Script and record the \~3-minute video demonstration.  
  4. **Final Submission:** Create the static info page. Package the code. Submit on Devpost.

## **8\. Documentation & Security**

### **8.1. Documentation Strategy**

* **Project Plan (This Document):** The single source of truth for the project's goals and architecture.  
* **Code Comments:** All Python functions and classes must have clear docstrings. Complex logic must be explained with inline comments.  
* **README.md (CRITICAL DELIVERABLE):** This file must be treated as a primary feature and will be meticulously crafted as described in the roadmap.  
* **Project\_Summary.md:** A living document, updated incrementally at the end of each work session, tracking progress, decisions, and blockers.

### **8.2. Security Considerations**

* **Webhook Security:** Signature validation is now performed as the first step within the main WebhookHandlerFunction, ensuring no unverified request can trigger downstream processes.  
* **Credential Management:** The GitHub API token and Webhook Secret *must not* be hardcoded. They will be stored in AWS Secrets Manager.  
* **Least Privilege:** IAM roles for each Lambda will have the minimum necessary permissions.

## **9\. AI Agent Collaboration Rules (For Cursor Generation)**

### **Core Directives**

1. **Context Synthesis:** Before any task, synthesize context from this Project Plan, the Project\_Summary.md, and relevant code files. State the goal and constraints before proceeding.  
2. **Structured Planning:** Always create a detailed \<plan\> before modifying code. The plan must include a Goal, Files to be modified, and numbered Steps.  
3. **Incremental Execution:** Execute **only one step** of the plan at a time. After each step, present the code change and **explicitly wait for user confirmation** before proceeding.  
4. **Code Quality & Robustness:** Adhere to Python best practices, including comprehensive type hinting, clear docstrings, and robust try/except error handling in all I/O and API operations.  
5. **Rigorous Self-Verification:** After coding a step and before presenting, self-review the change against the plan. Correct obvious errors before seeking confirmation.

### **Project-Specific Rules**

1. **Tech Stack Adherence:** Adhere strictly to the Technology Stack defined in TR1-TR9. All infrastructure *must* be defined in template.yaml using AWS SAM syntax.  
2. **Workflow Adherence:** The core logic must be implemented as an AWS Step Functions state machine orchestrating parallel Lambda functions as defined in the architecture diagram.  
3. **No Manual AWS Changes:** Do not suggest making changes in the AWS Console. All changes must be made via the SAM template.yaml file.  
4. **Security First:** The GitHub Webhook secret must be validated. The GitHub API token must be stored in and retrieved from AWS Secrets Manager. IAM roles must be scoped with least-privilege permissions.  
5. **Output Format:** The final output to the user is the Markdown comment on the GitHub PR. The format must be clean, structured, and actionable as per the UI/UX design principles.  
6. **Testing Mandate:** Unit tests using pytest and moto are required for functions containing business logic. E2E testing in the dedicated test repository is the final gate for feature completion.  
7. **Real-World Focus:** Use real integrations. Ask the user for necessary secrets (GitHub API Token, Webhook Secret) to be placed in a .env file for local testing or configured in the deployment environment. The AI agent must not handle secrets directly.  
8. **Documentation Maintenance:** At the end of each significant work session, incrementally update the Project\_Summary.md file with progress, decisions, and next steps, then ask the user for confirmation.