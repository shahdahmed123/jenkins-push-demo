# Jenkins Declarative Pipeline Lab

This project demonstrates the implementation of a Jenkins Declarative Pipeline using parameters, conditional execution, environment variables, and post-build actions.

## Overview

The pipeline simulates a basic CI/CD workflow by performing:

- Source code checkout
- Build stage
- Optional test execution
- Conditional deployment
- Build status reporting

The project is intended for learning Jenkins Pipeline syntax and pipeline automation concepts.

---

## Features

- Declarative Jenkins Pipeline
- Build Parameters
- Conditional Stage Execution
- Environment Variables
- Git SCM Checkout
- Post Build Actions
- Bash Script Execution

---

## Pipeline Flow

```
          Start
            │
            ▼
      Checkout Source
            │
            ▼
          Build
            │
            ▼
     Run Tests (Optional)
            │
            ▼
Deploy (master + prod only)
            │
            ▼
      Success / Failure
```

---

## Build Parameters

| Parameter | Description |
|-----------|-------------|
| VERSION | Application version |
| ENV | Deployment environment (dev, test, prod) |
| RUN_TESTS | Enable or disable testing |

---

## Pipeline Stages

### Checkout

Retrieves the source code from Git.

### Build

Simulates the application build process.

### Test

Runs only when **RUN_TESTS = true**.

### Deploy

Runs only when:

- Branch = master
- Environment = prod

---

## Post Actions

On Success

- Display success message.

On Failure

- Display failure message.

---

## Shell Script

The pipeline executes a simple Bash script that:

- Prints current date and time
- Displays machine hostname
- Lists current directory contents

---

## Technologies

- Jenkins
- Declarative Pipeline
- Git
- Bash
