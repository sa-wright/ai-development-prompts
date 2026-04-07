Do a complete security hardening pass. Work through every section.
Fix issues as you find them. This app will face the public internet.

═══════════════════════════════════════════════════════════════
SECTION 1: AUTHENTICATION AND AUTHORIZATION
═══════════════════════════════════════════════════════════════

1. Password security:
   - Passwords hashed with bcrypt/argon2 (not MD5/SHA)
   - Minimum password length enforced (8+ characters)
   - No password logged anywhere (check all log statements)
   - Password reset flow doesn't reveal if email exists

2. Token security:
   - JWTs have reasonable expiry (15 min access, 7 day refresh)
   - Refresh tokens are stored securely and rotated on use
   - Tokens include only necessary claims (no sensitive data)
   - Token revocation works

3. Authorization:
   - Every endpoint checks permissions, not just authentication
   - Users can only access their own data
   - Admin endpoints require admin role
   - No privilege escalation paths (user can't make themselves admin)

═══════════════════════════════════════════════════════════════
SECTION 2: INPUT VALIDATION
═══════════════════════════════════════════════════════════════

4. Every user input must be validated:
   - Type checking (string, number, email format, URL format)
   - Length limits on all string fields
   - Range limits on all numeric fields
   - Whitelist validation on enum fields
   - File upload: type checking, size limits, filename sanitization

5. SQL injection prevention:
   - Search every database query for string concatenation
   - All queries must use parameterized statements
   - No raw SQL with user input

6. XSS prevention:
   - All user content rendered in HTML is escaped
   - Custom code injection fields use DOMPurify or equivalent
   - Content-Security-Policy headers are set
   - No innerHTML with user data

7. Command injection prevention:
   - No shell commands built with user input
   - If shell commands are necessary, use safe subprocess APIs

═══════════════════════════════════════════════════════════════
SECTION 3: HTTP SECURITY
═══════════════════════════════════════════════════════════════

8. Set security headers on every response:
   - Strict-Transport-Security (HSTS)
   - Content-Security-Policy
   - X-Content-Type-Options: nosniff
   - X-Frame-Options: DENY
   - X-XSS-Protection: 0 (rely on CSP instead)
   - Referrer-Policy: strict-origin-when-cross-origin

9. CORS configuration:
   - Not set to allow all origins (*)
   - Allowed origins from environment variable
   - Only necessary methods allowed
   - Credentials mode configured correctly

10. Rate limiting:
    - Login endpoint: 5 attempts per minute per IP
    - Registration: 3 per hour per IP
    - Password reset: 3 per hour per email
    - Public API: appropriate per-key limits
    - Return 429 with Retry-After header

═══════════════════════════════════════════════════════════════
SECTION 4: DATA PROTECTION
═══════════════════════════════════════════════════════════════

11. Secrets management:
    - No secrets in source code (grep for them)
    - No secrets in logs (grep log statements for sensitive fields)
    - No secrets in error responses
    - All secrets from environment variables
    - .env is in .gitignore

12. Sensitive data handling:
    - PII is identified and handled appropriately
    - Sensitive fields excluded from API list responses
    - Database backups would be encrypted
    - Logs don't contain passwords, tokens, or credit card numbers

13. File upload security:
    - File type validated by content, not just extension
    - Upload size limited
    - Files stored outside web root
    - Filenames sanitized (no path traversal)
    - No executable files accepted

═══════════════════════════════════════════════════════════════
SECTION 5: DEPENDENCY SECURITY
═══════════════════════════════════════════════════════════════

14. Check dependencies:
    - Run dependency vulnerability scanner (npm audit, pip audit, etc.)
    - Update any dependencies with known vulnerabilities
    - Remove unused dependencies
    - Pin dependency versions

═══════════════════════════════════════════════════════════════
SECTION 6: REPORT
═══════════════════════════════════════════════════════════════

15. Generate security report:

| Category | Status | Critical | High | Medium | Low |
|----------|--------|----------|------|--------|-----|
| Auth | | | | | |
| Input Validation | | | | | |
| HTTP Security | | | | | |
| Data Protection | | | | | |
| Dependencies | | | | | |

List any issues that need manual attention (can't be auto-fixed).
