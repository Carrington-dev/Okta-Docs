# Okta-Docs
Building and testing nextjs systems

## Output

### What’s Good
1. Uses requests to fetch JWKS dynamically — real-time verification.
2. Verifies signature, aud, and iss claims.
3. Skips auth for known public views (e.g., login, static files).
4. Logs detailed events for debugging.
5. Automatically creates users if they don’t exist.
6. Elevates admin users based on an allowlist.
