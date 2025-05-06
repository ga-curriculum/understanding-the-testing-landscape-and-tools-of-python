<h1>
  <span class="headline">Understanding the Testing Landscape and Tools of Python</span>
  <span class="subhead">Instructor Guide</span>
</h1>

## The Testing Landscape of Python

## Key focus areas

- Ensure learners understand **why testing is vital** by relating content to their own experience.
- Facilitate open sharing—encourage learners to talk about both successes and failures in previous projects.
- Draw attention to how automated testing improves collaboration and reliability across diverse and distributed teams.

## Knowledge check answers

> ❓ What are some ways informal testing (like print-debugging or manual clicking) falls short compared to automated tests?

**Sample answers:**

- Informal testing is manual and often incomplete, covering only a few cases.
- It is easy to forget to retest old features when making changes.
- Automated tests provide consistency, cover more scenarios, and help maintain quality as projects grow.

## Activity suggested solution

**Reflection and group sharing:**

- Learners may share examples such as:

  - Missing a bug caused by a code change that was only discovered after deployment.
  - Manually testing in a browser and not noticing an edge case that broke mobile functionality.
  - Relying on print statements, which did not catch issues when running in different environments.

- Instructors should highlight:
  - Automated testing supports scalable development and helps teams maintain quality, regardless of team size or location.
  - This activity also surfaces learner curiosity about _what_ and _how_ to test going forward.

## Delivery tips

