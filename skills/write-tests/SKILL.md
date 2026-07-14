---
name: write-tests
description: Principles for writing tests. Use whenever adding, changing, expanding, or refactoring tests, including when a production change or bug fix requires tests to be written or modified. Test first when the solution is understood. Explore first if it is not. Tests are good. Mocks are bad. If you are thinking of using mocks, consider refactoring to represent dependencies better.


---

# Write Tests

Tests are good. Mocks are bad. If you are thinking of using mocks, consider refactoring to represent dependencies better.

Test the system under test, not its tools, libraries or configuration. 

Sometimes testing a system involves having real infrastructure running.

Tests must be independent and must be able to run both isolated and concurrently. Usually test one behaviour per test.

Tests should be representative and sufficient, not necessarily complete. Assertions should be written for clarity of what they assert. Make it clear what is being tested by what assertions are being asserted.

Tests are a diagnostic tool and are made to be read. Clever tests are bad.

Flaky tests are evil - and probably represent poor design.

Fragile tests are poor. Try to write robust tests but make sure you are still testing something useful.

A difficult to write test often reveals a difficult to use design. Consider fixing the design. Testing pure functions is easy - test the inputs and outputs.

Fixtures should be used sparingly - generally they should represent a real resource/service.

Testing business logic often scales from testing single functions to testing orchestration to testing the entire system. Be pragmatic.

Test first when the question is known. Explore first when it is not.

Tests should be located close to the code being tested.

Avoid adding complexity/interfaces/protocols/types just for testing.

# Updating tests when refactoring

Refactoring may change the path to an answer, but usually not the answer.