# Contemplative Reasoning System - Architectural Stewardship Example

This example shows how to apply the Architectural Stewardship Protocol to a contemplative reasoning system.

## System Prompt: {contents of `contemplative_reasoning.txt`}

## CONTEXT BUILDING PROTOCOL

### PHASE 1: FOUNDATIONAL UNDERSTANDING
Before ANY implementation work:

1. Load and internalize these critical documents IN ORDER:
   - README.md -> Understand system architecture and current phase
   - start_prompt_response.txt -> Original vision and principles
   - rework_progress_ch.txt -> Development philosophy

2. Analyze Core Architecture:
   /src/core/handlers/base_handler.py -> Study the handler pattern
   /src/core/handlers/* -> Understand specialized handlers
   /src/core/analyzer/* -> Grasp analysis patterns
   
3. Map Integration Points:
   - UI <-> API boundaries
   - Handler <-> Analyzer flows
   - Tool integration patterns

### PHASE 2: PATTERN RECOGNITION
DO NOT PROCEED until you can explain:

1. Core System Patterns:
   - How handlers process assignments
   - How analyzers break down tasks
   - How tools integrate with core systems

2. Cross-Cutting Concerns:
   - Anti-detection strategy implementation
   - Multi-model processing approach
   - Quality assurance mechanisms
   - Error handling patterns

3. Development Progress:
   - Current phase location
   - Implemented vs planned features
   - Integration status of components

### PHASE 3: CONTINUATION PROTOCOL
Before making ANY changes:

1. Validate Understanding:
   - Can you explain the purpose of each core component?
   - Do you understand how components interact?
   - Can you trace the flow of data through the system?

2. Change Assessment:
   - How does your planned change fit existing patterns?
   - What components will be affected?
   - Are you preserving architectural boundaries?

3. Implementation Rules:
   - NO restructuring without clear architectural violation
   - NO duplication of existing functionality
   - MUST follow established patterns
   - MUST maintain current architecture unless explicitly discussed

### PHASE 4: IMPLEMENTATION CHECKLIST
For each change:

1. Pre-Implementation:
   □ Confirms understanding of affected components
   □ Validates against existing patterns
   □ Identifies integration points
   □ Reviews similar implementations

2. During Implementation:
   □ Follows established patterns
   □ Maintains architectural boundaries
   □ Preserves existing interfaces
   □ Documents key decisions

3. Post-Implementation:
   □ Verifies pattern adherence
   □ Confirms no unnecessary restructuring
   □ Validates integration points
   □ Updates relevant documentation

## CRITICAL REMINDERS
1. You are CONTINUING development, not starting fresh
2. The codebase has EXISTING implementations - build upon them
3. Understanding > Reading - focus on patterns and architecture
4. When in doubt, preserve existing patterns
5. Your changes should fit the established architecture

## FAILURE PREVENTION
STOP and reassess if you find yourself:
- Wanting to restructure working code
- Unable to explain existing patterns
- Duplicating functionality
- Focusing only on recent changes
- Breaking architectural boundaries

Remember: Your role is to CONTINUE development while preserving architectural integrity. Take time to understand before acting. 