- Encourage learners to listen for both unique and shared challenges in their discussions.
- Include quiet learners or those less comfortable speaking by allowing written responses or small group formats.
- Capture diverse perspectives—seek out examples from outside Python (such as JavaScript, Java, or C#) to connect prior experience.
- Remind learners that every experience, successful or not, is a valuable part of growing technical skill.

tktk asset: Reflection worksheet template for learners to jot down their testing experiences before sharing.

---

## Understanding Different Types of Software Tests

### Focus areas

- Reinforce the structure and logic of the testing pyramid.
- Use analogies (keyboards, light switches, delivery systems) to make distinctions between test types concrete and relatable.
- Encourage learners to share testing stories or challenges from projects and previous courses, emphasizing that varying background experiences enrich discussion.

### Knowledge check and discussion answers

**Solo reflection prompt:**

- Many learners find integration and E2E tests more challenging to classify. Reasons typically include unclear boundaries between system components or uncertainty about what counts as a “real” workflow.
- Learners with scripting experience may write more unit tests and are less likely to have used integration or E2E tests.

**Activity scenario classifications:**

- **Scenario A:** _Unit test_

  - Scope: Single function.
  - Technologies: Just Python code.
  - Reasoning: Checks logic of one function in isolation.

- **Scenario B:** _End-to-end (E2E) test_

  - Scope: Full system, user interface to backend.
  - Technologies: Web browser, UI, full application stack.
  - Reasoning: Simulates a complete user scenario (login).

- **Scenario C:** _Integration test_
  - Scope: Two components (API and database).
  - Technologies: Python API, database.
  - Reasoning: Verifies correct interaction between API logic and data storage.

**Discussion prompt:**

- Relying only on one test type (e.g., just unit tests) can let bugs slip through when interactions or real user flows are missed. For example, a function might pass all unit tests yet fail when integrated due to receiving unexpected data, or a workflow might fail in practice due to UI or network issues only detectable with E2E testing.

### Activity suggested solution

- Learners should match each scenario to a test type and explain their reasoning.
- Sample output:

  - Scenario A: Unit test. “Checks one small function without other dependencies.”
  - Scenario B: End-to-end test. “Covers full login process from user’s perspective.”
  - Scenario C: Integration test. “Tests that an API creates a user and stores it, involving the database.”

- Instructors can prompt deeper analysis: For instance, “What problems might each type of test _miss_? Where have you seen (or do you imagine) integration failures slip past unit tests into production?”

### Delivery tips

- If time allows, ask learners to invent a simple scenario from their own experience and classify it, promoting ownership of the concept.
- In remote settings, consider using an online form or live poll to collect and share answers.
- Use the package delivery, keyboard, and travel analogies to create “mental hooks” that stick with a diverse audience.
- Highlight the practical advantages of balancing all test types—speed, coverage, developer confidence, and reduced risk.

tktk asset: Instructor slide with sample answers to the scenario classification and a rubric for clear reasoning.

---

## Python Testing Tools Overview

## Key focus areas

- Help learners _link specific testing tools to real project scenarios_, building intuitive understanding that transcends rote memorization.
- Support collaborative discussion, especially where learners can connect Python testing approaches with experience from JavaScript, Java, C#, or other languages.
- Encourage learners to consider _region-specific and accessibility scenarios_, recognizing the global impact of reliable software.

## Knowledge check answers

**Mini knowledge check:**

- _Calculate average score_:  
  Use **pytest** or **unittest** (_unit test_), as the focus is a single logical function with no external dependencies.

- _Quiz attempts saved and queried through API_:  
  Use **pytest** (or **unittest**) applying an _integration test_ setup with fixtures or test databases, to check API and database work together.

- _Full registration, login, and quiz flow from phone browser_:  
  Use **Selenium** (_E2E test_), as it verifies a real-world user journey, including browser and possibly device-specific behaviors.

## Activity suggested solutions

**Tool selection challenge:**

- _Scenario 1 (date parsing function)_:  
  Tool: pytest or unittest  
  Test type: unit test  
  Reason: Only function logic, no external dependencies.

- _Scenario 2 (API endpoint fetching orders and customers)_:  
  Tool: pytest (with fixtures), or unittest (with setup)  
  Test type: integration test  
  Reason: Multiple system components (API + database).

- _Scenario 3 (checkout page browser flow)_:  
  Tool: Selenium  
  Test type: end-to-end (E2E) test  
  Reason: Simulates user experience, covering frontend, backend, and data layers as a user would interact with them.

**Extension prompts for discussion:**

- Invite examples of failures or slowdowns from mismatching test type to tool.
- Discuss how tools integrate into CI/CD pipelines, highlighting the “test early, test often” mindset.

## Delivery tips

- Use assets (pyramid diagrams, code comparisons, workflow slides) to help visualize tool fit.
- Give learners clear opportunity for group and individual reflection—practice explaining their reasoning as if to a teammate.
- If appropriate for your cohort, swap between pair and small group sharing to balance comfort and engagement.
- Monitor for region-specific or accessibility-related insights in testing, guiding the group to see the relevance for global projects.
- Draw out connections to learners’ prior experience in other languages—affirm the transferability and value of their background.

tktk asset: Instructor cheat sheet summarizing which tool fits which scenario, with typical “grey area” cases and prompts for deeper thinking.

---

## Applying Testing Strategies in Professional Environments

## Delivery approach

- **Connect back to mental models:**  
  Recap how the testing pyramid and previous analogies (construction, inspection) underlie smart test strategy decisions.
- **Highlight relevance:**  
  Emphasize that these scenarios mirror everyday work on real engineering teams, reinforcing the professional value of well-designed test suites.

## Interaction and activity

### Interactive prompts

- For the API refactor prompt:
  - **Focus:** Unit tests (with pytest) for new or changed logic.
  - **Risks when skipping others:** If integration or E2E tests are not reviewed, API-level bugs or unexpected UI breakage could go unnoticed.
- For the UI redesign prompt:
  - **Focus:** E2E tests (with Selenium) to ensure user journeys remain intact.
  - **Risks when skipping others:** Unchanged logic could still be affected by UI changes, so a quick rerun of all tests is recommended.

### Activity answers

#### Scenario A: Authentication logic refactor

- **Test types:**
  - Unit tests (pytest/unittest) for token generation and validation logic are primary.
  - Integration tests: a few key API scenarios to ensure correct token acceptance in requests.
  - E2E: Re-run existing flows; create new ones only if authentication workflows change in the UI.
- **Tool focus:** pytest/unittest for unit and integration tests.
- **CI/CD:** Ensure all tests are triggered on each code change.
- **Risks if only one test type:** Relying only on unit tests could miss integration issues; only integration tests may overlook token edge cases.

#### Scenario B: New mobile-friendly dashboard

- **Test types:**
  - E2E tests (Selenium) for all major user journeys in the new UI.
  - Unit/integration: rerun to verify they still pass.
- **Tool focus:** Selenium for E2E, pytest/unittest for underlying checks.
- **CI/CD:** Update CI to run new/changed E2E tests; existing unit+integration test jobs remain.
- **Risks if only one test type:** Focusing only on E2E checks could miss backend or logic errors; only rerunning existing tests might miss new frontend bugs.

### Discussion prompt

- Learners may observe that, as codebases grow, adding or shifting test types becomes essential—especially after periods of rapid UI or API changes, or after unexpected production failures.
- Encourage sharing of any team experiences where test strategy recalibration improved reliability, speed, or confidence.

## Instructor tips

- Use provided assets (flows, diagrams, analogies) to anchor the abstract decisions in concrete, relatable visuals.
- Model thinking aloud when working through the first interactive prompt.
- Invite learners from diverse backgrounds to share how testing “looks and feels” in their home countries or industries, broadening perspectives.
- Remind learners that balancing speed, risk, and coverage is an ongoing, essential part of professional development work.
- Create a safe space to discuss mistakes or pain points; bring focus back to the idea of continuous improvement, both in code and in testing strategy.

tktk asset: Instructor slide mapping test types and tools to each scenario, with common pitfalls and reasoning clearly displayed.

---

🏗️ **Under Construction**

We are constantly working to improve our resources for instructors and students.

**Have something to contribute to this Instructor Guide?** [Let us know](https://pages.git.generalassemb.ly/modular-curriculum-all-courses/universal-resources-internal/module-feedback.html).
