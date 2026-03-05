***# Deploy Static Website with Terraform (No Modules)***



***A Terraform project that deploys a static website to AWS using S3 and CloudFront, without using any Terraform modules.***



***## 📋 Overview***



***This project creates a complete infrastructure for hosting a static website on AWS with:***

***- \*\*S3 Bucket\*\* for static file storage***

***- \*\*CloudFront Distribution\*\* for global content delivery***

***- \*\*Bucket Policy\*\* for appropriate access controls***

***- Automatic upload of website files***



***## 🏗️ Infrastructure Components***



***### 1. S3 Bucket***

***- Configured for static website hosting***

***- Serves `index.html` as the default document***

***- Serves `error.html` for error pages***

***- Public read access via bucket policy***



***### 2. CloudFront Distribution***

***- Uses S3 bucket as origin***

***- Enables caching for optimal performance***

***- Default root object set to `index.html`***

***- HTTPS support with default CloudFront certificate***



***### 3. Static Website Files***

***- `index.html` - Homepage***

***- `error.html` - Error page***

***- `style.css` - Stylesheet***

***- Additional assets as needed***



***## 📁 Project Structure***



***```***

***terraform-static-site-no-modules/***

***│***

***├── main.tf              # Main Terraform configuration***

***├── variables.tf         # Variable definitions***

***├── outputs.tf           # Output definitions***

***├── terraform.tfvars     # Variable values (gitignored)***

***├── .gitignore          # Git ignore rules***

***├── README.md           # This file***

***│***

***├── website/            # Static website files***

***│   ├── index.html***

***│   ├── error.html***

***│   └── style.css***

***│***

***└── screenshots/        # Deployment proof (optional)***

    ***├── 01-terraform-init.png***

    ***├── 02-terraform-plan.png***

    ***├── 03-terraform-apply.png***

    ***├── 04-terraform-outputs.png***

    ***├── 05-s3-bucket.png***

    ***├── 06-s3-files.png***

    ***├── 07-cloudfront-distribution.png***

    ***├── 08-website-live.png***

    ***└── 09-website-error-page.png***

***```***



***## 🚀 Prerequisites***



***Before you begin, ensure you have:***



***1. \*\*Terraform\*\* installed (v1.0+)***

   ***```bash***

   ***terraform --version***

   ***```***



***2. \*\*AWS CLI\*\* configured with credentials***

   ***```bash***

   ***aws configure***

   ***```***



***3. \*\*AWS Account\*\* with appropriate permissions:***

   ***- S3: CreateBucket, PutObject, PutBucketPolicy***

   ***- CloudFront: CreateDistribution***

   ***- IAM: PassRole (for bucket policies)***



***## 📝 Configuration***



***### Step 1: Clone or Create Project***



***```bash***

***mkdir terraform-static-site-no-modules***

***cd terraform-static-site-no-modules***

***```***



***### Step 2: Create `terraform.tfvars`***



***Create a `terraform.tfvars` file with your specific values:***



***```hcl***

***aws\_region  = "us-east-1"***

***bucket\_name = "my-unique-static-website-bucket-12345"***

***project\_name = "static-website"***

***environment = "production"***

***```***



***\*\*Note:\*\* S3 bucket names must be globally unique. Choose a unique name.***



***### Step 3: Create Website Files***



***Place your website files in the `website/` directory:***



***```***

***website/***

***├── index.html***

***├── error.html***

***└── style.css***

***```***



***## 🔧 Deployment***



***### Initialize Terraform***



***```bash***

***terraform init***

***```***



***This downloads the required AWS provider.***



***### Validate Configuration***



***```bash***

***terraform validate***

***```***



***### Preview Changes***



***```bash***

***terraform plan***

***```***



***Review the resources that will be created.***



***### Deploy Infrastructure***



***```bash***

***terraform apply***

***```***



***Type `yes` when prompted to confirm.***



***### Deployment Time***



***- Initial deployment: ~10-15 minutes (CloudFront distribution creation takes the longest)***

