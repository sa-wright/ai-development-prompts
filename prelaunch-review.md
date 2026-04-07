I need to demo this project tomorrow. Make it demo-ready.
Work through every section. Priority is making it LOOK good 
and WORK reliably for a live demo.

═══════════════════════════════════════════════════════════════
SECTION 1: DOES IT START CLEANLY?
═══════════════════════════════════════════════════════════════

1. Start everything from scratch:
   - make clean
   - make build
   - make run
   
   If any step fails or shows ugly warnings, fix it.
   The startup should be clean — no errors, no warnings, no 
   deprecation notices scrolling by.

═══════════════════════════════════════════════════════════════
SECTION 2: HAPPY PATH PERFECTION
═══════════════════════════════════════════════════════════════

2. Identify the 3-5 features I would demo. For each one:
   - Walk through it end to end
   - Fix anything that's broken
   - Fix anything that's ugly or confusing
   - Make sure error states are handled gracefully
   - Make sure loading states exist (no blank screens)
   - Make sure success feedback is clear (toast, redirect, message)

3. Create demo data:
   - Realistic, impressive-looking seed data
   - Not "test123" or "lorem ipsum"
   - Enough data to look like a real product
   - Add it to make seed-demo

═══════════════════════════════════════════════════════════════
SECTION 3: VISUAL POLISH (if UI exists)
═══════════════════════════════════════════════════════════════

4. Quick visual fixes:
   - Consistent spacing and alignment
   - No orphaned labels or empty states showing raw "null" or "undefined"
   - Loading spinners where data loads
   - Empty states with helpful messages ("No items yet. Create one!")
   - Error states with friendly messages
   - Page titles set correctly
   - Favicon exists

═══════════════════════════════════════════════════════════════
SECTION 4: CREATE DEMO SCRIPT
═══════════════════════════════════════════════════════════════

5. Create scripts/demo.sh that:
   - Resets to a clean state
   - Seeds demo data
   - Starts all services
   - Prints a nice banner with URLs and test credentials
   - Optionally opens the browser

6. Create docs/DEMO_SCRIPT.md with:
   - Talking points for each feature
   - Exact steps to walk through
   - What to click, what to type, what to show
   - Known issues to avoid during demo
   - Recovery steps if something goes wrong

═══════════════════════════════════════════════════════════════
SECTION 5: STABILITY CHECK
═══════════════════════════════════════════════════════════════

7. Run through the demo flow 3 times consecutively:
   - Does it work every time?
   - Does anything get slower on repeated use?
   - Does anything crash or hang?
   - Are there any race conditions in the UI?
   Fix anything that fails even once.

═══════════════════════════════════════════════════════════════
SECTION 6: BACKUP PLAN
═══════════════════════════════════════════════════════════════

8. Create a safety net:
   - Git tag the current state: git tag demo-ready
   - Document how to reset if something breaks mid-demo:
     make clean && make seed-demo && make run
   - Note which features to AVOID showing (fragile or incomplete)
   - Prepare offline fallback if network-dependent features exist

Report back: "Demo ready" or "These issues remain: [list]"
