# DevOps with GitHub: A Comprehensive Guide

## **Module 1: Introduction to DevOps and GitHub**

### **What is DevOps?**
DevOps is a set of practices that combines software development (Dev) and IT operations (Ops). It aims to shorten the development lifecycle while delivering high-quality software. 

#### **Key Principles of DevOps:**
1. Collaboration between teams.
2. Automation of processes.
3. Continuous Integration and Delivery.
4. Monitoring and Feedback.

#### **Example:**
Imagine a team building a weather app. With DevOps:
- Developers write code and push it to a shared repository.
- Automated tools test the code.
- Operations deploy the app automatically if tests pass.

### **What is GitHub?**
GitHub is a platform for version control and collaboration. It allows developers to work on projects together, track changes, and manage code repositories.

#### **Setting up GitHub:**
1. Create a GitHub account at [github.com](https://github.com).
2. Install Git on your local machine.
3. Configure Git with your username and email:
   ```bash
   git config --global user.name "Your Name"
   git config --global user.email "your-email@example.com"
   ```

### **Lab: Setting Up Your GitHub Repository**
1. **Create a Repository:**
   - Log in to GitHub and click “New Repository”.
   - Name your repository (e.g., `weather-app`).
   - Select “Public” and check “Initialize this repository with a README”.
2. **Clone the Repository Locally:**
   ```bash
   git clone https://github.com/your-username/weather-app.git
   ```
3. **Push Code to GitHub:**
   ```bash
   echo "# Weather App" >> README.md
   git add README.md
   git commit -m "Initial commit"
   git push origin main
   ```

---

## **Module 2: Version Control and Collaboration**

### **Advanced Git Concepts**

#### **Branching and Merging:**
Branches allow you to work on different features simultaneously.

- Create a new branch:
  ```bash
  git branch feature-login
  git checkout feature-login
  ```
- Merge the branch:
  ```bash
  git checkout main
  git merge feature-login
  ```

#### **Resolving Merge Conflicts:**
If two branches modify the same file, conflicts occur during merging.
- Open the conflicting file and edit manually.
- Mark resolved conflicts and commit:
  ```bash
  git add .
  git commit -m "Resolved conflicts"
  ```

#### **Example:**
1. Developer A works on `feature-login`.
2. Developer B works on `feature-signup`.
3. Both merge into `main`, resolving any conflicts.

### **Collaborative Development**
- **Pull Requests:**
  1. Create a pull request in GitHub.
  2. Add reviewers and wait for feedback.
- **GitHub Issues:**
  - Use for bug tracking or feature requests.

#### **Lab: Collaborative Project**
1. Clone a shared repository.
2. Create a branch for your feature.
3. Push changes and open a pull request.

---

## **Module 3: Continuous Integration (CI) with GitHub Actions**

### **What is CI/CD?**
CI/CD automates testing and deployment. Continuous Integration ensures code changes integrate seamlessly, while Continuous Delivery automates deployment.

#### **GitHub Actions Basics:**
1. **Workflow Files:** Define automation scripts in `.github/workflows/`.
   Example CI workflow:
   ```yaml
   name: CI Pipeline
   on:
     push:
       branches:
         - main
   jobs:
     build:
       runs-on: ubuntu-latest
       steps:
         - uses: actions/checkout@v2
         - name: Run Tests
           run: npm test
   ```

2. **Triggers:** Automatically start workflows based on events like `push` or `pull_request`.

### **Lab: Build and Test Automation**
1. Create `.github/workflows/ci.yml`.
2. Define steps to test your project.
3. Push changes to trigger the workflow.

---

## **Module 4: Continuous Delivery (CD) with GitHub Actions**

### **Deploying Applications:**
1. Automate deployments to AWS, Azure, or GCP.
2. Example Deployment Workflow:
   ```yaml
   name: CD Pipeline
   on:
     push:
       branches:
         - main
   jobs:
     deploy:
       runs-on: ubuntu-latest
       steps:
         - uses: actions/checkout@v2
         - name: Deploy to AWS
           run: ./deploy-script.sh
   ```

### **Lab: CD Workflow**
1. Write a deployment script.
2. Configure a GitHub Action to run it on every merge.

---

## **Module 5: Infrastructure as Code (IaC) with GitHub**

### **What is IaC?**
IaC manages infrastructure using code, enabling consistency and versioning.

#### **Example with Terraform:**
1. Install Terraform.
2. Write a configuration file:
   ```hcl
   provider "aws" {
     region = "us-west-2"
   }
   resource "aws_s3_bucket" "my_bucket" {
     bucket = "my-unique-bucket-name"
     acl    = "private"
   }
   ```
3. Apply the configuration:
   ```bash
   terraform init
   terraform apply
   ```

### **Lab: Deploy Infrastructure with IaC**
1. Use Terraform to create an AWS EC2 instance.
2. Automate the process with GitHub Actions.

---

## **Module 6: Monitoring and Feedback**

### **Monitoring in DevOps:**
1. Use tools like Prometheus and Grafana for observability.
2. Set up alerts for performance issues.

#### **Example:**
Integrate monitoring tools to track application uptime and resource usage.

### **Lab: Set Up Monitoring**
1. Deploy Prometheus and Grafana.
2. Create dashboards for your application.

---

## **Module 7: Security in DevOps with GitHub**

### **GitHub Security Features:**
1. Enable Dependabot for dependency updates.
2. Use Code Scanning for vulnerability detection.

#### **Example:**
Set up CodeQL in GitHub Actions to scan your repository:
```yaml
name: CodeQL Analysis
on:
  push:
    branches: [ main ]
jobs:
  analyze:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Initialize CodeQL
        uses: github/codeql-action/init@v2
        with:
          languages: javascript
      - name: Perform CodeQL Analysis
        uses: github/codeql-action/analyze@v2
```

### **Lab: Implement Security Practices**
1. Enable Dependabot alerts.
2. Resolve identified vulnerabilities.

---

## **Module 8: Real-World DevOps Project**

### **Project Overview:**
1. Create an end-to-end pipeline for a sample project.
2. Include CI/CD, IaC, monitoring, and security.

#### **Lab:**
1. Build a weather app.
2. Automate testing, deployment, and monitoring.

---

## **Detailed Commands Table**

| **Name**    | **Commands**         | **Description**                                                  |
|-------------|----------------------|------------------------------------------------------------------|
| **Clone**   | `git clone <url>`    | Clone a repository into a new directory.                        |
| **Init**    | `git init`           | Create an empty Git repository or initialize an existing one.   |
| **Add**     | `git add .`          | Add file contents to the index.                                 |
| **Mv**      | `git mv <source> <destination>` | Move or rename a file, or directory.                          |
| **Restore** | `git restore <file>` | Restore working tree files.                                     |
| **Rm**      | `git rm -r <file>`   | Remove files or directories from the working tree and index.    |
| **Commit**  | `git commit -m "<message>"` | Record changes to the repository with a descriptive message.  |
| **Push**    | `git push origin <branch>` | Update remote refs along with associated objects.             |
| **Branch**  | `git branch <branch>`| Create a new branch.                                            |
| **Checkout**| `git checkout <branch>` | Switch branches or restore working tree files.               |
| **Merge**   | `git merge <branch>` | Join two or more development histories together.                |
| **Config**  | `git config --global user.name "<name>"` | Set the global username configuration.                      |
|             | `git config --global user.email "<email>"` | Set the global email configuration.                        |
| **Pull**    | `git pull`           | Fetch and integrate with another repository or branch.          |
| **Status**  | `git status`         | Show the working tree status.                                   |
| **Log**     | `git log`            | Show commit logs.                                               |
| **Fetch**   | `git fetch`          | Download objects and refs from another repository.              |
| **Stash**   | `git stash`          | Save and clear changes in the working directory.                |
| **Rebase**  | `git rebase <branch>`| Reapply commits on top of another base tip.                     |
| **Tag**     | `git tag <tag>`      | Create, list, delete, or verify tags in Git.                    |
| **Reset**   | `git reset <file>`   | Unstage a file without deleting it from the working directory.  |
| **Init Terraform** | `terraform init` | Initialize a Terraform working directory.                     |
| **Apply Terraform** | `terraform apply` | Apply Terraform configuration to provision resources.         |
| **NPM Test**| `npm test`           | Run tests for a Node.js application.                            |
| **Custom Script** | `./deploy-script.sh` | Execute a custom deployment script.                          |

## **Detailed Commands Table**

<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Commands</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><b>Clone</b></td>
      <td>
        <code>git clone &lt;url&gt;</code>
        <button onclick="copyToClipboard('git clone <url>')">Copy</button>
      </td>
      <td>Clone a repository into a new directory.</td>
    </tr>
    <tr>
      <td><b>Init</b></td>
      <td>
        <code>git init</code>
        <button onclick="copyToClipboard('git init')">Copy</button>
      </td>
      <td>Create an empty Git repository or initialize an existing one.</td>
    </tr>
    <tr>
      <td><b>Add</b></td>
      <td>
        <code>git add .</code>
        <button onclick="copyToClipboard('git add .')">Copy</button>
      </td>
      <td>Add file contents to the index.</td>
    </tr>
    <tr>
      <td><b>Push</b></td>
      <td>
        <code>git push origin &lt;branch&gt;</code>
        <button onclick="copyToClipboard('git push origin <branch>')">Copy</button>
      </td>
      <td>Update remote refs along with associated objects.</td>
    </tr>
    <tr>
      <td><b>Commit</b></td>
      <td>
        <code>git commit -m "&lt;message&gt;"</code>
        <button onclick="copyToClipboard('git commit -m \"<message>\"')">Copy</button>
      </td>
      <td>Record changes to the repository with a descriptive message.</td>
    </tr>
    <!-- Add more rows here as needed -->
  </tbody>
</table>

<script>
  function copyToClipboard(command) {
    navigator.clipboard.writeText(command).then(() => {
      alert(`Copied: ${command}`);
    });
  }
</script>
