# 🚀 Continuous Delivery Pipeline with GitHub, CodeBuild, CodePipeline, and AWS Elastic Beanstalk

This project demonstrates how to implement a **Continuous Delivery (CD) Pipeline** using **AWS Elastic Beanstalk**, **AWS CodePipeline**, **AWS CodeBuild**, and **GitHub** as the source repository. The pipeline automates the process of building and deploying a sample application to Elastic Beanstalk whenever changes are pushed to the GitHub repository.

---

## 🔧 Tech Stack & AWS Services Used

- **GitHub** – Source Control
- **AWS Elastic Beanstalk** – Application Deployment
- **AWS CodeBuild** – Build and Package the App
- **AWS CodePipeline** – Continuous Delivery Pipeline
- **IAM** – Role-based Access Control

---

## 📸 Step-by-Step Implementation

### ✅ Step 1: Create a Sample App in AWS Elastic Beanstalk

1. Navigate to the **Elastic Beanstalk** service in AWS.
2. Create a new **sample application** environment (e.g., Node.js, Python, etc.).

![Step 1a](steps/step1a.png)

![Step 1b](steps/step1b.png)

![Step 1c](steps/step1c.png)

![Step 1d](steps/step1d.png)

![Step 1e](steps/step1e.png)

3. Create IAM Role for AWS ElasticBeanstalk

Make sure to create and attach an **IAM Role** with appropriate permissions for the services to interact securely.

- Add permissions for:
  - `AWSElasticBeanstalkReadOnly`
  - `AWSElasticBeanstalkWebTier`
  - `AWSElasticBeanstalkWorkerTier`

![Step 1e1](steps/step1e1.png)

![Step 1e2](steps/step1e2.png)

![Step 1e3](steps/step1e3.png)

![Step 1e4](steps/step1e4.png)

4. Specify the role.

![Step 1f](steps/step1f.png)

5. Click on review and Submit.

![Step 1g](steps/step1g.png)

![Step 1h](steps/step1h.png)

5. Verify sample app deployment.

![Step 1h](steps/step1i.png)

---

### 🛠️ Step 2: Create a CodeBuild Project

1. Open **AWS CodeBuild** and create a new project.

![steps2](steps/step2a.png)
  
2. Connect it with your GitHub repository (authorize if required).

![steps2](steps/step2b.png)

![steps2](steps/step2c.png)
  
3. Define the **buildspec commands** from below example.

Example `buildspec.yml`:
```yaml
version: 0.2
phases:
  build:
    commands:
      - npm i --save
artifacts:
  files:
    - '**/*'

![steps2](steps/step2c2.png)

![steps2](steps/step2c3.png)

4. Click on Create Build Project.

![steps2](steps/step2cd.png)

5. Start Build and Verify logs.

![steps2](steps/step2ce.png)

![steps2](steps/step2cf.png)

---

### 🛠️ Step 3: Create a CodePipeline Project

1. Open AWS CodePipeline and create a new pipeline.

![steps3](steps/step3a.png)

2. Select existing or create New service role

![steps3](steps/step3b.png)

3. Choose GitHub as the source provider and connect your repository.

![steps3](steps/step3c.png)

4. Add the CodeBuild project as the build step.

![steps3](steps/step3d.png)

![steps3](steps/step3e.png)

5. Set Elastic Beanstalk as the Deploy provider and choose the environment created earlier.

![steps3](steps/step3f.png)

6. Create Pipeline.

![steps3](steps/step3g.png)

![steps3](steps/step3h.png)

5. Verify Deployment.

![steps3](steps/step3i.png)
