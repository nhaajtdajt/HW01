# G9.1 — Three mistakes in the AI-generated mindmap

**Artifact audited:** `mindmap_ai_original.md` — Gemini Flash-Lite, prompt G10 in `prompt_log.md`
**Checked against:** ISTQB Certified Tester Foundation Level syllabus **v4.0**, dated 2023-04-21
([official download](https://istqb.org/certifications/certified-tester-foundation-level-ctfl-v4-0/) · [direct PDF copy](https://www.gasq.org/files/content/gasq/downloads/certification/ISTQB/Foundation%20Level/ISTQB_CTFL_Syllabus-v4.0%20.pdf))

> ⚠️ **Check the syllabus edition your class uses before submitting.** Mistakes 1 and 2 below are mistakes **against v4.0**. In the older v3.1 syllabus there were four test levels and the test types were functional / non-functional / white-box / change-related — exactly what the AI produced. Mistake 3 is wrong in **every** edition, so it is the safest of the three. Mistake 4 is kept as a spare.

---

## Mistake 1 — Only four test levels; v4.0 defines five

**AI said:**
> 4. Test levels — Component testing (Unit testing) · **Integration testing** · System testing · Acceptance testing

**ISTQB v4.0, §2.2.1 Test Levels (p. 27):**
> "In this syllabus, the following **five test levels** are described: • Component testing (also known as unit testing) …"

The five are **component testing, component integration testing, system testing, system integration testing, acceptance testing**. The syllabus uses all five names again in §1.5.3: *"developers performing component and component integration testing, test team performing system and system integration testing, and business representatives performing acceptance testing."*

**Why it matters:** collapsing the two integration levels into one hides that integration is verified twice at different scopes — between components inside a system, and between whole systems. They have different test bases, different environments and usually different owners.

**Corrected branch:**
- Component (unit) testing
- Component integration testing
- System testing
- System integration testing
- Acceptance testing (UAT · operational · contractual/regulatory · alpha and beta)

---

## Mistake 2 — Black-box testing missing from test types; change-related testing wrongly listed as a type

**AI said:**
> 5. Test types — Functional testing · Non-functional testing · White-box testing · **Change-related testing (Confirmation testing and Regression testing)**

**ISTQB v4.0, §2.2.2 Test Types (p. 28):**
> "In this syllabus, the following **four test types** are addressed: Functional testing … Non-functional testing …"

The four are **functional, non-functional, black-box and white-box testing**. The AI listed white-box but dropped its counterpart black-box, and put change-related testing in its place. Confirmation testing and regression testing have their own section — **§2.2.3 "Confirmation Testing and Regression Testing" (p. 29)** — and are not test types. (§2.3 is Maintenance Testing, a different topic again.)

**Why it matters:** a test type is defined by the quality characteristic it targets, so it is chosen during test analysis. Change-related testing is triggered by a *change*, so it is scheduled by the release process. Mixing them up leads to regression testing being planned as if it were a one-off activity per quality characteristic.

**Corrected branches:**
- **Test types (§2.2.2):** functional · non-functional · black-box · white-box
- **Change-related testing (§2.2.3):** confirmation testing (re-testing) · regression testing

---

## Mistake 3 — Testing principle 5 is garbled

**AI said:**
> 6. The ISTQB testing principles — … **"Pesticide paradox is destructive"** …

**ISTQB v4.0, §1.3 Testing Principles:**
> "5. **Tests wear out.** If the same tests are repeated many times, they become increasingly ineffective in detecting new defects (Beizer 1990). To overcome this effect, existing tests and test data may need to be modified, and new tests may need to be written."

The word *"pesticide"* does not appear anywhere in the v4.0 syllabus (0 occurrences in the PDF). In the older v3.1 edition the principle was worded *"Beware of the pesticide paradox"* — so **neither edition** says the paradox "is destructive".

**Why it matters:** the principle says tests lose their power to find *new* defects, and the response is to revise and add tests. "Destructive" suggests the opposite idea — that re-running tests damages something — which would justify running fewer tests, the opposite of the intended guidance. The syllabus even notes that repetition can be beneficial, e.g. in automated regression testing.

**Corrected branch:**
- 5. Tests wear out — repeating the same tests makes them progressively less effective at finding new defects; revise existing tests and add new ones

---

## Mistake 4 (spare) — Roles given as job titles

**AI said:**
> 3. Roles in testing according to ISTQB — **Test manager · Tester**

**ISTQB v4.0, §1.4.5 Roles in Testing (p. 21):**
> "In this syllabus, **two principal roles in testing** are covered: a **test management role** and a **testing role**. The activities and tasks assigned to these two roles depend on factors such as the project and product context, the skills of the people in the roles, and the organization."

The syllabus defines *roles*, not job titles, and the same person may perform both. "Test manager" and "Tester" are industry job titles.

**Why it matters:** R1 of this homework shows the difference in practice — the Money Forward posting puts the test management role (release decisions, risk governance) and the testing role (automation, execution) in a single job advert.

The same page adds: *"Different people may take on these roles at different times … It is also possible for one person to take on the roles of testing and test management at the same time."* **Evidence:** `evidence/mindmap_istqb_roles.png`.

---

## Also worth noting (not counted as one of the three)

Branch 1 "QA vs QC vs Testing — how they differ" lists the three terms and explains **no difference at all**, although the prompt asked for it. This is an **incompleteness**, not a factual error, so it belongs in the audit verdict rather than in the three mistakes. The distinction the syllabus draws is in **§1.2.2 Testing and Quality Assurance (QA)**: QA is process-oriented, QC is product-oriented, and testing is a form of quality control.

---

## Mistake 5 (spare) — principle 7 uses the old wording

**AI said:**
> 6. The ISTQB testing principles — … **"Absence-of-errors fallacy"**

**ISTQB v4.0, §1.3, principle 7 (p. 18):**
> "7. **Absence-of-defects fallacy**. It is a fallacy (i.e., a misconception) to expect that software verification will ensure the success of a system."

v4.0 renamed this principle from *absence-of-errors* (v3.1) to *absence-of-defects*. Same version caveat as mistakes 1 and 2: it only counts if your class uses v4.0.

**Evidence:** `evidence/mindmap_istqb_principle5.png` — the same screenshot shows principles 5, 6 and 7.

---

## Evidence (captured 24/09/2026)

| File | What it shows |
|---|---|
| `evidence/mindmap_ai_1.png` | Gemini chat: the prompt and branches 1–4 |
| `evidence/mindmap_ai_2.png` | Gemini chat: branches 3–7, including the four test levels and "Pesticide paradox is destructive" |
| `evidence/mindmap_ai_3.png` | Gemini chat: branches 5–7 in full |
| `evidence/mindmap_istqb_levels.png` | Syllabus p. 27, `five test levels` highlighted — mistake 1 |
| `evidence/mindmap_istqb_types.png` | Syllabus p. 28, `four test types` highlighted — mistake 2 |
| `evidence/mindmap_istqb_principle5.png` | Syllabus p. 18, `Tests wear out` highlighted — mistake 3 (and principle 7, mistake 5) |
| `evidence/mindmap_istqb_roles.png` | Syllabus p. 21, `two principal roles in testing` highlighted — mistake 4 |

Every syllabus screenshot shows the page footer **"v4.0 … 2023-04-21 © International Software Testing Qualifications Board"**, which proves which edition was used.
