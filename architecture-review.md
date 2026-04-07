Do a complete architecture review of this codebase. Work through 
every section. Don't fix anything yet — just document what you find.
Give me the full report at the end.

═══════════════════════════════════════════════════════════════
SECTION 1: STRUCTURE ANALYSIS
═══════════════════════════════════════════════════════════════

1. Map the entire project structure. For each directory and file:
   - What is its purpose?
   - Does it belong where it is?
   - Is anything misplaced?

2. Draw a dependency graph:
   - Which modules depend on which?
   - Are there circular dependencies?
   - Are there modules that depend on too many things?
   - Are there modules that everything depends on (fragile core)?

3. Identify the architectural pattern:
   - Is it MVC, layered, hexagonal, microservices, or chaos?
   - Is the pattern applied consistently?
   - Where does it break down?

═══════════════════════════════════════════════════════════════
SECTION 2: DATA FLOW ANALYSIS
═══════════════════════════════════════════════════════════════

4. Trace the complete lifecycle of a request:
   - HTTP request comes in → where does it go?
   - How does data flow from input to database to response?
   - Where are the validation boundaries?
   - Where does transformation happen?

5. Identify data hotspots:
   - Which database tables are written most?
   - Which queries are most complex?
   - Are there N+1 query patterns?
   - Is there data that should be cached but isn't?

6. Check data consistency:
   - Are there places where data could get out of sync?
   - Are transactions used where they should be?
   - Could concurrent requests corrupt data?

═══════════════════════════════════════════════════════════════
SECTION 3: COUPLING ANALYSIS
═══════════════════════════════════════════════════════════════

7. Find tight coupling:
   - Which components know too much about each other?
   - Could you replace the database without rewriting everything?
   - Could you replace the web framework without rewriting everything?
   - Are business rules mixed into HTTP handlers?

8. Find missing abstractions:
   - Is there duplicated logic that should be a shared service?
   - Are there God objects that do too many things?
   - Are there files over 500 lines that should be split?

═══════════════════════════════════════════════════════════════
SECTION 4: SCALABILITY ASSESSMENT
═══════════════════════════════════════════════════════════════

9. What breaks at 10x current load?
   - Which endpoints would be slowest?
   - Which database queries would time out?
   - Is there any in-memory state that prevents horizontal scaling?
   - Are there synchronous operations that should be async?

10. What breaks at 100x current data?
    - Which tables would become unmanageable?
    - Are there full table scans?
    - Is pagination implemented everywhere it should be?

═══════════════════════════════════════════════════════════════
SECTION 5: REPORT
═══════════════════════════════════════════════════════════════

Generate a report in docs/ARCHITECTURE_REVIEW.md:

| Area | Health | Critical Issues | Recommendations |
|------|--------|----------------|-----------------|
| Structure | | | |
| Data Flow | | | |
| Coupling | | | |
| Scalability | | | |
| Overall | | | |

List the top 5 things to fix, ranked by impact.
List the top 5 things that are done well.
Give an honest overall grade: A through F.
