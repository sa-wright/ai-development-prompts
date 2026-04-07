Build a comprehensive test suite for this project. Work through 
every section. Run tests after each section to make sure they pass.

═══════════════════════════════════════════════════════════════
SECTION 1: TEST INFRASTRUCTURE
═══════════════════════════════════════════════════════════════

1. Set up test infrastructure (if not already done):
   - Test runner configured and working
   - Test database or mocking strategy
   - Test fixtures and factories for creating test data
   - Helper functions for common test operations (create user, get token)
   - make test runs everything and reports results
   - Tests run in isolation — no shared state between tests

═══════════════════════════════════════════════════════════════
SECTION 2: UNIT TESTS — CORE BUSINESS LOGIC
═══════════════════════════════════════════════════════════════

2. Identify every function that contains business logic 
   (not just CRUD wrappers). For each one, write tests for:
   - Happy path with typical input
   - Edge cases (empty, null, boundary values)
   - Error cases (invalid input, missing data)
   - Boundary conditions (max values, min values, exactly at limits)

3. Test data transformations:
   - Input parsing and validation
   - Data format conversions
   - Calculation functions
   - Filtering and sorting logic

═══════════════════════════════════════════════════════════════
SECTION 3: INTEGRATION TESTS — API ENDPOINTS
═══════════════════════════════════════════════════════════════

4. For EVERY API endpoint, write tests covering:
   - Success case with valid input and auth
   - Missing authentication (expect 401)
   - Wrong role/permissions (expect 403)
   - Invalid input — each validation rule (expect 400)
   - Missing required fields (expect 400)
   - Resource not found (expect 404)
   - Duplicate creation (expect 409 if applicable)

5. Test authentication flow end-to-end:
   - Register → login → get token → use token → refresh token
   - Invalid credentials
   - Expired token
   - Revoked token (if applicable)

═══════════════════════════════════════════════════════════════
SECTION 4: DATA INTEGRITY TESTS
═══════════════════════════════════════════════════════════════

6. Test database constraints:
   - Creating records with missing required fields fails
   - Unique constraints are enforced
   - Foreign key constraints are enforced
   - Cascade deletes work correctly

7. Test concurrent operations:
   - Two simultaneous updates to the same resource
   - Race condition in counter increments
   - Simultaneous creation of same unique resource

═══════════════════════════════════════════════════════════════
SECTION 5: ERROR RECOVERY TESTS
═══════════════════════════════════════════════════════════════

8. Test failure scenarios:
   - What happens when database is unavailable? (mock it)
   - What happens when cache is unavailable?
   - What happens when external API is unavailable?
   - What happens when file storage is unavailable?
   - Does the app recover when services come back?

═══════════════════════════════════════════════════════════════
SECTION 6: SECURITY TESTS
═══════════════════════════════════════════════════════════════

9. Test security boundaries:
   - User A cannot access User B's data
   - Regular user cannot access admin endpoints
   - SQL injection attempts are rejected
   - XSS payloads are sanitized
   - Extremely large inputs are rejected
   - Rate limiting kicks in at the configured threshold

═══════════════════════════════════════════════════════════════
SECTION 7: REPORT
═══════════════════════════════════════════════════════════════

10. Run the full suite. Show me:
    - Total tests written
    - Total passing
    - Total failing (fix these)
    - Coverage percentage if measurable
    - Which critical paths still have no coverage
