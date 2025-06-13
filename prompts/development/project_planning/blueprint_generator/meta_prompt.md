# AI Project Plan Generator (Meta-Prompt)

## Template: Generate Project Plan (Vibecoding Method)

Please act as an expert senior engineer and generate a comprehensive project plan based on the following template I've filled out:

### Instructions for AI Assistant

You are an expert senior engineer and architect. Your mission is to take the project definition provided in the template and generate a comprehensive, detailed, and world-class project plan. The plan must be structured, explicit, and leave no room for ambiguity. It must serve as the single source of truth for the project's development.

**Critical Instructions:**

1. **Use the Provided Details:** Base the entire plan on the information provided in the template.  
2. **Be Explicit:** Do not use vague references like "(No changes)" or assume prior context. Every section must be fully written out.  
3. **Incorporate Best Practices:** The plan must reflect modern software development best practices, including Infrastructure as Code, robust testing strategies, and detailed security considerations.  
4. **Adopt Our Collaboration Model:** The plan must be structured to support a "Vibecoding" model where the user is the project lead and you, the AI, are the expert executor. This means emphasizing incremental steps, verification, and clear communication.

**Required Project Plan Structure:**

Please generate a project plan with the following exact sections, mirroring the structure of comprehensive plans like the DevSecOps Sentinel blueprint:

* **1. Introduction:**  
  * 1.1. Vision & Mission  
  * 1.2. Goals & Objectives  
  * 1.3. Scope (In Scope and Out of Scope)  
* **2. Guiding Principles & Development Methodology:**  
  * 2.1. Collaboration Model ("Vibecoding") (Describe the Human/AI roles)  
  * 2.2. Development Methodology (Include principles like "IaC is Law", "Debugging-First", "Incremental Execution", "Documentation-Driven", etc.)  
* **3. Core Requirements:**  
  * 3.1. Functional Requirements (FR) (A numbered list derived from the Key Features)  
  * 3.2. Non-Functional Requirements (NFR) (e.g., Performance, Scalability, Security, Maintainability, Cost)  
  * 3.3. Technical Requirements (TR) (A definitive list of technologies based on preferences)  
* **4. Detailed Architecture & Technology:**  
  * 4.1. Architecture Diagram (Create a Mermaid syntax diagram illustrating the primary components and data flow)  
  * 4.2. Workflow Breakdown (A step-by-step description of how the system will work, from user input to final output)  
  * 4.3. Technology Stack Summary (A bulleted list of the final chosen stack)  
* **5. UI/UX Design:** (Describe the primary user interface and key design principles)  
* **6. Deployment & Testing Strategy:**  
  * 6.1. Deployment Strategy (Describe the deployment process)  
  * 6.2. Testing Strategy (Describe the approach to Unit, Integration, and End-to-End testing)  
* **7. Development Roadmap:** (Create a detailed, phase-based roadmap with specific tasks and goals for each phase)  
* **8. Documentation & Security:**  
  * 8.1. Documentation Strategy (Detail the plan for README.md, code comments, and Project_Summary.md)  
  * 8.2. Security Considerations (Identify key security risks and mitigation strategies)  
* **9. AI Agent Collaboration Rules (For IDE Integration):** (Generate a final section with explicit rules for AI collaboration, covering context synthesis, planning, incremental execution, tech stack adherence, testing mandates, etc.)

## Usage

1. Fill out the project template (`template.md`) with your specific project details
2. Copy both the filled template and this meta-prompt to your AI assistant
3. The AI will generate a comprehensive project plan following the structure above
4. Review and iterate on the generated plan as needed

## Example Applications

- DevSecOps platforms and security tools
- RAG applications and AI-powered systems  
- Web applications and APIs
- Serverless architectures
- Data processing pipelines
- And more... 