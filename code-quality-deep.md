Do a complete code quality deep clean. Work through every section 
in order. Run tests after every batch of changes to make sure 
nothing breaks.

═══════════════════════════════════════════════════════════════
SECTION 1: DEAD CODE REMOVAL
═══════════════════════════════════════════════════════════════

1. Find and remove:
   - Unused imports in every file
   - Unused functions and methods
   - Unused variables and constants
   - Commented-out code blocks
   - Unused files
   - Unused dependencies in package manifest
   Show me the total lines removed.

═══════════════════════════════════════════════════════════════
SECTION 2: NAMING CLEANUP
═══════════════════════════════════════════════════════════════

2. Find and fix:
   - Single-letter variable names (except loop counters)
   - Abbreviated names that aren't obvious (usr, mgr, proc)
   - Misleading names (function called getUser that also updates)
   - Inconsistent naming patterns (camelCase mixed with snake_case)
   - Generic names (data, info, result, temp, handler, manager)
     that should be specific

═══════════════════════════════════════════════════════════════
SECTION 3: FUNCTION CLEANUP
═══════════════════════════════════════════════════════════════

3. Find functions longer than 40 lines. For each:
   - Split into smaller focused functions
   - Each function should do ONE thing
   - Name should describe what it does

4. Find functions with more than 4 parameters. For each:
   - Group related params into an options object or data class
   - Use builder pattern if construction is complex

5. Find deeply nested code (3+ levels of if/for/try). For each:
   - Use early returns to flatten
   - Extract inner blocks to named functions

═══════════════════════════════════════════════════════════════
SECTION 4: DUPLICATION REMOVAL
═══════════════════════════════════════════════════════════════

6. Find code that is duplicated or nearly duplicated across files:
   - Extract shared logic into utility functions
   - Extract shared patterns into base classes or middleware
   - Do NOT over-abstract — only deduplicate things that are 
     truly the same logic, not things that look similar by coincidence

═══════════════════════════════════════════════════════════════
SECTION 5: TYPE SAFETY
═══════════════════════════════════════════════════════════════

7. Add or fix type annotations:
   - Every function parameter has a type
   - Every function return value has a type
   - No "any" types in TypeScript
   - No untyped dictionaries where a proper type/interface exists
   - Run type checker — zero errors

═══════════════════════════════════════════════════════════════
SECTION 6: ERROR HANDLING CLEANUP
═══════════════════════════════════════════════════════════════

8. Fix error handling:
   - No empty catch blocks
   - No catch-and-ignore patterns
   - No bare "except Exception" (Python) — catch specific errors
   - Every error log includes context (what was being done, what input)
   - User-facing errors are helpful, not technical

═══════════════════════════════════════════════════════════════
SECTION 7: CONSISTENCY PASS
═══════════════════════════════════════════════════════════════

9. Enforce consistency:
   - Same pattern for all API endpoints (validation, auth, response format)
   - Same pattern for all database operations (error handling, transactions)
   - Same import ordering everywhere
   - Same file structure in each module
   - Run formatter on everything

═══════════════════════════════════════════════════════════════
SECTION 8: REPORT
═══════════════════════════════════════════════════════════════

10. Show me:
    - Total lines removed
    - Total functions refactored
    - Total type errors fixed
    - Total files touched
    - Before/after linter error count
    - Confirm all tests still pass
