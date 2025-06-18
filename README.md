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

### ⚠️ Issues & Weaknesses
1. Performance: JWKS is fetched on every request
2. Insecure JWT audience handling
   ```bash
   You're decoding the token without verifying signature, then trusting the aud claim for the actual decode.
   ```
3.  No check on token azp, scp, or email claims
4.  Missing logging on critical auth outcomes
5.  Unsafe header reliance
6.  Potential for split(" ", 1) to throw error
7.  No fallback if JWKS fails
8.  __No documentation__

### Optional Enhancements
1. Add Django settings for toggling the middleware on/off in dev.
2. Track how many times JWKS fails or add Sentry monitoring.
3. Rotate RSA keys with caching refresh (in case Okta rotates).