***- Subsequent updates: ~5-10 minutes***



***## 📤 Outputs***



***After successful deployment, Terraform will output:***



***```***

***cloudfront\_distribution\_domain = "d1234567890abc.cloudfront.net"***

***cloudfront\_distribution\_id = "E1234567890ABC"***

***s3\_bucket\_name = "my-unique-static-website-bucket-12345"***

***website\_url = "https://d1234567890abc.cloudfront.net"***

***```***



***## 🌐 Accessing Your Website***



***Once deployed, access your website using the CloudFront domain:***



***```***

***https://d1234567890abc.cloudfront.net***

***```***



***\*\*Note:\*\* CloudFront distributions can take 10-15 minutes to fully deploy globally.***



***## 📸 Documentation \& Proof of Deployment***



***To document and prove successful deployment, capture screenshots and add them to the `screenshots/` directory:***



***### Required Screenshots***



***Create a `screenshots/` folder in your project root:***



***```***

***terraform-static-site-no-modules/***

***│***

***└── screenshots/***

    ***├── 01-terraform-init.png          # terraform init success***

    ***├── 02-terraform-plan.png          # terraform plan output***

    ***├── 03-terraform-apply.png         # terraform apply completion***

    ***├── 04-terraform-outputs.png       # CloudFront URL and outputs***

    ***├── 05-s3-bucket.png               # S3 bucket in AWS Console***

    ***├── 06-s3-files.png                # Uploaded files in S3***

    ***├── 07-cloudfront-distribution.png # CloudFront distribution details***

    ***├── 08-website-live.png            # Working website in browser***

    ***└── 09-website-error-page.png      # Error page (404) working***

***```***



***### Screenshot Checklist***



***- \[ ] \*\*Terraform Init\*\* - Shows provider installation***

***- \[ ] \*\*Terraform Plan\*\* - Shows resources to be created***

***- \[ ] \*\*Terraform Apply\*\* - Shows successful resource creation***

***- \[ ] \*\*Terraform Outputs\*\* - Shows CloudFront domain and S3 bucket name***

***- \[ ] \*\*S3 Bucket Console\*\* - Shows bucket exists with correct configuration***

***- \[ ] \*\*S3 Files\*\* - Shows index.html, error.html, and style.css uploaded***

***- \[ ] \*\*CloudFront Distribution\*\* - Shows distribution in "Deployed" status***

***- \[ ] \*\*Website Homepage\*\* - Browser showing your index.html via CloudFront URL***

***- \[ ] \*\*Website Error Page\*\* - Browser showing error.html (access a non-existent page)***



***### What to Capture in Each Screenshot***



***#### 1. \*\*01-terraform-init.png\*\****

   ***- \*\*Command:\*\* `terraform init`***

   ***- \*\*Show:\*\* "Terraform has been successfully initialized!" message***

   ***- \*\*Include:\*\* Provider download confirmation***



***#### 2. \*\*02-terraform-plan.png\*\****

   ***- \*\*Command:\*\* `terraform plan`***

   ***- \*\*Show:\*\* Resource count (e.g., "Plan: 5 to add, 0 to change, 0 to destroy")***

   ***- \*\*Include:\*\* List of resources to be created***



***#### 3. \*\*03-terraform-apply.png\*\****

   ***- \*\*Command:\*\* `terraform apply`***

   ***- \*\*Show:\*\* "Apply complete! Resources: X added, 0 changed, 0 destroyed"***

   ***- \*\*Include:\*\* Execution time and resource creation summary***



***#### 4. \*\*04-terraform-outputs.png\*\****

   ***- \*\*Command:\*\* `terraform output`***

   ***- \*\*Show:\*\* CloudFront domain name, S3 bucket name, and website URL***

   ***- \*\*Include:\*\* All output values clearly visible***



***#### 5. \*\*05-s3-bucket.png\*\****

   ***- \*\*AWS Console:\*\* S3 → Buckets***

   ***- \*\*Show:\*\* Your bucket listed with name and region***

   ***- \*\*Include:\*\* Bucket properties showing static website hosting enabled***



