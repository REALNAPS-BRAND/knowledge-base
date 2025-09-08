# Contributing to the Realnaps Codebase

## 1.0 Introduction

This document provides the official guidelines for all developers contributing to the Realnaps codebase. Its purpose is to ensure that all contributions are consistent, high-quality, and align with our architectural and cultural principles. Adherence to these guidelines is mandatory for all team members and authorized contractors.

## 2.0 Core Philosophy

Our goal is to build robust, secure, and maintainable software. We achieve this by following a structured development process. All contributions, from minor bug fixes to major features, must follow the prescribed workflow of creating an issue, submitting a pull request, and passing a formal code review and quality assurance check.

## 3.0 Getting Started: The Development Lifecycle

All work must be tracked via GitHub Issues in the relevant private repository.

### 3.1 Issue Tracking

*   **Bugs:** Before writing any code for a bug fix, ensure a corresponding "Bug Report" issue has been created. The issue must be detailed enough for another developer to understand and reproduce the problem.
    
*   **Features:** New features or enhancements must start with a "Feature Request" issue. This serves as the specification document and the hub for all technical discussions related to the feature.
    

### 3.2 The Pull Request Process

1.  **Fork & Clone:** While you will have direct access to the private repositories, the best practice is to fork the repository to your personal account to keep the main repo clean. Clone your fork locally.
    
2.  **Branching:** Create a new branch from `main` for your work. Use a descriptive name that includes the issue number (e.g., `feature/123-user-profile-avatars`).
    
3.  **Code with Standards:** Write your code, adhering strictly to our technical principles:
    
    *   **Object-Oriented Programming (OOP):** All code, whether it's PHP or Node.js, must be written following strict OOP principles. This is a foundational requirement.
        
    *   **Technology Stack:**
        
        *   **Web Client:** Modern, Object-Oriented PHP, with jQuery for specific frontend functionalities.
            
        *   **Desktop Client & Scrapers:** Node.js and Electron, written in a clean, object-oriented style.
            
4.  **Commit Messages:** Use clear and descriptive commit messages that follow the [Conventional Commits](https://www.conventionalcommits.org/ "null") specification. Reference the issue number in your commits.
    
5.  **Submit a Pull Request:** Push your branch to your fork and open a pull request against the `main` branch of the upstream repository.
    
    *   The PR title must be clear and reference the issue number.
        
    *   The description must detail the changes and explicitly link the issue it resolves using "Closes #123".
        
    *   Assign the relevant reviewers as specified in the `CODEOWNERS` file.
        
6.  **Code Review & QA:** Your PR will be reviewed by the core team and tested on the **Staging Environment** by QA. You are expected to address any feedback or requested changes promptly. Once approved and all checks pass, it will be merged by a code owner.
    

### 3.3 Development Environments

*   **Development:** Your local setup. This must be a full replication of the system to allow for comprehensive testing.
    
*   **Staging:** A production-like environment for final, pre-merge testing. All PRs are deployed here for QA.
    
*   **Production:** The live system serving our customers.
    
*   **Disaster Recovery:** We maintain robust backup and data replication strategies.
