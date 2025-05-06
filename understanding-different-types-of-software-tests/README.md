<h1>
  <span class="headline">Understanding the Testing Landscape and Tools of Python</span>
  <span class="subhead">Understanding Different Types of Software Tests</span>
</h1>

**Learning Objective:**  
Differentiate between unit, integration, and end-to-end tests by describing their purpose, scope, and typical use cases within the software development lifecycle.

---

## Making sense of the testing pyramid

Developing reliable software involves not just writing code, but _testing_ it in meaningful ways. One widely-used mental model for understanding software testing strategies is the _testing pyramid_.

Imagine a triangle divided into three layers:

- **Base:** _Unit tests_
- **Middle:** _Integration tests_
- **Top:** _End-to-end (E2E) tests_

The widest part of the pyramid—the foundation—is composed of many unit tests. As you work your way up, you add fewer integration and even fewer E2E tests.

> 💡 The pyramid helps you visualize a balanced approach: focusing on fast, low-cost tests (unit) at the bottom, and using smaller numbers of slower, more complex tests (integration, E2E) at the top.

### Why stack the pyramid this way?

- **Cost and Speed:**  
  Unit tests are quick to run and write, while E2E tests are more involved and take longer to execute.
- **Scope:**  
  Unit tests check code in isolation. Integration tests check components working together. E2E tests simulate a user’s interaction with the entire system.

Building test suites according to this pyramid leads to faster feedback, fewer maintenance issues, and higher confidence in your code.

tktk asset: Clear, labeled illustration of the testing pyramid, showing the layers (unit, integration, E2E) and their relative sizes.

---

## Unit tests: Fast checks for small pieces

**Key concept:** _Unit tests_ examine single pieces of your code—such as a function or a method—without involving other parts of your application.

### Where do unit tests fit in your workflow?

Suppose you have a reusable function that calculates a discount on a product’s price. You want to guarantee it always returns the right result, regardless of how or where it’s used in your application.

<code class="filepath">tests/test_discount.py</code>

```python
def calculate_discount(price, percent):
    return price * (1 - percent / 100)

def test_calculate_discount():
    # Arrange: set up example inputs
    price = 100
    percent = 15
    # Act & Assert: check that the result is correct
    assert calculate_discount(price, percent) == 85
```

> 🏆 Unit tests provide immediate feedback—when this function changes in the future, you will quickly know if you accidentally broke its logic.

**Real-world analogy:**  
Unit tests are like verifying the operation of a single key on a keyboard before assembling the whole device. If the “A” key works, you know that one part of the whole system behaves correctly in isolation.

**Typical use cases:**

- Checking calculations or algorithms (e.g., totals, averages, discounts).
- Verifying data transformations.
- Testing simple business logic decisions.

tktk asset: Illustration of a person testing a single key from a keyboard, with other keys set aside.

---

## Integration tests: Assembling the bigger picture

**Key concept:** _Integration tests_ make sure that different parts of your application work together as intended.

### Where do integration tests fit in your workflow?

Imagine your FastAPI app has a feature where users register, and upon registration, their information is saved in a database. Here, you care about the interaction—not just whether saving to the database works, or the registration logic works alone, but whether they work _together_.

<code class="filepath">tests/test_user_registration.py</code>

```python
def test_user_registration(client, test_db):
    # Arrange: prepare test data
    user_info = {"username": "samira", "password": "securepass123"}
    # Act: submit registration via API
    response = client.post("/register", json=user_info)
    # Assert: check response and database
    assert response.status_code == 201
    users = test_db.get_all_users()
    assert any(u["username"] == "samira" for u in users)
```

> 🧠 Integration tests are critical for systems where parts rely on each other. They often reveal problems that unit tests cannot catch, like mismatched data formats or overlooked setup steps.

**Real-world analogy:**  
Integration tests are like checking whether a light switch actually turns on a lamp after both have already been tested alone. The switch and lamp might work separately, but only an integration check confirms the wiring between them is correct.

**Typical use cases:**

- Ensuring APIs return correct data after querying a database.
- Verifying that messaging services or email notifications are triggered appropriately.
- Testing workflows that span several interconnected modules.

tktk asset: Simple diagram showing a switch, wire, and lamp, highlighting the integration point.

---

## End-to-end tests: Walking in the user’s shoes

**Key concept:** _End-to-end (E2E) tests_ simulate a user’s complete journey through your application—often using tools that operate in the same way a human would interact with your product.

### Where do E2E tests fit in your workflow?

If you build a web application where users sign up, log in, shop for items, and check out, an E2E test might follow this whole process from start to finish using an automated browser.