***#### 6. \*\*06-s3-files.png\*\****

   ***- \*\*AWS Console:\*\* S3 → Your Bucket → Objects***

   ***- \*\*Show:\*\* index.html, error.html, and style.css uploaded***

   ***- \*\*Include:\*\* File sizes and last modified dates***



***#### 7. \*\*07-cloudfront-distribution.png\*\****

   ***- \*\*AWS Console:\*\* CloudFront → Distributions***

   ***- \*\*Show:\*\* Distribution with "Enabled" and "Deployed" status***

   ***- \*\*Include:\*\* Distribution domain name, origin (S3 bucket), and status***



***#### 8. \*\*08-website-live.png\*\****

   ***- \*\*Browser:\*\* Navigate to CloudFront URL***

   ***- \*\*Show:\*\* Your website homepage rendering correctly***

   ***- \*\*Include:\*\* URL bar showing CloudFront domain with full page visible***



***#### 9. \*\*09-website-error-page.png\*\****

   ***- \*\*Browser:\*\* Navigate to `https://your-cloudfront-url.net/nonexistent`***

   ***- \*\*Show:\*\* Custom error.html page displaying***

   ***- \*\*Include:\*\* URL bar showing the invalid path***



***### Taking Screenshots***



***\*\*Windows:\*\****

***- `Windows + Shift + S` - Snipping tool***

***- `PrtScn` - Full screen capture***



***\*\*Mac:\*\****

***- `Cmd + Shift + 4` - Selection capture***

***- `Cmd + Shift + 3` - Full screen capture***



***\*\*Linux:\*\****

***- `PrtScn` or use `gnome-screenshot`***



***### Organizing Screenshots***



***```bash***

***# Create screenshots directory***

***mkdir screenshots***



***# Move/save all screenshots there with proper naming***

***# Follow the numbering scheme: 01, 02, 03, etc.***

***```***



***### Adding Screenshots to Documentation***



***You can reference screenshots in your documentation:***



***```markdown***

***## Deployment Evidence***



***### Terraform Execution***

***!\[Terraform Apply](./screenshots/03-terraform-apply.png)***



***### Live Website***

***!\[Website Live](./screenshots/08-website-live.png)***



***### AWS Infrastructure***

***!\[S3 Bucket](./screenshots/05-s3-bucket.png)***

***!\[CloudFront Distribution](./screenshots/07-cloudfront-distribution.png)***

***```***



***### Git Considerations***



***\*\*Option 1:\*\* Include screenshots in repository (recommended for documentation):***

***```bash***

***git add screenshots/***

***git commit -m "Add deployment proof screenshots"***

***```***



***\*\*Option 2:\*\* Exclude from Git (if screenshots contain sensitive info):***

***```gitignore***

***# In .gitignore***

***screenshots/***

***```***



***## 🔄 Updating Your Website***



***To update website content:***



***1. Modify files in the `website/` directory***

***2. Run:***

   ***```bash***

   ***terraform apply***

   ***```***

***3. Invalidate CloudFront cache (optional, for immediate updates):***

   ***```bash***

   ***aws cloudfront create-invalidation \\***

     ***--distribution-id <YOUR\_DISTRIBUTION\_ID> \\***

     ***--paths "/\*"***

   ***```***



***## 🧹 Cleanup***



***To destroy all resources and avoid charges:***



***```bash***

***terraform destroy***

***```***



***Type `yes` when prompted.***



***\*\*Warning:\*\* This will permanently delete:***

***- S3 bucket and all contents***

***- CloudFront distribution***

***- All associated configurations***



***## 💰 Cost Estimation***



***Approximate monthly costs (USD):***



***| Service | Usage | Cost |***

***|---------|-------|------|***

***| S3 | First 50 TB storage | $0.023/GB (~$0.23 for 10GB) |***

***| S3 | GET requests | $0.0004 per 1,000 requests |***

