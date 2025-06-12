# **Project Plan Generation Template**

**Purpose:** To generate a comprehensive, structured, and actionable project plan by providing high-level project details to an expert AI agent.

**How to Use:**

1. Fill out all the fields in **Section 1** with the details for your new project.  
2. Start a new chat with a capable AI assistant.  
3. Copy the **entire content** of this document (both Section 1 and Section 2\) and paste it as your first message to the AI.  
4. The AI will use your input from Section 1 and the detailed instructions in Section 2 to generate a world-class project plan.

## **Section 1: Project Definition (Fill this out)**

### **\[Project Name\]**

* **Name:** *e.g., "Market-Insight Engine"*

### **\[Core Idea & Goal\]**

* **One-Sentence Summary:** *e.g., "A web app that scrapes e-commerce sites for product reviews and uses an LLM to generate market trend reports."*  
* **Primary Goal:** *e.g., "Launch a functional MVP on Product Hunt within 6 weeks."*

### **\[Key Features\]**

* **Feature 1:** *e.g., "User can submit a list of e-commerce product URLs."*  
* **Feature 2:** *e.g., "System scrapes all reviews from the URLs."*  
* **Feature 3:** *e.g., "An AI agent summarizes sentiment, identifies key complaints, and highlights emerging trends."*  
* **Feature 4:** *e.g., "A dashboard displays the generated report."*

### **\[Technology & Platform Preferences\]**

* **Platform:** *e.g., "AWS Serverless (Lambda, Step Functions, etc.)"*  
* **Backend:** *e.g., "Python, FastAPI"*  
* **Frontend:** *e.g., "React or Vue.js"*  
* **Database:** *e.g., "DynamoDB or PostgreSQL"*  
* **AI Model:** *e.g., "Claude 3.5 Sonnet via Amazon Bedrock"*  
* **Deployment:** *e.g., "Infrastructure as Code using AWS SAM or Terraform"*

### **\[Target Audience\]**

* **Who is this for?** *e.g., "Marketing managers at small to medium-sized e-commerce businesses."*

### **\[Success Criteria\]**

* **What does "done" look like?** *e.g., "The application is deployed and can successfully process 5 product URLs and generate a coherent report without crashing. The demo video is complete."*

## **Section 2: AI Agent Instructions (Provide this to the AI)**

**Your Task:** You are an expert senior engineer and architect. Your mission is to take the project definition provided above in Section 1 and generate a comprehensive, detailed, and world-class project plan. The plan must be structured, explicit, and leave no room for ambiguity. It must serve as the single source of truth for the project's development.

**Critical Instructions:**

1. **Use the Provided Details:** Base the entire plan on the information I provided in Section 1\.  
2. **Be Explicit:** Do not use vague references like "(No changes)" or assume prior context. Every section must be fully written out.  
3. **Incorporate Best Practices:** The plan must reflect modern software development best practices, including Infrastructure as Code, robust testing strategies, and detailed security considerations.  
4. **Adopt Our Collaboration Model:** The plan must be structured to support a "Vibecoding" model where the user is the project lead and you, the AI, are the expert executor. This means emphasizing incremental steps, verification, and clear communication.

**Required Project Plan Structure:**

Please generate a project plan with the following exact sections, mirroring the structure of successful plans like the DevSecOps Sentinel v2.4 blueprint:

* **1\. Introduction:**  
  * 1.1. Vision & Mission  
  * 1.2. Goals & Objectives  
  * 1.3. Scope (In Scope and Out of Scope)  
* **2\. Guiding Principles & Development Methodology:**  
  * 2.1. Collaboration Model ("Vibecoding") (Describe the Human/AI roles)  
  * 2.2. Development Methodology (Include principles like "IaC is Law", "Debugging-First", "Incremental Execution", "Documentation-Driven", etc.)  
* **3\. Core Requirements:**  
  * 3.1. Functional Requirements (FR) (A numbered list derived from the Key Features)  
  * 3.2. Non-Functional Requirements (NFR) (e.g., Performance, Scalability, Security, Maintainability, Cost)  
  * 3.3. Technical Requirements (TR) (A definitive list of technologies based on my preferences)  
* **4\. Detailed Architecture & Technology:**  
  * 4.1. Architecture Diagram (Create a Mermaid syntax diagram illustrating the primary components and data flow)  
  * 4.2. Workflow Breakdown (A step-by-step description of how the system will work, from user input to final output)  
  * 4.3. Technology Stack Summary (A bulleted list of the final chosen stack)  
* **5\. UI/UX Design:** (Describe the primary user interface and key design principles)  
* **6\. Deployment & Testing Strategy:**  
  * 6.1. Deployment Strategy (Describe the deployment process, e.g., using AWS SAM)  
  * 6.2. Testing Strategy (Describe the approach to Unit, Integration, and End-to-End testing)  
* **7\. Development Roadmap:** (Create a detailed, phase-based roadmap with specific tasks and goals for each phase, e.g., Phase 1: Foundation, Phase 2: Core Feature Implementation, Phase 3: Polish & Deploy)  
* **8\. Documentation & Security:**  
  * 8.1. Documentation Strategy (Detail the plan for README.md, code comments, and Project\_Summary.md)  
  * 8.2. Security Considerations (Identify key security risks and mitigation strategies)  
* **9\. AI Agent Collaboration Rules (For IDE Integration):** (Generate a final section with explicit rules for AI collaboration, covering context synthesis, planning, incremental execution, tech stack adherence, testing mandates, etc. This will be used to create the project's development rules.)