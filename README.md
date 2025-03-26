# 🚀 Tech Quiz App with CI/CD using GitHub Actions

This is a full-stack Tech Quiz application that incorporates a robust CI/CD pipeline using GitHub Actions. The project is designed to demonstrate how automated testing and deployment can be seamlessly integrated into a modern development workflow.

## 📋 Table of Contents

- [About the Project](#about-the-project)
- [Tech Stack](#tech-stack)
- [CI/CD Workflow](#cicd-workflow)
- [Getting Started](#getting-started)
- [Running Tests](#running-tests)
- [Deployment](#deployment)
- [Screenshots](#screenshots)
- [Contributing](#contributing)
- [License](#license)

---

## 📖 About the Project

**User Story:**

> As a software engineer looking to integrate a CI/CD pipeline into a codebase,  
> I want a full-stack application that runs test cases when a Pull Request is made to the `develop` branch  
> and automatically deploys to Render when the code is merged to the `main` branch,  
> So that I can ensure all integrations are clean, tested, and deployed efficiently.

This project ensures high code quality and delivery speed by:
- Running **Cypress component tests** on pull requests to the `develop` branch
- Automatically deploying the application to **Render** when code is merged into the `main` branch

---

## 🛠 Tech Stack

- **Frontend:** React, Tailwind CSS
- **Backend:** Node.js, Express
- **Database:** MongoDB (via Render)
- **Testing:** Cypress (Component Testing)
- **CI/CD:** GitHub Actions
- **Deployment:** Render

---

## 🔄 CI/CD Workflow

### ✅ On Pull Request to `develop`
- GitHub Actions runs Cypress component tests
- Ensures feature branches don’t break the app

### 🚀 On Merge to `main`
- GitHub Actions triggers Render deploy hook
- Automatically deploys the app to the live environment

---

## 🧪 Running Tests

Make sure you have all dependencies installed:

```bash
npm install
```

Then, run the component tests locally:

```bash
npm run test:component
```

> GitHub Actions runs this command automatically during PRs to `develop`.

---

## 📦 Deployment

The app is deployed using **Render**.

- **Auto-deploy** is disabled
- A **Deploy Hook URL** is configured as a secret (`RENDER_DEPLOY_HOOK_URL`) in the GitHub repository
- When code is merged into `main`, GitHub Actions triggers the deploy

---

## 🖼 Screenshots

### ✅ GitHub Action - Cypress Tests on Pull Request
![Cypress Tests Workflow](./screenshots/cypress-tests.png)

### 🚀 GitHub Action - Deploy to Render on Merge to Main
![Render Deployment Workflow](./screenshots/render-deploy.png)

---

## 🤝 Contributing

Contributions are welcome! Please follow the feature branch workflow:

1. Branch off from `develop`: `git checkout -b feature/your-feature`
2. Submit a Pull Request to `develop`
3. Ensure all tests pass via GitHub Actions
4. Once stable, merge `develop` into `main`

---

## 📝 License

This project is licensed under the [MIT License](LICENSE).

---

## 🔗 Live Demo

🌐 [Live App on Render](https://your-app-url.onrender.com)

---

## 📁 Repository

📂 [GitHub Repo](https://github.com/yourusername/your-repo-name)
