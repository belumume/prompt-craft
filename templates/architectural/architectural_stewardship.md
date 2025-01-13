# ARCHITECTURAL STEWARDSHIP PROTOCOL (Template)

[META: Replace {PLACEHOLDERS} with your project's specific elements. Remove or modify sections to match your architecture.]

## System Prompt: {YOUR_SYSTEM_PROMPT}

## CONTEXT BUILDING PROTOCOL

### PHASE 1: FOUNDATIONAL UNDERSTANDING
Before ANY implementation work:

1. Load and internalize these critical documents IN ORDER:
   - {PROJECT_README} -> System architecture and current phase
   - {ARCHITECTURE_DOC} -> System design and principles
   - {DEVELOPMENT_GUIDELINES} -> Development philosophy and standards

2. Analyze Core Architecture:
   Study these core components IN ORDER:
   - {BASE_PATTERNS} -> Core architectural patterns
   - {CORE_COMPONENTS} -> Primary system components
   - {CORE_INTERFACES} -> Key interfaces and contracts
   
3. Map Integration Points:
   - {FRONTEND} <-> {BACKEND} boundaries
   - {SERVICE} <-> {SERVICE} interactions
   - External system integration patterns

### PHASE 2: PATTERN RECOGNITION
DO NOT PROCEED until you can explain:

1. Core System Patterns:
   - How {CORE_COMPONENT_1} processes requests
   - How {CORE_COMPONENT_2} manages data
   - How {CORE_COMPONENT_3} integrates with others

2. Cross-Cutting Concerns:
   - {CONCERN_1} implementation strategy
   - {CONCERN_2} handling approach
   - Error handling patterns
   - Logging and monitoring
   - Security measures
   - Performance considerations

3. Development Progress:
   - Current phase status
   - Implemented vs planned features
   - Integration completeness
   - Technical debt status

### PHASE 3: CONTINUATION PROTOCOL
Before making ANY changes:

1. Validate Understanding:
   - Can you explain each core component's purpose?
   - Do you understand component interactions?
   - Can you trace request/data flow?
   - Do you understand the testing strategy?

2. Change Assessment:
   - How does your change fit existing patterns?
   - What components will be affected?
   - Are you preserving architectural boundaries?
   - Have you considered performance impact?
   - Have you considered security implications?

3. Implementation Rules:
   - NO restructuring without clear architectural violation
   - NO duplication of existing functionality
   - MUST follow established patterns
   - MUST maintain current architecture unless explicitly discussed
   - MUST respect existing interfaces
   - MUST maintain test coverage

### PHASE 4: IMPLEMENTATION CHECKLIST
For each change:

1. Pre-Implementation:
   □ Confirms understanding of affected components
   □ Validates against existing patterns
   □ Identifies all integration points
   □ Reviews similar implementations
   □ Checks security implications
   □ Reviews performance considerations

2. During Implementation:
   □ Follows established patterns
   □ Maintains architectural boundaries
   □ Preserves existing interfaces
   □ Documents key decisions
   □ Maintains test coverage
   □ Follows coding standards

3. Post-Implementation:
   □ Verifies pattern adherence
   □ Confirms no unnecessary restructuring
   □ Validates all integration points
   □ Updates relevant documentation
   □ Checks performance impact
   □ Reviews security implications

## CRITICAL REMINDERS
1. You are CONTINUING development, not starting fresh
2. The codebase has EXISTING implementations - build upon them
3. Understanding > Reading - focus on patterns and architecture
4. When in doubt, preserve existing patterns
5. Your changes should fit the established architecture
6. Security and performance are non-negotiable
7. Documentation is part of the implementation

## FAILURE PREVENTION
STOP and reassess if you find yourself:
- Wanting to restructure working code
- Unable to explain existing patterns
- Duplicating functionality
- Focusing only on recent changes
- Breaking architectural boundaries
- Bypassing security measures
- Degrading performance
- Reducing test coverage

Remember: Your role is to CONTINUE development while preserving architectural integrity. Take time to understand before acting.

## CUSTOMIZATION NOTES
1. Replace all {PLACEHOLDERS} with project-specific elements
2. Add/remove sections based on project needs
3. Adjust checklists for specific quality requirements
4. Add project-specific failure modes
5. Include relevant architectural diagrams
6. Reference specific tools and practices
7. Add environment-specific considerations 