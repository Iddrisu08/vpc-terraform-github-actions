# AWS VPC Infrastructure with Terraform and GitHub Actions

This project demonstrates Infrastructure as Code (IaC) using Terraform to deploy a complete AWS VPC setup with automated CI/CD through GitHub Actions.

[![Terraform CI CD Pipeline for Deploying AWS Resources](https://github.com/Iddrisu08/vpc-terraform-github-actions/actions/workflows/deploy.yml/badge.svg)](https://github.com/Iddrisu08/vpc-terraform-github-actions/actions/workflows/deploy.yml)

## 🏗️ Architecture Overview

This infrastructure creates a robust AWS VPC environment with the following components:

- **VPC**: Virtual Private Cloud with configurable CIDR blocks
- **Subnets**: Multiple subnets for high availability
- **Security Groups**: Network security rules for EC2 instances
- **EC2 Instances**: Compute resources within the VPC
- **Application Load Balancer (ALB)**: Traffic distribution across instances

## 📁 Project Structure

```
.
├── .github/
│   └── workflows/
│       └── deploy.yml          # CI/CD pipeline configuration
├── Terraform-VPC/
│   ├── main.tf                 # Main Terraform configuration
│   ├── variable.tf             # Input variables
│   ├── provider.tf             # AWS provider configuration
│   └── modules/
│       ├── vpc/                # VPC module
│       ├── sg/                 # Security Groups module
│       ├── ec2/                # EC2 instances module
│       └── alb/                # Application Load Balancer module
└── README.md
```

## 🚀 Features

- **Modular Design**: Terraform modules for reusable infrastructure components
- **Automated Deployment**: GitHub Actions workflow for CI/CD
- **Security Best Practices**: Proper security group configurations
- **Load Balancing**: Application Load Balancer for high availability
- **Infrastructure Validation**: Terraform validate, plan, and apply stages

## 🛠️ Prerequisites

Before using this project, ensure you have:

1. **AWS Account** with appropriate permissions
2. **AWS CLI** configured with access credentials
3. **Terraform** installed (v1.0+)
4. **GitHub repository** with the following secrets configured:
   - `AWS_ACCESS_KEY`: Your AWS access key ID
   - `AWS_SECRET_ACCESS_KEY`: Your AWS secret access key

## ⚙️ Configuration

### Terraform Variables

Configure the following variables in `Terraform-VPC/variable.tf`:

- `vpc_cidr`: CIDR block for the VPC
- `subnet_cidr`: List of CIDR blocks for subnets

### GitHub Secrets

Set up these secrets in your GitHub repository:

1. Go to **Settings** → **Secrets and variables** → **Actions**
2. Add the following secrets:
   - `AWS_ACCESS_KEY`: Your AWS access key ID
   - `AWS_SECRET_ACCESS_KEY`: Your AWS secret access key

## 🚦 Deployment

The deployment is fully automated through GitHub Actions:

1. **Push to main branch** triggers the pipeline
2. **Terraform Init**: Initializes Terraform working directory
3. **Terraform Validate**: Validates configuration files
4. **Terraform Plan**: Shows planned infrastructure changes
5. **Terraform Apply**: Applies the infrastructure changes

### Manual Deployment

To deploy manually:

```bash
cd Terraform-VPC
terraform init
terraform validate
terraform plan
terraform apply
```

## 🗂️ Modules

### VPC Module
- Creates VPC with specified CIDR
- Sets up subnets across availability zones
- Configures internet gateway and routing

### Security Groups Module
- Defines network security rules
- Controls inbound/outbound traffic

### EC2 Module
- Launches EC2 instances in subnets
- Applies security group rules

### ALB Module
- Creates Application Load Balancer
- Distributes traffic across EC2 instances
- Health check configuration

## 🔧 Customization

To customize the infrastructure:

1. Modify variables in `variable.tf`
2. Update module configurations in `main.tf`
3. Adjust security group rules in `modules/sg/`
4. Configure ALB settings in `modules/alb/`

## 📝 CI/CD Pipeline

The GitHub Actions workflow (`deploy.yml`) includes:

- **Trigger**: Automatic on push to main branch
- **Environment**: Ubuntu latest with Terraform setup
- **Steps**: Checkout → Setup → Init → Validate → Plan → Apply
- **Security**: Uses GitHub secrets for AWS credentials

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test the infrastructure
5. Submit a pull request

## ⚠️ Important Notes

- The current workflow runs `terraform destroy` in the apply step for demonstration purposes
- For production use, change the apply step to `terraform apply --auto-approve`
- Always review the Terraform plan before applying changes
- Monitor AWS costs when running infrastructure

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

**Built with** ❤️ using Terraform and GitHub Actions
