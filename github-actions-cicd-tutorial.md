# 🚀 GitHub Actions CI/CD Tutorial with Cypress and Render

This tutorial walks you through setting up a CI/CD pipeline using GitHub Actions to run Cypress component tests and automatically deploy a full-stack app to Render.

---

## 🎯 Objective

To implement a workflow where:

- Cypress component tests run automatically on pull requests to the `develop` branch
- The app automatically deploys to Render when code is merged to the `main` branch

---

## 🛠 Tech Stack

- React (Frontend)
- Node.js / Express (Backend)
- MongoDB (via Render)
- Cypress (Testing)
- GitHub Actions (CI/CD)
- Render (Deployment)

---

## 🗂️ Branch Strategy

- `main`: Production-ready code
- `develop`: Integration branch for features
- `feature/*`: Feature branches merged into `develop`

---

## ✅ GitHub Action: Cypress Tests on Pull Request

Create a file: `.github/workflows/cypress-tests.yml`

```yaml
name: Cypress Tests

on:
  pull_request:
    branches:
      - develop

jobs:
  cypress-run:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '18'

      - name: Install dependencies
        run: npm install

      - name: Run Cypress component tests
        run: npm run test:component
```

📌 Make sure `package.json` includes:

```json
"scripts": {
  "test:component": "cypress run --component"
}
```

---

## 🚀 GitHub Action: Deploy to Render on Merge to Main

Create a file: `.github/workflows/render-deploy.yml`

```yaml
name: Deploy to Render

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
      - name: Trigger Render Deploy Hook
        run: |
          curl "$RENDER_DEPLOY_HOOK_URL"
        env:
          RENDER_DEPLOY_HOOK_URL: ${{ secrets.RENDER_DEPLOY_HOOK_URL }}
```

---

## ⚙️ Render Setup

1. Deploy app manually on [Render](https://render.com/)
2. Disable **Auto Deploy**
3. Copy the **Deploy Hook URL**
4. Add it to your GitHub repo:
   - Go to **Settings > Secrets > Actions**
   - Name: `RENDER_DEPLOY_HOOK_URL`
   - Value: (your hook URL)

---

## 🧪 Local Test Setup

Install dependencies:

```bash
npm install
```

Run component tests:

```bash
npm run test:component
```

---

## 🧾 Summary of Workflow

| Action                  | Trigger                      | Result                         |
|------------------------|------------------------------|--------------------------------|
| Cypress Tests          | PR to `develop`              | Run component tests            |
| Deploy to Render       | Merge to `main`              | App automatically deployed     |

---

## 📬 Submission

- Upload all code to a GitHub repo with `main` and `develop` branches
- Push features to feature branches and merge into `develop`
- Merge `develop` into `main` to deploy
- Submit this tutorial as a **GitHub Gist (.md)**

---

## 📝 Notes

- Follow GitHub best practices: commits, naming, structure
- Include a clean and descriptive README in your project repo
- Add screenshots of Actions workflows if required

---

Happy Deploying! 🚀
