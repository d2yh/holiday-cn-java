name: Bug Report
description: Report a bug or issue
title: "[BUG] "
labels: ["bug"]

body:
  - type: markdown
    attributes:
      value: |
        Thanks for taking the time to report a bug! Please provide as much detail as possible to help us understand and fix the issue.

  - type: input
    id: java-version
    attributes:
      label: Java Version
      description: What Java version are you using?
      placeholder: "1.8, 11, 17, etc."
    validations:
      required: true

  - type: input
    id: os
    attributes:
      label: Operating System
      description: What OS are you using?
      placeholder: "Windows, macOS, Linux, etc."
    validations:
      required: true

  - type: textarea
    id: description
    attributes:
      label: Description
      description: Describe the bug
      placeholder: "A clear and concise description of what the bug is."
    validations:
      required: true

  - type: textarea
    id: steps-to-reproduce
    attributes:
      label: Steps to Reproduce
      description: Steps to reproduce the behavior
      placeholder: |
        1. First do this...
        2. Then do that...
        3. See error...
    validations:
      required: true

  - type: textarea
    id: expected-behavior
    attributes:
      label: Expected Behavior
      description: What should happen?
    validations:
      required: true

  - type: textarea
    id: actual-behavior
    attributes:
      label: Actual Behavior
      description: What actually happens?
    validations:
      required: true

  - type: textarea
    id: error-logs
    attributes:
      label: Error Messages / Stack Traces
      description: Include any error messages or stack traces
      render: java

  - type: textarea
    id: additional-context
    attributes:
      label: Additional Context
      description: Any other information that might be helpful
