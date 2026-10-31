# ☁️ AWS Zero To Hero

### Notes and hands-on labs for learning AWS, one service at a time

**🟢 Beginner friendly | 🧪 Hands-on labs | 📝 Simple notes | 🧹 Cleanup steps included**

*Learn the concept, build the lab, clean up the resources.*

---

## 📑 Table of Contents

- [About](#-about)
- [Services Covered](#-services-covered)
- [Repository Structure](#-repository-structure)
- [How to Use This Repo](#-how-to-use-this-repo)
- [Prerequisites](#-prerequisites)
- [Cost Warning](#-cost-warning)
- [Learning Roadmap](#-learning-roadmap)
- [Contributing](#-contributing)

---

## 📖 About

**AWS Zero To Hero** is my personal learning journal for Amazon Web Services. Each service has:

- 📝 **Notes**: what the service is, key terms, and how it compares to similar services
- 🧪 **Labs**: step-by-step practice you can follow in the AWS console
- 🛠️ **Troubleshooting**: common errors and fixes
- 🧹 **Cleanup**: how to delete resources so you don't get surprise charges

---

## 🧩 Services Covered

| # | Service | Category | Notes + Lab |
|---|---------|----------|-------------|
| 1 | AWS IAM | Security | `IAM/` |
| 2 | Amazon S3 | Storage | `S3/` |
| 3 | Amazon EC2 | Compute | `EC2/` |
| 4 | Amazon CloudWatch | Monitoring | `CloudWatch/` |
| 5 | Amazon CloudFront | Networking / CDN | `CloudFront/` |
| 6 | Amazon Route 53 | Networking / DNS | `Route53/` |
| 7 | Amazon VPC | Networking | `VPC/` |
| 8 | AWS Lambda | Serverless | `Lambda/` |
| 9 | AWS CloudTrail | Monitoring / Governance | `CloudTrail/` |
| 10 | AWS KMS | Security | `KMS/` |
| 11 | Amazon EFS | Storage | [EFS](./EFS/README.md) |

> Update this table as you add new folders, and link each folder once its notes are ready.

---

## 🗂️ Repository Structure

```
Aws-Zero-To-Hero/
├── README.md
├── IAM/
│   └── README.md
├── S3/
│   └── README.md
├── EC2/
│   └── README.md
├── CloudWatch/
│   └── README.md
├── CloudFront/
│   └── README.md
├── Route53/
│   └── README.md
├── VPC/
│   └── README.md
├── Lambda/
│   └── README.md
├── CloudTrail/
│   └── README.md
├── KMS/
│   └── README.md
├── EFS/
│   └── README.md        # notes + lab for Amazon EFS
├── ...
└── images/              # optional screenshots used in notes
```

Each service folder follows the same layout inside its `README.md`:

1. What is it?
2. Key terms
3. Comparison with similar services
4. Lab goal
5. Step-by-step lab
6. Troubleshooting
7. Cleanup
8. References

---

## 🚀 How to Use This Repo

1. **Clone the repo**
   ```bash
   git clone https://github.com/<your-username>/Aws-Zero-To-Hero.git
   cd Aws-Zero-To-Hero
   ```
2. **Pick a service** from the [Services Covered](#-services-covered) table
3. **Read the notes** first so you understand the concept
4. **Follow the lab** in your own AWS account
5. **Run the cleanup steps** when you finish

---

## ✅ Prerequisites

- An [AWS account](https://aws.amazon.com/free/)
- Basic Linux commands (`cd`, `ls`, `cat`, `sudo`)
- An SSH client (Terminal, PowerShell, or PuTTY)
- A basic idea of what a server and a network are

---

## 💰 Cost Warning

Some labs create resources that can cost money while they exist, such as EC2 instances, EFS storage, and NAT gateways.

- Check which resources are covered by the AWS Free Tier before you start
- Always finish with the **Cleanup** section of each lab
- Set up a **billing alert** in AWS Budgets

---

## 🗺️ Learning Roadmap

1. Security: IAM
2. Storage: S3
3. Compute: EC2
4. Monitoring: CloudWatch
5. CDN: CloudFront
6. DNS: Route 53
7. Networking: VPC
8. Serverless: Lambda
9. Governance: CloudTrail
10. Security: KMS
11. Storage: EFS

---

## 🤝 Contributing

This is a personal learning repo, but suggestions and corrections are welcome.

1. Fork the repository
2. Create a branch: `git checkout -b add-s3-notes`
3. Commit your changes: `git commit -m "Add S3 notes and lab"`
4. Push the branch and open a pull request

---

## 📚 Useful Links

- [AWS Documentation](https://docs.aws.amazon.com/)
- [AWS Free Tier](https://aws.amazon.com/free/)
- [AWS Well-Architected Framework](https://aws.amazon.com/architecture/well-architected/)

---

⭐ If this repo helps you, give it a star and keep building!
