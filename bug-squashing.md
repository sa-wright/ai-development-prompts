This project has bugs. Do a systematic bug triage and fix.
Work through every section.

═══════════════════════════════════════════════════════════════
SECTION 1: INVENTORY
═══════════════════════════════════════════════════════════════

1. Start the application and all services.

2. Test every feature systematically. For each, note:
   - Does it work at all?
   - Does it work correctly?
   - Does it handle errors?
   - Does it match what the docs/plan say it should do?

3. Run the full test suite. List all failures.

4. Check application logs for errors or warnings.

5. Compile the complete bug list. For each bug:
   - What: description of incorrect behavior
   - Where: file and function
   - Severity: Critical (blocks usage) / High (wrong results) / 
     Medium (poor experience) / Low (cosmetic)
   - Reproducible: steps to trigger it

═══════════════════════════════════════════════════════════════
SECTION 2: PRIORITIZE
═══════════════════════════════════════════════════════════════

6. Sort bugs by severity. Show me the list and ask if I want 
   to adjust priorities before you start fixing.

═══════════════════════════════════════════════════════════════
SECTION 3: FIX — CRITICAL AND HIGH
═══════════════════════════════════════════════════════════════

7. Fix all Critical and High bugs:
   - Fix the bug
   - Write a test that reproduces the bug (test should fail before fix)
   - Apply the fix
   - Verify the test passes
   - Run full test suite to check for regressions
   - Commit each fix separately with descriptive message

═══════════════════════════════════════════════════════════════
SECTION 4: FIX — MEDIUM AND LOW
═══════════════════════════════════════════════════════════════

8. Fix Medium and Low bugs:
   - Same process as above
   - Skip any that would require significant refactoring
   - Note skipped ones with reason

═══════════════════════════════════════════════════════════════
SECTION 5: REGRESSION CHECK
═══════════════════════════════════════════════════════════════

9. After all fixes:
   - Run full test suite
   - Manually test every feature that was fixed
   - Manually test features adjacent to fixes (could be affected)
   - Check for new warnings in logs

═══════════════════════════════════════════════════════════════
SECTION 6: REPORT
═══════════════════════════════════════════════════════════════

10. Show me:

| Severity | Found | Fixed | Remaining | Skipped (why) |
|----------|-------|-------|-----------|---------------|
| Critical | | | | |
| High | | | | |
| Medium | | | | |
| Low | | | | |

Total tests added for bug fixes: ___
All tests passing: yes/no
