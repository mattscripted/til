# Types of Automated Tests

One of my key takeaways from Kent C. Dodds's [_Testing JavaScript_](https://testingjavascript.com/) course is that automated tests are much more than unit tests.

He recommends these automated tests, starting from the simplest to the most complex:

| Type| Description |
| - | - |
| **Static Analysis Testing** | Checks code for defects without running it, such as with eslint, Prettier, or TypeScript |
| **Unit Testing** | Checks isolated units for defects, such as functions or components |
| **Integrating Testing** | Checks groups of units for defects, such as fetching and displaying data from an API |
| **End-to-End Testing** | Checks entire user flows for defects, such as logging in or purchasing an item |

## Further Reading

- [Kent C. Dodds - Static vs Unit vs Integration vs E2E Testing for Frontend Apps](https://kentcdodds.com/blog/unit-vs-integration-vs-e2e-tests)
- [Atlassian - The different types of software testing](https://www.atlassian.com/continuous-delivery/software-testing/types-of-software-testing)
