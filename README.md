# 🌐 Terraform Static Website — AWS S3 + CloudFront

> Deploy a production-ready static website on AWS using Terraform — built from scratch, no modules, full control.

![Terraform](https://img.shields.io/badge/Terraform-1.0+-7B42BC?style=flat&logo=terraform)
![AWS](https://img.shields.io/badge/AWS-FF9900?style=flat&logo=amazonaws&logoColor=white)
![S3](https://img.shields.io/badge/S3-Storage-569A31?style=flat&logo=amazons3)
![CloudFront](https://img.shields.io/badge/CloudFront-CDN-FF9900?style=flat&logo=amazonaws)
![License](https://img.shields.io/badge/License-MIT-blue?style=flat)

---

<!-- Add your screenshot here -->
![Site Screenshot](website/screenshot.png)
<!-- Replace the path above with your actual screenshot file path or URL -->

---

## About The Project

This project provisions a complete static website hosting solution on AWS using raw Terraform — no community modules, no abstractions. Every resource is explicitly defined, giving you full visibility into how S3 and CloudFront work together in a real-world setup.

Built to demonstrate hands-on Infrastructure as Code skills and a deep understanding of AWS networking, storage, and CDN configuration.

---

## Architecture
```
Users
  │
  ▼
CloudFront Distribution  ←  HTTPS, CDN, Edge Caching
  │
  ▼
S3 Bucket (Private)      ←  Static Files Storage
```

The S3 bucket is fully private. All traffic is served exclusively through CloudFront.

---

## Built With

- [Terraform](https://www.terraform.io/) v1.0+
- [AWS S3](https://aws.amazon.com/s3/)
- [AWS CloudFront](https://aws.amazon.com/cloudfront/)

---

## Getting Started

### Prerequisites

- AWS account with IAM permissions for S3 and CloudFront
- Terraform v1.0+
- AWS CLI configured

### Installation
```bash
# 1. Clone the repo
git clone https://github.com/your-username/terraform-static-site-no-modules.git
cd terraform-static-site-no-modules

# 2. Set your bucket name
nano terraform.tfvars
# bucket_name = "your-globally-unique-name"

# 3. Deploy
terraform init
terraform validate
terraform plan
terraform apply
```

> ⏱ CloudFront takes ~10–15 minutes to deploy globally.

---

## Usage

After `terraform apply` completes, you'll see:
```bash
Outputs:
s3_bucket_name         = "your-bucket-name"
cloudfront_domain_name = "https://xxxxxxxxxx.cloudfront.net"
```

Open the CloudFront URL in your browser — your site is live.


---

<!-- Add more screenshots here if you have them -->
<!-- Example: -->
<!-- ![AWS Console S3](screenshots/s3-console.png) -->
<!-- ![CloudFront Distribution](screenshots/cloudfront-console.png) -->

## Project Structure
```
terraform-static-site-no-modules/
├── main.tf
├── variables.tf
├── outputs.tf
├── terraform.tfvars
├── .gitignore
├── README.md
└── website/
    ├── index.html
    ├── error.html
    └── style.css
```

---

## Roadmap

- [ ] Add custom domain with Route53 + ACM certificate
- [ ] Set up CI/CD pipeline with GitHub Actions
- [ ] Add CloudWatch monitoring and alerts
- [ ] Refactor into reusable Terraform modules

---

## Related

- 📖 [Read the full blog post](#) — replace with your blog URL
- 🔗 [Modular version of this project](#) — replace with your modules repo link

---

## License

Distributed under the MIT License.