***| CloudFront | First 10 TB transfer | $0.085/GB |***

***| CloudFront | HTTP/HTTPS requests | $0.0075 per 10,000 requests |***



***\*\*Estimated total for low-traffic site:\*\* $1-5/month***



***## 🔒 Security Best Practices***



***This configuration includes:***



***✅ S3 bucket is not publicly accessible directly***  

***✅ Access only through CloudFront distribution***  

***✅ HTTPS enabled by default via CloudFront***  

***✅ Origin Access Control (OAC) for secure S3 access***  



***## 🐛 Troubleshooting***



***### Issue: Bucket name already exists***

***\*\*Solution:\*\* Change `bucket\_name` in `terraform.tfvars` to a unique value.***



***### Issue: 403 Forbidden when accessing website***

***\*\*Solution:\*\**** 

***- Wait 10-15 minutes for CloudFront to deploy***

***- Check bucket policy allows CloudFront access***

***- Verify `index.html` exists in S3 bucket***



***### Issue: Changes not reflecting on website***

***\*\*Solution:\*\* Create CloudFront invalidation:***

***```bash***

***aws cloudfront create-invalidation \\***

  ***--distribution-id <DISTRIBUTION\_ID> \\***

  ***--paths "/\*"***

***```***



***### Issue: Terraform state errors***

***\*\*Solution:\*\**** 

***```bash***

***terraform refresh***

***terraform plan***

***```***



***## 📚 File Descriptions***



***- \*\*main.tf\*\* - Core infrastructure resources (S3, CloudFront, policies)***

***- \*\*variables.tf\*\* - Input variable declarations***

***- \*\*outputs.tf\*\* - Output value definitions***

***- \*\*terraform.tfvars\*\* - Actual variable values (not committed to Git)***

***- \*\*.gitignore\*\* - Excludes sensitive/generated files from Git***

***- \*\*website/\*\* - Static HTML/CSS/JS files for the website***

***- \*\*screenshots/\*\* - Deployment proof and documentation images***



***## 🎯 Acceptance Criteria***



***- \[x] Terraform code runs successfully***

***- \[x] S3 bucket is created with website hosting enabled***

***- \[x] Static website files are uploaded to S3***

***- \[x] CloudFront distribution is created and configured***

***- \[x] Website is accessible via CloudFront URL***

***- \[x] No Terraform modules used (plain configuration only)***

***- \[x] Screenshots documented for proof of deployment***



***## 🔗 Useful Commands***



***```bash***

***# Initialize Terraform***

***terraform init***



***# Format code***

***terraform fmt***



***# Validate configuration***

***terraform validate***



***# Plan changes***

***terraform plan***



***# Apply changes***

***terraform apply***



***# Show current state***

***terraform show***



***# List resources***

***terraform state list***



***# View outputs***

***terraform output***



***# Destroy infrastructure***

***terraform destroy***



***# Create CloudFront invalidation***

***aws cloudfront create-invalidation \\***

  ***--distribution-id <DISTRIBUTION\_ID> \\***

  ***--paths "/\*"***

***```***



***## 📖 Additional Resources***



***- \[Terraform AWS Provider Documentation](https://registry.terraform.io/providers/hashicorp/aws/latest/docs)***

***- \[AWS S3 Static Website Hosting](https://docs.aws.amazon.com/AmazonS3/latest/userguide/WebsiteHosting.html)***

***- \[AWS CloudFront Documentation](https://docs.aws.amazon.com/cloudfront/)***

***- \[Terraform Best Practices](https://www.terraform-best-practices.com/)***



***## 📄 License***



***This project is provided as-is for educational purposes.***



***## 👤 Author***



***Your Name - \[Your GitHub Profile]***



***## 🤝 Contributing***



***Feel free to fork this project and submit pull requests with improvements.***



***---***



***\*\*Note:\*\* Remember to never commit sensitive files like `terraform.tfvars`, `.terraform/` directory, or state files to Git. The included `.gitignore` handles this automatically.***

