Do a complete performance audit and optimization. Work through 
every section. Benchmark before and after each change.

═══════════════════════════════════════════════════════════════
SECTION 1: IDENTIFY BOTTLENECKS
═══════════════════════════════════════════════════════════════

1. Start the application. Hit every major endpoint and time them:
   - Use curl with timing: curl -w "%{time_total}s" -o /dev/null -s
   - Flag anything over 500ms
   - Flag anything over 200ms that should be instant

2. For each slow endpoint, identify WHY:
   - Is it a slow database query?
   - Is it making external API calls synchronously?
   - Is it doing heavy computation in the request path?
   - Is it loading too much data into memory?

═══════════════════════════════════════════════════════════════
SECTION 2: DATABASE OPTIMIZATION
═══════════════════════════════════════════════════════════════

3. Find missing indexes:
   - Check every WHERE clause and JOIN in the codebase
   - Add indexes for columns used in filters and lookups
   - Add composite indexes for multi-column queries

4. Find N+1 queries:
   - Any loop that makes a database call per iteration
   - Replace with batch queries or eager loading/joins

5. Find expensive queries:
   - Any query that does a full table scan
   - Any query that returns more columns than needed (SELECT *)
   - Any query that loads large text/JSON fields unnecessarily
   - Optimize each one

6. Check connection pooling:
   - Is connection pooling configured?
   - Are connections released properly?
   - Is pool size appropriate for the workload?

═══════════════════════════════════════════════════════════════
SECTION 3: CACHING
═══════════════════════════════════════════════════════════════

7. Identify cacheable data:
   - Data that rarely changes but is read frequently
   - Expensive computations that produce the same result for same input
   - External API responses that can be cached briefly

8. Implement caching:
   - Add Redis/memory cache for identified items
   - Set appropriate TTLs (don't cache forever)
   - Add cache invalidation when data changes
   - Add cache hit/miss logging

═══════════════════════════════════════════════════════════════
SECTION 4: ASYNC AND BACKGROUND JOBS
═══════════════════════════════════════════════════════════════

9. Find operations that should not be in the request path:
   - Email sending
   - File processing
   - External API calls that the user doesn't need to wait for
   - Report generation
   - Data aggregation

10. Move them to background jobs:
    - Use existing job queue or set one up
    - Return 202 Accepted with a job ID
    - Add status polling endpoint
    - Add error handling and retry logic

═══════════════════════════════════════════════════════════════
SECTION 5: FRONTEND PERFORMANCE (if applicable)
═══════════════════════════════════════════════════════════════

11. Check bundle size:
    - Run bundle analyzer
    - Find the largest dependencies
    - Lazy load anything not needed on first render
    - Tree-shake unused code

12. Check loading performance:
    - Are images optimized and lazy loaded?
    - Are fonts loaded efficiently?
    - Is CSS critical path optimized?
    - Are API calls parallelized where possible?

═══════════════════════════════════════════════════════════════
SECTION 6: RESOURCE MANAGEMENT
═══════════════════════════════════════════════════════════════

13. Check for resource leaks:
    - Database connections that aren't closed
    - File handles that aren't closed
    - Event listeners that aren't removed
    - Timers/intervals that aren't cleared
    - Memory that grows unbounded over time

14. Check for wasteful operations:
    - Redundant API calls (same data fetched multiple times)
    - Redundant computation (same calculation done repeatedly)
    - Over-fetching (loading full objects when only ID is needed)

═══════════════════════════════════════════════════════════════
SECTION 7: BENCHMARK REPORT
═══════════════════════════════════════════════════════════════

15. Re-benchmark every endpoint that was slow in Section 1.
    Show me a before/after table:

| Endpoint | Before | After | Improvement |
|----------|--------|-------|-------------|
| | | | |

List what was changed for each improvement.
