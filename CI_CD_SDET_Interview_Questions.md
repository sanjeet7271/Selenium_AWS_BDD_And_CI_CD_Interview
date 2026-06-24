# CI/CD Pipeline Tricky Interview Questions & Answers (10+ Years SDET)

## 1. What is the biggest mistake teams make when implementing CI/CD?
Many teams automate deployment without automating quality validation.

Pipeline:
- Build
- Unit Tests
- Static Analysis
- API Tests
- UI Tests
- Security Scan
- Deploy

---

## 2. Your pipeline suddenly becomes 3x slower. How would you investigate?
- Check build duration trends
- Analyze stage timings
- Review infrastructure changes
- Check dependency download times
- Investigate resource contention

---

## 3. How would you reduce a 2-hour regression pipeline to 20 minutes?
- Parallel execution
- Test impact analysis
- Headless execution
- Containerized agents
- Remove duplicate tests
- Shift validations to API level

---

## 4. What is a Quality Gate?
Examples:
- Code Coverage > 80%
- Critical Vulnerabilities = 0
- Smoke Tests Pass
- API Tests Pass

---

## 5. Explain Blue-Green Deployment
- Blue = Current Production
- Green = New Release
- Deploy to Green
- Run Smoke Tests
- Switch Traffic
- Rollback by switching traffic back to Blue

---

## 6. Explain Canary Deployment
Release gradually:
- 5%
- 25%
- 50%
- 100%

Benefits:
- Reduced risk
- Production validation

---

## 7. What should trigger a deployment rollback?
- High error rates
- Critical API failures
- Smoke test failures
- Memory spikes
- Increased response times

---

## 8. How do you handle flaky tests?
- Identify
- Quarantine
- Root cause analysis
- Fix permanently

Avoid excessive retries.

---

## 9. Should UI tests run on every commit?
Recommended:
- Commit → Unit Tests
- Pull Request → API Tests
- Nightly → Full UI Regression

---

## 10. What is Shift Left Testing?
Testing earlier through:
- Unit tests
- Static analysis
- Contract testing
- Security scanning

---

## 11. Pipeline passed but deployment failed. What could be wrong?
- Environment mismatch
- Missing secrets
- Database migration issues
- Network policies
- Missing dependencies

---

## 12. How would you test microservices in CI/CD?
Layers:
1. Unit Tests
2. Contract Tests
3. API Integration Tests
4. End-to-End Tests

---

## 13. Why are contract tests important?
They detect breaking API changes before deployment.

---

## 14. How do you secure secrets in CI/CD?
Use:
- HashiCorp Vault
- AWS Secrets Manager
- Azure Key Vault

Never store secrets in source code.

---

## 15. What metrics define a mature CI/CD pipeline?
- Deployment Frequency
- Lead Time
- Change Failure Rate
- MTTR (Mean Time To Recovery)

---

## 16. Jenkins Agent Goes Offline Randomly. What Would You Do?
Check:
- Agent logs
- Memory usage
- Disk space
- Network connectivity
- Java version

---

## 17. How Would You Design a CI/CD Pipeline for a Large Enterprise?
- Build
- Unit Tests
- Coverage
- Static Analysis
- Security Scan
- Artifact Repository
- QA Deployment
- API Automation
- UI Smoke
- Stage Deployment
- Performance Tests
- Production Deployment

---

## 18. Difference Between CI and CD

### Continuous Integration
Code Merge → Build → Test

### Continuous Delivery
Release-ready artifact with approval.

### Continuous Deployment
Automatic deployment to production.

---

## 19. Five Services, One Fails. Should Deployment Stop?
Depends on architecture:
- Tightly coupled → Stop deployment
- Independent microservices → Deploy successful services

---

## 20. How Do You Measure CI/CD Success?
- Faster lead time
- Higher deployment frequency
- Lower change failure rate
- Reduced MTTR
- Stable automation
- Faster developer feedback
