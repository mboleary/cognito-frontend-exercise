# Cognito Frontend Exercise

This exercise uses Vue `2.5.22` to implement an example interface for answering questions.

The stylesheet used is from my website and other various projects at [Ars Materia](https://github.com/mboleary/ars-css-next).

## Requirements

- [x] A button should be used to advance from one question to the next
- [x] The user cannot advance to the next question without answering the current question
- [x] Once a question has been answered, the user cannot revisit it
- [x] The summary should display all questions and their respective answers in one view

## Reference

- https://stackoverflow.com/questions/69692842/error-message-error0308010cdigital-envelope-routinesunsupported
    - If you run into problems running this under NodeJS 17+, you may need to set an environment variable

```bash
export NODE_OPTIONS=--openssl-legacy-provider
```