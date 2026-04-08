I need you to do a complete production readiness audit and fix of this 
project. Work through every section below in order. Don't skip anything. 
Fix issues as you find them. Run tests after every batch of fixes.

═══════════════════════════════════════════════════════════════
SECTION 1: CAN IT EVEN START?
═══════════════════════════════════════════════════════════════

1. Read the README. Follow the setup instructions exactly as written.
   If any step fails, fix the code AND the README.

2. Start all services (Docker, database, cache, queue, workers, app).
   If anything fails to start, fix it.

3. Check that every service is healthy:
   - Hit every health check endpoint
   - Verify database is connected and migrated
   - Verify cache/Redis is connected
   - Verify background workers are running
   - Show me the output of each check

4. If there is no health check endpoint, create one that checks 
   all dependencies and returns their status.

═══════════════════════════════════════════════════════════════
SECTION 2: HIT EVERY ENDPOINT
═══════════════════════════════════════════════════════════════

5. List every API endpoint in the application.

6. For each endpoint, send a real request with realistic data using curl.
   Show me the request and response for every single one.
   Flag any that:
   - Return 500
   - Return unexpected data
   - Take longer than 2 seconds
   - Return stack traces or internal errors to the user
   - Don't validate input properly

7. Test authentication flows end to end:
   - Register a new user (if applicable)
   - Login and get a token
   - Use the token on a protected endpoint
   - Try a protected endpoint WITHOUT a token (should get 401)
   - Try a protected endpoint with an EXPIRED token
   - Try a protected endpoint with a MALFORMED token
   - Try accessing admin-only endpoints as a regular user (should get 403)

8. Fix every issue found in steps 6 and 7.

═══════════════════════════════════════════════════════════════
SECTION 3: BREAK IT ON PURPOSE
═══════════════════════════════════════════════════════════════

9. Send malicious and malformed input to every endpoint:
   - Empty strings where strings are required
   - Null values where values are required
   - Strings where numbers are expected
   - Numbers where strings are expected
   - Extremely long strings (10,000+ characters)
   - SQL injection: ' OR 1=1 --
   - XSS: <script>alert('xss')</script>
   - Unicode and emoji: 你好 🚀 ñ
   - Negative numbers where only positive makes sense
   - Zero where zero would cause division errors
   - Arrays where objects are expected
   - Deeply nested JSON (100 levels)
   - Missing required fields
   - Extra unexpected fields

10. Every one of these should return a 400 with a helpful error 
    message, NOT a 500. Fix any that return 500.

═══════════════════════════════════════════════════════════════
SECTION 4: SECURITY AUDIT
═══════════════════════════════════════════════════════════════

11. Check for hardcoded secrets:
    Search for password, secret, api_key, token, private_key 
    across all source files. Remove any real secrets. Ensure all 
    secrets come from environment variables.

12. Check CORS configuration:
    - Is it set to allow all origins (*)? That is wrong for production.
    - Set it to specific allowed origins from env var.

13. Check for missing rate limiting:
    - Public endpoints should be rate limited
    - Auth endpoints (login, register) should be strictly rate limited
    - Add rate limiting where missing

14. Check for missing input sanitization:
    - Any user input rendered as HTML must be sanitized
    - Any user input in SQL must be parameterized
    - Any user input in shell commands must be escaped

15. Check that error responses don't leak internal information:
    - No stack traces in production responses
    - No database column names in errors
    - No file paths in errors
    - No internal IP addresses

16. Fix every issue found.

═══════════════════════════════════════════════════════════════
SECTION 5: DATA INTEGRITY
═══════════════════════════════════════════════════════════════

17. Check database schema:
    - Every foreign key has ON DELETE behavior defined
    - Every required field is NOT NULL
    - Every unique constraint that should exist does exist
    - Indexes exist on fields used in WHERE clauses and JOINs
    - Timestamps have defaults (created_at, updated_at)

18. Check for data races:
    - Any read-then-write operations should be in transactions
    - Any counter increments should be atomic
    - Any status transitions should check current state

19. Check for orphan data:
    - Deleting a parent should handle children (cascade or prevent)
    - File uploads should be cleaned up if the record is deleted

20. Fix every issue found.

═══════════════════════════════════════════════════════════════
SECTION 6: ERROR HANDLING
═══════════════════════════════════════════════════════════════

