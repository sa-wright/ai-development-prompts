Generate complete, professional documentation for this project.
Work through every section. Every doc should be accurate to the 
current codebase — not aspirational, not copy-pasted from a template.

Start by removing all project markdown files. Then:

═══════════════════════════════════════════════════════════════
SECTION 1: README.md
═══════════════════════════════════════════════════════════════

1. Rewrite README.md to include:
   - Project name and one-line description
   - What problem it solves (2-3 sentences, no buzzwords)
   - Screenshot or demo link placeholder
   - Tech stack with versions
   - Prerequisites (exact versions needed)
   - Quick start (clone to running in under 5 minutes)
   - All make/docker commands with descriptions
   - Environment variables table (name, description, required, default)
   - Project structure overview

   Test every command in the README yourself. If it fails, fix it.

═══════════════════════════════════════════════════════════════
SECTION 2: API DOCUMENTATION
═══════════════════════════════════════════════════════════════

2. Generate docs/API.md with:
   - Base URL and versioning info
   - Authentication guide (how to get a token, how to use it)
   - For EVERY endpoint:
     - Method and path
     - Description
     - Authentication requirement
     - Request headers
     - Request body schema with field types and descriptions
     - Example request (curl)
     - Success response with example
     - Error responses with examples
     - Rate limiting info
   - Common error codes table
   - Pagination format explanation

═══════════════════════════════════════════════════════════════
SECTION 3: ARCHITECTURE DOCUMENTATION
═══════════════════════════════════════════════════════════════

3. Update docs/ARCHITECTURE.md to reflect reality:
   - System overview diagram (mermaid)
   - Component descriptions (what each service/module does)
   - Data flow diagram (request lifecycle)
   - Database schema (all tables, relationships, key fields)
   - External integrations (what, why, how)
   - Key design decisions and rationale
   - Directory structure with purpose of each folder

═══════════════════════════════════════════════════════════════
SECTION 4: OPERATIONS DOCUMENTATION
═══════════════════════════════════════════════════════════════

4. Create docs/OPERATIONS.md:
   - How to deploy (step by step)
   - How to monitor (what to watch, what alerts to set)
   - How to scale (horizontal, vertical, what to scale first)
   - How to backup and restore the database
   - How to rotate secrets
   - Common issues and their fixes (troubleshooting guide)
   - How to roll back a bad deployment

═══════════════════════════════════════════════════════════════
SECTION 5: DEVELOPER ONBOARDING
═══════════════════════════════════════════════════════════════

5. Create docs/ONBOARDING.md:
   - First-time setup from scratch (assume fresh Mac or Linux)
   - How to run the full stack locally
   - How to run tests
   - How to add a new API endpoint (step by step pattern)
   - How to add a new database model
   - How to add a new background job
   - Code style and conventions
   - Git workflow (branching, PRs, commit messages)
   - Where to find things (which file does what)


═══════════════════════════════════════════════════════════════
SECTION 6: VALIDATION
═══════════════════════════════════════════════════════════════

6. Verify all documentation:
   - Every code example runs correctly
   - Every curl example returns the documented response
   - Every setup step works on a clean environment
   - No references to files or endpoints that don't exist
   - No placeholder text left (TODO, TBD, lorem ipsum)

