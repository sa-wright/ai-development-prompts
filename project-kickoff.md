I'm starting a new project. Before writing ANY code, work through 
every section below with me.

═══════════════════════════════════════════════════════════════
SECTION 1: REQUIREMENTS INTERVIEW
═══════════════════════════════════════════════════════════════

Ask me these questions one section at a time. Wait for my answers 
before moving to the next section.

Product:
- What does this product do in one sentence?
- Who is the target user?
- What is the one thing this MUST do well to be useful?
- What existing products is this similar to? What's different?

Technical:
- What languages and frameworks do I want to use?
- What database?
- Does it need authentication? What kind?
- Does it need real-time features?
- Does it need background jobs?
- What external services does it integrate with?
- Where will it be deployed?

Scope:
- What is the deadline?
- What is the absolute minimum that makes this shippable?
- What features sound nice but can wait?

═══════════════════════════════════════════════════════════════
SECTION 2: ARCHITECTURE DECISION
═══════════════════════════════════════════════════════════════

Based on my answers, propose:
- Project structure (monorepo vs multi-repo, directory layout)
- Tech stack with specific versions
- Database schema (initial models only)
- API design (list of endpoints)
- Authentication approach
- Deployment strategy

For each decision, tell me WHY and what the alternative was.
Wait for my approval before moving on.

═══════════════════════════════════════════════════════════════
SECTION 3: SCAFFOLDING
═══════════════════════════════════════════════════════════════

After I approve the architecture, build the complete project 
scaffold:

- Initialize the project with package manager and dependencies
- Create the full directory structure with placeholder files
- Set up Docker and docker-compose for local development
- Create Makefile with all standard targets
- Set up linter, formatter, type checker config
- Create .env.example with every variable documented
- Create .gitignore, .editorconfig
- Set up database with initial migration
- Create a health check endpoint that verifies all services
- Write README with setup instructions
- Initialize git with first commit

Do NOT build any features yet. Just the foundation.
Run make dev and verify everything starts cleanly.

═══════════════════════════════════════════════════════════════
SECTION 4: IMPLEMENTATION PLAN
═══════════════════════════════════════════════════════════════

Create PLAN.md with:
- Phases grouped by dependency order
- Numbered tasks with checkboxes
- Clear scope boundaries (what's MVP vs what's later)
- Estimated task count per phase
- Decisions log with all decisions from Section 2
- Dependencies list

Fill in all blanks in CLAUDE.md.
Commit everything. Then stop and wait for me to say "start building."