21. Find every try/catch or error handler in the codebase. 
    Verify each one:
    - Logs the error with enough context to debug
    - Returns a useful message to the user
    - Does not swallow errors silently
    - Does not catch generic Exception when a specific one is appropriate

22. Check for unhandled promise rejections (JS/TS) or 
    unhandled exceptions (Python/Go).

23. Check that every external call (database, cache, API, file system) 
    has error handling and a timeout.

24. Fix every issue found.

═══════════════════════════════════════════════════════════════
SECTION 7: CONFIGURATION
═══════════════════════════════════════════════════════════════

25. Verify .env.example exists and documents EVERY environment 
    variable the app needs. For each variable include:
    - What it does
    - Example value
    - Whether it is required or optional
    - Default value if optional

26. Verify the app fails fast with a clear error message if a 
    required env var is missing. Not a random crash 5 minutes 
    in but a clear message on startup.

27. Check for any hardcoded URLs, ports, or configuration values 
    that should be environment variables. Extract them.

28. Fix every issue found.

═══════════════════════════════════════════════════════════════
SECTION 8: TESTS
═══════════════════════════════════════════════════════════════

29. Run the full test suite. Fix any failures.

30. Check test coverage. For any critical path with zero coverage 
    (auth, payments, data mutations, core business logic), 
    write tests.

31. Verify tests can run in isolation — no dependency on external 
    services, test database, or specific state. Tests should pass 
    on a fresh clone with no setup beyond the test command.

32. Fix every issue found.

═══════════════════════════════════════════════════════════════
SECTION 9: DOCUMENTATION
═══════════════════════════════════════════════════════════════

33. Verify README includes:
    - What this project does (2-3 sentences)
    - Prerequisites (runtime versions, tools needed)
    - Setup instructions that actually work
    - How to run in development
    - How to run tests
    - How to build for production
    - Environment variables reference
    - API overview or link to API docs

34. If API docs do not exist, generate them — every endpoint with 
    method, path, auth requirements, request and response examples.

35. Update ARCHITECTURE.md to reflect the current state of the 
    codebase, not the plan.

36. Fix every issue found.

═══════════════════════════════════════════════════════════════
SECTION 10: LINT, FORMAT, TYPES
═══════════════════════════════════════════════════════════════

37. Run the linter. Fix all errors. Zero warnings where possible.

38. Run the formatter. Format everything.

39. Run the type checker. Fix all type errors. No any types in 
    TypeScript, no untyped functions in Python.

40. Commit everything.

═══════════════════════════════════════════════════════════════
SECTION 11: DOCKER AND DEPLOYMENT
═══════════════════════════════════════════════════════════════

41. Verify Dockerfile:
    - Multi-stage build (build stage + runtime stage)
    - Non-root user in runtime stage
    - .dockerignore excludes node_modules, .git, .env, tests
    - Minimal final image (no dev dependencies)
    - Health check instruction in Dockerfile

42. Verify docker-compose:
    - All services have health checks
    - Services wait for dependencies (depends_on with condition)
    - Volumes are used for persistent data
    - No secrets in docker-compose.yml (use env_file)
    - docker-compose down -v cleanly removes everything

43. Test full Docker lifecycle:
    - docker-compose build (should succeed)
    - docker-compose up (all services healthy)
    - Run a few API requests against the containerized app
    - docker-compose down -v (clean shutdown)

44. Fix every issue found.

═══════════════════════════════════════════════════════════════
SECTION 12: FINAL REPORT
═══════════════════════════════════════════════════════════════

45. Generate a production readiness report. Show me a summary table:

| Category         | Status | Issues Found | Issues Fixed | Remaining |
|------------------|--------|-------------|-------------|-----------|
| Startup          |        |             |             |           |
| API Endpoints    |        |             |             |           |
| Input Validation |        |             |             |           |
| Security         |        |             |             |           |
| Data Integrity   |        |             |             |           |
| Error Handling   |        |             |             |           |
| Configuration    |        |             |             |           |
| Tests            |        |             |             |           |
| Documentation    |        |             |             |           |
| Lint/Types       |        |             |             |           |
| Docker           |        |             |             |           |

Give me an honest RED / YELLOW / GREEN for each category.
List any remaining issues you could not fix and why.
Remove all elements and artificats of AI-assited coding. You can remove git, make sure that this looks like a human did the work.
Commit all changes when done.
