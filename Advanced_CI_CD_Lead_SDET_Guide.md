# CI/CD Pipeline Interview Questions & Answers for Lead SDET (10+ Years)

## Section 1: CI/CD Fundamentals
1. Difference between CI, Continuous Delivery, and Continuous Deployment?
2. What are the key pillars of a mature CI/CD pipeline?
3. What metrics indicate CI/CD success?
4. What are DORA metrics and why are they important?
5. What is Shift Left Testing?

## Section 2: Jenkins & Pipeline Design
6. Declarative vs Scripted Pipelines.
7. How do you design a reusable Jenkins pipeline?
8. How do you manage shared libraries?
9. How would you troubleshoot slow Jenkins builds?
10. Why do Jenkins agents go offline?
11. How do you secure Jenkins credentials?
12. How do you scale Jenkins for thousands of builds?

## Section 3: Test Automation in CI/CD
13. What tests should run on every commit?
14. What tests belong in nightly runs?
15. How do you reduce pipeline execution time?
16. How do you manage flaky tests?
17. How do you quarantine unstable tests?
18. How do you prioritize API vs UI tests?
19. What is test impact analysis?
20. How do you parallelize automation execution?

## Section 4: Microservices & API Testing
21. What are contract tests?
22. Why is Pact useful?
23. How do you test microservices independently?
24. How do you validate backward compatibility?
25. How do you manage service virtualization?
26. What is consumer-driven contract testing?

## Section 5: Deployment Strategies
27. Blue-Green Deployment.
28. Canary Deployment.
29. Rolling Deployment.
30. Recreate Deployment.
31. Feature Toggles.
32. Dark Launches.
33. A/B Testing.

## Section 6: Kubernetes & Containers
34. Why use Docker in CI/CD?
35. How do you optimize Docker images?
36. What are Kubernetes readiness and liveness probes?
37. How do you perform zero-downtime deployments?
38. What causes pod crashes?
39. How do you troubleshoot CrashLoopBackOff?
40. What are Kubernetes namespaces?

## Section 7: Security & Compliance
41. How do you secure secrets?
42. What is DevSecOps?
43. How do you integrate SAST tools?
44. How do you integrate DAST tools?
45. How do you prevent secrets from reaching Git?
46. What are supply-chain security risks?

## Section 8: Production Readiness
47. What should trigger rollback?
48. How do you automate rollback?
49. What production smoke tests should run?
50. How do you validate deployments post-release?
51. What monitoring tools have you used?
52. How do you handle incident response?

## Section 9: Scenario-Based Questions

### Q53: Pipeline passed but production failed. Why?
Potential reasons:
- Environment mismatch
- Infrastructure drift
- Configuration issues
- Secrets issues
- Database migration failures

### Q54: A 3-hour regression suite must finish in 30 minutes. What will you do?
- Parallel execution
- Test impact analysis
- API-first testing
- Containerized execution
- Remove duplicate coverage

### Q55: Deployment frequency is low. How would you improve it?
- Increase automation
- Improve quality gates
- Reduce manual approvals
- Improve observability

### Q56: How would you design an enterprise CI/CD pipeline?

Developer Commit
→ Build
→ Unit Tests
→ Code Coverage
→ Static Analysis
→ Security Scan
→ Artifact Repository
→ Deploy QA
→ API Automation
→ UI Smoke
→ Deploy Stage
→ Performance Testing
→ Production Approval
→ Production Deployment
→ Production Smoke Tests

### Q57: What would you do if one microservice fails deployment?
- Assess coupling
- Stop release if critical
- Continue independent deployments where possible
- Trigger automated rollback if needed

### Q58: How do you measure automation ROI?
- Execution time saved
- Defects caught early
- Reduced production incidents
- Faster feedback cycles

### Q59: What are the qualities of a mature SDET-led CI/CD pipeline?
- Fast feedback
- Reliable automation
- Security scanning
- Observability
- Automated rollback
- Quality gates

### Q60: What is your leadership approach for CI/CD adoption?
- Standardization
- Metrics-driven decisions
- Developer collaboration
- Continuous improvement
- Risk-based testing
