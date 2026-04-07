I want to add a new feature to this project: [DESCRIBE THE FEATURE]

Work through every section below in order.

═══════════════════════════════════════════════════════════════
SECTION 1: UNDERSTAND THE CODEBASE
═══════════════════════════════════════════════════════════════

1. Before writing anything, read the existing codebase and tell me:
   - What patterns and conventions does this project use?
   - Where should this feature live in the directory structure?
   - What existing code can be reused?
   - What existing code needs to be modified?
   - Are there any conflicts with existing features?

═══════════════════════════════════════════════════════════════
SECTION 2: DESIGN
═══════════════════════════════════════════════════════════════

2. Propose the design:
   - New database models or schema changes needed
   - New API endpoints (method, path, request, response)
   - New UI components (if applicable)
   - Changes to existing code
   - New dependencies needed (justify each one)

3. Ask me clarifying questions about anything ambiguous.
   Wait for my approval before building.

═══════════════════════════════════════════════════════════════
SECTION 3: DATABASE CHANGES
═══════════════════════════════════════════════════════════════

4. If database changes are needed:
   - Create migration with both up and down
   - Add indexes for any new query patterns
   - Update seed data if applicable
   - Run migration and verify

═══════════════════════════════════════════════════════════════
SECTION 4: IMPLEMENTATION
═══════════════════════════════════════════════════════════════

5. Build the feature following existing project patterns:
   - Match the code style of existing files
   - Match the error handling patterns
   - Match the validation patterns
   - Match the response format
   - Match the file organization
   Do NOT introduce new patterns unless the existing ones are broken.

═══════════════════════════════════════════════════════════════
SECTION 5: TESTING
═══════════════════════════════════════════════════════════════

6. Write tests for the new feature:
   - Unit tests for business logic
   - Integration tests for new API endpoints
   - Edge case tests
   - Permission tests (who can and cannot access this)
   - Run entire test suite — new feature must not break existing tests

═══════════════════════════════════════════════════════════════
SECTION 6: DOCUMENTATION
═══════════════════════════════════════════════════════════════

7. Update all documentation:
   - Add new endpoints to API docs
   - Update ARCHITECTURE.md with new components
   - Update README if setup steps changed
   - Update PLAN.md if using the plan system
   - Add entry to CHANGELOG

═══════════════════════════════════════════════════════════════
SECTION 7: QUALITY CHECK
═══════════════════════════════════════════════════════════════

8. Final checks:
   - Run linter — zero new errors
   - Run type checker — zero new errors
   - Run full test suite — all pass
   - Test the feature manually with realistic data
   - Check that no existing feature is broken
   - Commit everything together
