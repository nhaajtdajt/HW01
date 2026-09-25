# QA/QC and the ISTQB test process — corrected mindmap

> Bản sửa. Claude soạn nháp cấu trúc, sinh viên đối chiếu từng dòng với bản PDF chính thức **ISTQB CTFL v4.0 ngày 2023-04-21**. Khai báo là Artifact #11 trong `[AI-02]`.
> Render as PNG at markmap.js.org/repl if a PNG is preferred.

## Software QA/QC

### 1. QA vs QC vs Testing (§1.2.2 Testing and Quality Assurance)
- **Quality Assurance (QA)** — process-oriented: is the process capable of producing quality?
  - Preventive: standards, process improvement, training, audits
- **Quality Control (QC)** — product-oriented: does the work product meet its requirements?
  - Corrective and detective: inspections, testing
- **Testing** — one form of quality control
  - Not a synonym for QA
- **Verification vs validation**
  - Verification: are we building the product right? (against the specification)
  - Validation: are we building the right product? (against the user need)

### 2. Test activities and tasks (§1.4.1)
- Test planning
- Test monitoring and control
- Test analysis — *what to test*
- Test design — *how to test*
- Test implementation — build the testware
- Test execution — run and compare actual vs expected
- Test completion — report, archive testware, lessons learned
- Supporting concepts
  - Testware (§1.4.3): test plans, test cases, test data, test scripts, test reports
  - Traceability (§1.4.4): test basis ↔ test cases ↔ results

### 3. Roles in testing (§1.4.5)
- **Test management role** — planning, monitoring, control, reporting
- **Testing role** — analysis, design, implementation, execution
- Both roles may be performed by the same person; the split depends on the SDLC and the organisation
- *(Job titles such as QA Manager, Test Lead, SDET or Automation Tester are industry labels, not ISTQB roles)*

### 4. Test levels (§2.2.1)
- Component (unit) testing
- Component integration testing
- System testing
- System integration testing
- Acceptance testing
  - User acceptance testing (UAT)
  - Operational acceptance testing
  - Contractual and regulatory acceptance testing
  - Alpha and beta testing

### 5. Test types (§2.2.2)
- Functional testing — *what* the system does
- Non-functional testing — *how well* it does it (performance, usability, security, reliability, portability, maintainability, compatibility)
- Black-box testing — based on the specification
- White-box testing — based on the internal structure

### 6. Change-related testing (§2.2.3 Confirmation Testing and Regression Testing)
- Confirmation testing (re-testing) — the fix works
- Regression testing — the fix broke nothing else
- *(These are neither test levels nor test types)*

### 7. Testing principles (§1.3)
1. Testing shows the presence, not the absence, of defects
2. Exhaustive testing is impossible
3. Early testing saves time and money
4. Defects cluster together
5. Tests wear out
6. Testing is context dependent
7. Absence-of-defects fallacy *(v3.1 worded this "absence-of-errors fallacy")*

### 8. Static vs dynamic testing (§3.1, differences in §3.1.3)
- **Static testing** — the work product is not executed
  - Reviews: informal review, walkthrough, technical review, inspection
  - Static analysis: tools examine code or models
  - Finds defects **directly**, and early
- **Dynamic testing** — the software is executed
  - Finds **failures**, from which defects are inferred

### 9. Errors, defects, failures and root causes (§1.2.3)
- **Error (mistake)** — a human action that produces an incorrect result
- **Defect (bug, fault)** — the flaw in the work product
- **Failure** — the observable wrong behaviour when the defect is executed
- **Root cause** — the underlying reason the error was made
- Not every defect causes a failure; failures can also come from environmental conditions