<code class="filepath">tests/test_checkout_e2e.py</code>

```python
from selenium import webdriver

def test_checkout_process():
    browser = webdriver.Firefox()
    try:
        browser.get("http://localhost:8000")
        # Simulate actions: sign in, add to cart, purchase
        browser.find_element("id", "button-login").click()
        browser.find_element("id", "field-username").send_keys("alex")
        browser.find_element("id", "field-password").send_keys("passw0rd!")
        browser.find_element("id", "button-submit-login").click()
        browser.find_element("id", "button-add-item").click()
        browser.find_element("id", "button-checkout").click()
        assert "Thank you for your purchase" in browser.page_source
    finally:
        browser.quit()
```

> 💡 E2E tests show you if _everything_—from user interface to backend to data storage—works together as expected from a user’s perspective.

**Real-world analogy:**  
E2E testing is like having an independent inspector try out an entire transportation journey—checking a ticket, boarding a bus, transferring to a train, and reaching the final destination. A successful journey means every component along the way worked as it should.

**Typical use cases:**

- Confirming a user can complete registration, login, and checkout workflows.
- Testing complex interactions and error scenarios (such as forgotten password flows).
- Validating that real browsers or devices display the application correctly.

tktk asset: Comic-style sequence of a traveler purchasing a ticket, making transfers, and reaching their destination—mirroring steps in an E2E test.

---

## At a glance: Comparing the three types

| Test type        | Purpose                             | Scope                     | Example use case           | Cost & speed    |
| ---------------- | ----------------------------------- | ------------------------- | -------------------------- | --------------- |
| Unit test        | Check a single function or class    | Code in isolation         | Validate price calculation | Fast, low cost  |
| Integration test | Check cooperation of components     | Multiple modules/services | API saves to database      | Medium          |
| End-to-end (E2E) | Simulate user flow across whole app | Full system               | User completes checkout    | Slow, high cost |

> ♻️ A healthy project balances all three types, using unit tests for most scenarios, integration tests for key connections, and E2E tests for critical workflows.

tktk asset: Visual “scorecard” infographic showing strengths and tradeoffs of each test layer in terms of speed, coverage, and complexity.

---

## Activity: Identify and classify software test scenarios

Let’s practice distinguishing between the main types of tests using scenarios you might encounter as a Python developer.

**Purpose:**  
This activity helps you apply the testing pyramid concepts and recognize how each test fits real-world software work.

### Instructions

1. **Scenario analysis—5 minutes**  
   For each scenario below, jot down what type of test it describes and why.

   - **Scenario A:**  
     Test a function that accepts a list of numbers and returns their average. Make sure you check various input lists for correctness.
   - **Scenario B:**  
     Simulate submitting a login form in a web browser and verify that the user lands on the dashboard page after logging in.
   - **Scenario C:**  
     Test your API’s ability to add a new user to a database, then confirm that the user appears in the results when you list all users. This test connects to an actual test database.

2. **Classification—3 minutes**  
   For each scenario, answer:

   - What is the scope—just one function, several modules, or the entire system?
   - Which technologies are involved—just Python code, or also a database, browser, or an API endpoint?
   - Based on your answers, classify each scenario as a unit, integration, or end-to-end test.

3. **Solo reflection—2 minutes**  
   Write briefly:

   - Was any scenario more challenging to classify?
   - In your own coding experience (in Python or another language), which type of test do you write most often? Which do you feel least confident about?

> ❓ Why might relying only on one type of test not be enough to ensure software quality? Can you describe a specific situation or project where this could cause problems?

4. **Group discussion prompt**  
   Which type of testing do you believe will be most beneficial for your projects, and why? Share or discuss an example from your experience or imagine a plausible scenario.

tktk asset: Printable worksheet or slide template that lists the three scenarios and provides space for learners to classify and explain their answers.

---

## Making testing relatable: Everyday systems and quality checks

Software testing concepts can sometimes feel abstract. Let’s consider an analogy you encounter regularly: the journey of a package through a delivery system.

- **Unit test:**  
  Inspecting each box before it’s packed. Is it sturdy and properly sealed?
- **Integration test:**  
  Ensuring the conveyor belt actually moves the box from one station to the next.
- **End-to-end test:**  
  Following a package from sender to receiver, making sure it arrives intact and on time.

> 💡 No single check guarantees success on its own; reliable delivery depends on sturdy boxes, working conveyor belts, and smooth handoff all the way to the final destination.

tktk asset: Visual showing a package moving through inspection stations, conveyor belts, and final delivery.

---

## Instructor guide

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
