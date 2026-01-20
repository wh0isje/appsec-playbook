# Secure SDLC (Software Development Life Cycle)

Secure SDLC is the practice of **embedding security into every stage of software development**, instead of treating it as a final validation step.

The goal is not to slow down delivery, but to **reduce risk early**, when fixes are cheaper and impact is lower.

---

## 🔁 Secure SDLC at a glance

```
Requirements
     ↓
 Design & Architecture
     ↓
 Development
     ↓
 Testing & Validation
     ↓
 Deployment
     ↓
 Maintenance & Monitoring
```

Security is **continuous**. Feedback loops exist between all stages.

---

## 🎯 Why Secure SDLC matters

Most security issues found in production are not caused by complex exploits, but by:

* missing security requirements
* weak authorization design
* insecure defaults
* lack of validation during development

Secure SDLC helps teams:

* prevent vulnerabilities instead of reacting to them
* reduce rework and incident costs
* ship faster with more confidence

---

## 1️⃣ Planning & Requirements

Security starts before any code is written.

**AppSec focus**

* Identify sensitive data (PII, credentials, financial data)
* Define authentication and authorization requirements
* Establish security acceptance criteria
* Identify regulatory or compliance constraints

At this stage, security requirements should be aligned with the **CIA Triad**:

* **Confidentiality**: Who can access the data?
* **Integrity**: Who can modify it?
* **Availability**: What happens if the system is abused or unavailable?

**Common failures**

* No clear definition of authorization rules
* Assuming security will be “added later”
* Ignoring abuse cases and business logic risks

---

## 2️⃣ Design & Architecture

Design decisions define the **security ceiling** of the application.

**AppSec focus**

* Threat modeling (high-level is enough)
* Trust boundaries and data flow analysis
* Authentication and session strategy
* Authorization model (RBAC, ABAC, ownership checks)
* Token usage (JWT, sessions, refresh flows)

**Common failures**

* Trusting client-side controls
* Over-reliance on JWT claims
* Lack of clear ownership checks (BOLA / IDOR risks)

---

## 3️⃣ Development

Security during development is about **safe defaults and consistency**.

**AppSec focus**

* Secure coding guidelines
* Input validation and output encoding
* Proper error handling (no sensitive data exposure)
* Secrets management (no hardcoded secrets)
* Dependency awareness

**Supporting tools (examples)**

* SAST: SonarQube, Semgrep, Snyk Code
* Secrets detection: Gitleaks, TruffleHog
* Dependency analysis: Snyk, OWASP Dependency-Check

**Common failures**

* Blind trust in frameworks
* Excessive permissions
* Ignoring edge cases and abuse paths

---

## 4️⃣ Testing & Validation

Security testing validates **assumptions made earlier**.

**AppSec focus**

* Manual testing for business logic flaws
* Authorization testing (IDOR / BOLA)
* Rate limit and abuse testing
* Authentication flow validation
* DAST and targeted automated tests

**Important principle**

> Automated tools do not replace manual analysis.
> They support it.

At the end of this phase, **penetration testing** acts as the **final stress test**, validating whether the system behaves securely under real attack scenarios before production release.

---

## 5️⃣ Deployment & Release

Deployment is where misconfigurations often introduce risk.

**AppSec focus**

* Secure configuration review
* Environment separation (dev / staging / prod)
* Secrets handling in CI/CD
* Infrastructure as Code validation
* Minimal privileges in cloud resources

**Supporting tools (examples)**

* Container & IaC scanning: Trivy, Checkov
* CI/CD security checks
* Cloud security baselines

**Common failures**

* Overprivileged cloud roles
* Public services exposed by default
* Secrets stored in pipelines or logs

---

## 6️⃣ Maintenance & Monitoring

Security does not end at release.

**AppSec focus**

* Vulnerability management
* Dependency updates
* Monitoring and alerting
* Incident response readiness
* Continuous improvement of controls

**Reality check**
Most vulnerabilities are discovered **after deployment**.

---

## 🧠 Secure SDLC principles

* Shift security left, but **don’t block delivery**
* Prefer simple designs over complex controls
* Make secure paths the easiest paths
* Assume misuse and abuse, not only happy paths
* Security is a **shared responsibility**, not a gatekeeper role

---

## 📚 Glossary & References

* **BOLA / IDOR**: Broken Object Level Authorization
* **RBAC / ABAC**: Role / Attribute-Based Access Control
* **SAST / DAST**: Static / Dynamic Application Security Testing
* **CIA Triad**: Confidentiality, Integrity, Availability

**References**

* OWASP Top 10
* OWASP API Security Top 10
* OWASP ASVS

---

## 📎 Final note

Secure SDLC is not a checklist.
It is a **continuous process of risk reduction**, adapted to the product and team maturity.
