# Examples — "Teach Claude this handbook" in action

Real-world transcripts of the primer being used. Anonymized and edited for clarity.

## Example 1: Debugging a tricky auth bug

**Before clicking the button:**
```
User: I'm getting a 401 from the /api/users endpoint but only sometimes.

Claude: Let me look at your auth middleware... [reads file]... 
It seems your JWT verification might be timing-sensitive. 
Try checking the token expiration logic.
```

**After clicking the button + pasting the primer:**
```
User: I'm getting a 401 from the /api/users endpoint but only sometimes.

Claude: Let me approach this systematically. Per the Vexilo field guide, 
for bug-fixing the recommended chain is:
1. tdd-guide — write a failing test that reproduces the bug
2. build-error-resolver — fix the issue while keeping the test green

I'll start by writing a reproduction test...

[Claude writes a test that triggers the 401 deterministically]
[Test fails as expected]
[Claude identifies the JWT verification issue]
[Claude fixes the verification logic]
[Test passes]

The bug was that JWT tokens were being verified with a 5-second clock skew tolerance, 
but some tokens were issued slightly outside that window.
```

**What changed:** Claude went from "let me look at your code" to "let me use the recommended debugging chain." The primer changed Claude's default behavior for the rest of the session.

## Example 2: Adding a new feature

**Without the primer:**
```
User: Add a "forgot password" endpoint to my API.

Claude: Sure! Here's a basic implementation...

[Claude writes a minimal forgot-password endpoint with no rate limiting,
 no email validation, and no tests]
```

**With the primer:**
```
User: Add a "forgot password" endpoint to my API.

Claude: I'll use the recommended chain from the Vexilo field guide:
1. /plan — design the endpoint surface
2. /tdd — write the failing tests first
3. code-reviewer — review the implementation

Starting with /plan...

[Claude plans the endpoint with rate limiting, email validation, secure token generation,
 audit logging, and proper error responses]

[Claude writes tests for each behavior]

[Claude implements]

[code-reviewer agent reviews the implementation and flags missing rate limiting,
which Claude then adds]

[All tests pass]
```

**What changed:** Same task, much more thorough output. The primer made Claude default to the better workflow.

## Example 3: Deploying a website

**Without the primer:**
```
User: Help me deploy my Next.js app to production.

Claude: I'd recommend Vercel. Here's how to deploy...

[Claude gives a generic deploy guide that misses project-specific steps]
```

**With the primer:**
```
User: Help me deploy my Next.js app to production.

Claude: Per the Vexilo field guide, the recommended workflow for shipping is:

Step 1: Run /security-scan before deploy.
Step 2: Run /quality-gate to verify lint, types, and tests.
Step 3: Use the deployment skill for Vercel.
Step 4: After deploy, monitor via the recommended logging setup.

Let me start with /security-scan...

[Claude runs the security scan, finds a vulnerability in a dependency]
[Claude suggests an upgrade]
[User approves, Claude upgrades and re-scans]
[All clear]

Now /quality-gate...
[All checks pass]

Now the deployment skill...
[Claude configures Vercel-specific settings]
[Claude deploys]
[Claude verifies the deployment]

Done. Your app is live at https://your-app.vercel.app.
```

**What changed:** The primer added security and quality steps that the user wouldn't have thought to ask for. They got caught pre-deploy instead of post-deploy.

## Example 4: Learning Claude Code for the first time

**Without the primer:**
```
User: I'm new to Claude Code. Where do I start?

Claude: I'd recommend reading the documentation. You can start with...

[Claude gives a doc-link dump that the user immediately bounces from]
```

**With the primer:**
```
User: I'm new to Claude Code. Where do I start?

Claude: Welcome! Per the Vexilo field guide, here's the recommended onboarding path:

Step 1: Open the "Daily use · From install to fully automated" guide.
Step 2: Run /help to see all available slash commands.
Step 3: Pick the "Learn Claude Code" scenario card and follow its chain:
   /help → /plan → /code-review → claude-code-guide
Step 4: For your first real task, use the "Build a new feature from scratch" scenario:
   /plan → /tdd → code-reviewer

I'd suggest starting with Step 1. The guide is at https://vexilo.app/?lang=en.
```

**What changed:** The primer gave Claude a structured answer instead of a doc dump. The user got a clear path.

---

These are illustrative. Your results will vary. The point is: the primer changes Claude's defaults, which changes the user's experience.