# DevOps AWS Learning

## Overview

This repository documents my hands-on learning journey in AWS and DevOps through structured, production-style assignments. Each assignment focuses on a specific cloud architecture pattern or core DevOps concept and is implemented using managed AWS services.

The objective is to demonstrate practical, real-world understanding of cloud systems by designing, building, and validating architectures that reflect production environments — not just theory.

All implementations follow best practices for:

* Security
* Scalability
* High Availability
* Observability


The assignments can be viewed here [assignments](./assignments)


---

## Repository Structure

This repository contains **four assignments**, each organized in a consistent and clear format.

```
devops-aws-learning/
│
├── assignment-1/
│   ├── README.md
│   ├── architecture/
│   ├── screenshots/
│   └── user-data/
│
├── assignment-2/
│   ├── README.md
│   ├── architecture/
│   ├── screenshots/
│   └── user-data/
│
├── assignment-3/
│   ├── README.md
│   ├── architecture/
│   ├── screenshots/
│   └── website-data/
│
├── assignment-4/
│   ├── README.md
│   ├── architecture/
│   ├── screenshots/
│   └── lambda-code-used/
│
└── README.md

```

### Folder Breakdown

Each assignment directory contains:

* **README.md** – Detailed explanation of the assignment, objectives, implementation steps, and design decisions
* **architecture/** – Architecture diagrams and design documentation
* **screenshots/** – Deployment proof and validation evidence
* **user-data/** – EC2 user data scripts or configuration files used during provisioning
* **lambda-code-used/** - This is the code used when setting up lambda
* **website-data/** - This is the code and the data that was used and shown
This structure ensures clarity, consistency, and proper documentation for every project.

---

## Why AWS Matters in DevOps

AWS provides the core infrastructure building blocks that DevOps teams use to design, deploy, and operate applications at scale. It enables reliable system design without managing physical hardware, while still maintaining detailed control over networking, access management, and system behavior.

Through these assignments, I focus on how AWS services work together to solve real operational challenges, including:

* Designing secure and resilient network architectures
* Deploying highly available and load-balanced applications
* Delivering content efficiently using managed CDN services
* Building serverless backends that scale automatically
* Implementing monitoring and logging for operational visibility

Security and observability are treated as fundamental requirements. Access follows least-privilege principles, public endpoints are secured using HTTPS and controlled access mechanisms, and system performance is validated through logs and metrics.

This repository reflects how modern DevOps teams design, secure, and operate cloud-native systems in real production environments.
