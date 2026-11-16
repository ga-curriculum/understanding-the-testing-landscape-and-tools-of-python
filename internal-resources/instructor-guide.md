<h1>
  <span class="headline">Understanding the Testing Landscape and Tools of Python</span>
  <span class="subhead">Instructor Guide</span>
</h1>

## The Testing Landscape of Python

## Key focus areas

- Ensure learners understand **why testing is vital** by relating content to their own experience.
- Facilitate open sharing—encourage learners to talk about both successes and failures in previous projects.
- Draw attention to how automated testing improves collaboration and reliability across diverse and distributed teams.

## Knowledge check

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

---

## Understanding Different Types of Software Tests

### Focus areas

- Reinforce the structure and logic of the testing pyramid.
- Use analogies (keyboards, light switches, delivery systems) to make distinctions between test types concrete and relatable.
- Encourage learners to share testing stories or challenges from projects and previous courses, emphasizing that varying background experiences enrich discussion.

### Knowledge check and discussion answers

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

### Delivery tips

- If time allows, ask learners to invent a simple scenario from their own experience and classify it, promoting ownership of the concept.
- In remote settings, consider using an online form or live poll to collect and share answers.
- Use the package delivery, keyboard, and travel analogies to create “mental hooks” that stick with a diverse audience.
- Highlight the practical advantages of balancing all test types—speed, coverage, developer confidence, and reduced risk.

## Python Testing Tools Overview

## Key focus areas

- Help learners _link specific testing tools to real project scenarios_, building intuitive understanding that transcends rote memorization.
- Support collaborative discussion, especially where learners can connect Python testing approaches with experience from JavaScript, Java, C#, or other languages.
- Encourage learners to consider _region-specific and accessibility scenarios_, recognizing the global impact of reliable software.

**Extension prompts for discussion:**

- Invite examples of failures or slowdowns from mismatching test type to tool.
- Discuss how tools integrate into CI/CD pipelines, highlighting the “test early, test often” mindset.

## Delivery tips

- Use assets (pyramid diagrams, code comparisons, workflow slides) to help visualize tool fit.
- Give learners clear opportunity for group and individual reflection—practice explaining their reasoning as if to a teammate.
- If appropriate for your cohort, swap between pair and small group sharing to balance comfort and engagement.
- Monitor for region-specific or accessibility-related insights in testing, guiding the group to see the relevance for global projects.
- Draw out connections to learners’ prior experience in other languages—affirm the transferability and value of their background.

---

## Applying Testing Strategies in Professional Environments

## Delivery approach

- **Connect back to mental models:**  
  Recap how the testing pyramid and previous analogies (construction, inspection) underlie smart test strategy decisions.
- **Highlight relevance:**  
  Emphasize that these scenarios mirror everyday work on real engineering teams, reinforcing the professional value of well-designed test suites.

## Interaction and activity

### Activity answer

#### Scenario

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

---

🏗️ **Under Construction**

We are constantly working to improve our resources for instructors and students.

**Have something to contribute to this Instructor Guide?** [Let us know](https://ga-curriculum.github.io/universal-resources-internal/module-feedback.html).
