# Threat Modeling (Security by Design)

Threat Modeling is the practice of systematically identifying, analyzing and prioritizing security threats **before they become vulnerabilities**.

Instead of reacting to incidents, Threat Modeling helps teams **anticipate how systems can fail**, where trust is placed, and what needs protection.

Security is not added later — it is **designed**.

---
### 🧭 Threat Modeling at a glance

Assets  
↓  
Entry Points  
↓  
Trust Boundaries  
↓  
Threats  
↓  
Controls & Mitigations

Threat Modeling is **iterative** and should be revisited whenever architecture or business logic changes.

---

## 🎯 Why Threat Modeling matters

- Identifies risks **early**, when fixes are cheaper
- Prevents entire classes of vulnerabilities (not just bugs)
- Improves communication between Security, Engineering and Architecture
- Shifts security left, without slowing delivery

Threat Modeling is not about finding exploits. It is about **understanding what can go wrong**.

---

## 🧩 Core Concepts

### 1️⃣ Assets

Assets are **what you need to protect**.

Examples:
- User data (PII, financial data)
- Authentication tokens (JWTs, session IDs)
- Business logic (payments, transfers, approvals)
- Infrastructure components
- Secrets and credentials

If you don’t know your assets, you don’t know your risks.

---

### 2️⃣ Entry Points

Entry Points are **where data enters the system**.

Examples:
- API endpoints
- Authentication flows
- Webhooks
- File uploads
- Background jobs
- Admin panels

Every entry point is a **potential attack surface**.

---

### 3️⃣ Trust Boundaries

Trust Boundaries define **where trust changes**.

Common trust boundaries:
- Client → API
- API Gateway → Backend service
- External service → Internal system
- Public network → Private network

Threats often exist **exactly at these boundaries**.

---

### 4️⃣ Threats

Threats are **undesired actions** that could impact assets.

They are not vulnerabilities yet — they are **possibilities**.

Examples:
- Unauthorized access
- Data tampering
- Privilege escalation
- Replay attacks
- Information disclosure
- Denial of service

---

### 5️⃣ Controls & Mitigations

Controls are **mechanisms that prevent or limit threats**.

Examples:
- Authentication
- Authorization
- Input validation
- Rate limiting
- Encryption
- Logging and monitoring

Threat Modeling connects **threats to controls**.

---

## 🧠 STRIDE (High-Level Reference)

STRIDE is a common classification model for threats:

- **S**poofing – pretending to be someone else
- **T**ampering – modifying data
- **R**epudiation – denying actions
- **I**nformation Disclosure – exposing data
- **D**enial of Service – making services unavailable
- **E**levation of Privilege – gaining higher access

STRIDE is a **thinking aid**, not a checklist to blindly follow.

---

## 🔐 Threat Modeling Example (API Scenario)

### Scenario
A REST API using JWT for authentication and authorization.

### Assets
- User identity
- Authorization levels
- Sensitive business operations

### Entry Points
- `/login`
- `/user/me`
- `/admin/*`
- `/payments`

### Trust Boundaries
- Client → API
- API Gateway → Backend services

### Threats Identified
- Token tampering
- Authorization bypass
- Token replay
- Excessive trust in JWT claims
- Missing validation of `aud`, `iss`, `exp`

### Possible Mitigations
- Mandatory JWT signature validation
- Enforce `aud` and `iss`
- Do not trust authorization claims blindly
- Server-side authorization checks
- Token expiration enforcement

This analysis **guides testing and implementation decisions**.

---

## 🧪 Threat Modeling vs Security Testing

Threat Modeling answers:
> *What could go wrong?*

Security Testing answers:
> *Does it actually go wrong?*

Threat Modeling:
- is proactive
- guides where to test
- reduces blind spots

Testing without Threat Modeling is **guesswork**.

---

## 🔁 When to perform Threat Modeling

- During design and architecture discussions
- Before implementing new features
- When changing authentication or authorization logic
- After major refactors
- Periodically, as systems evolve

Threat Modeling is **not a one-time activity**.

---

## 🛠️ Practical Tips for AppSec

- Start simple: one flow, one diagram, one discussion
- Focus on **business impact**, not academic models
- Document assumptions and trust boundaries
- Use Threat Modeling to support developers, not block them
- Keep it lightweight and actionable

---

## 📌 Key Takeaways

- Threat Modeling is about **thinking like an attacker before one exists**
- It connects assets, threats and controls
- It guides both secure design and effective testing
- It is a core pillar of Secure SDLC

