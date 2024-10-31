# Terraform EKS Project

This repository provides a sample configuration to create an Amazon Elastic Kubernetes Service (EKS) cluster on AWS using Terraform. EKS is a managed service that makes it easy to run Kubernetes on AWS without needing to manage your own control plane or nodes.

## File Explanations:

* **.terraform.lock.hcl:** This file is crucial for reproducible deployments. It locks down the specific versions of the Terraform providers used in this project, preventing unexpected changes during future runs and ensuring consistency across different environments.  This file should be committed to version control.

* **eks-cluster.tf:** This file is the heart of the EKS cluster deployment. It defines the EKS cluster itself, specifying parameters like the cluster's name, Kubernetes version, and the IAM role that the cluster will use.  It also configures important settings related to the cluster's control plane, such as public access and endpoint configuration.

* **outputs.tf:** After a successful Terraform apply, this file defines the output variables that provide access to key information about the deployed infrastructure.  For example, it might output the cluster's endpoint or the security group IDs. These outputs are useful for scripting, automation, and integrating with other tools.

* **security-groups.tf:** Security is paramount for any cloud deployment. This file defines the security groups that control network traffic to and from the EKS cluster.  It specifies rules that determine which ports and protocols are allowed, helping to protect the cluster from unauthorized access.

* **variables.tf:** This file declares variables that allow for customization of the deployment.  By using variables, you can easily modify parameters like the cluster's name, region, or instance type without changing the core Terraform code. This promotes reusability and makes it easier to manage different environments.

* **versions.tf:** This file specifies the required versions of Terraform and the AWS provider.  This ensures compatibility and helps avoid issues that might arise from using incompatible versions.  It's a good practice to keep these versions up-to-date.

* **vpc.tf:** This file defines the Virtual Private Cloud (VPC) that will house the EKS cluster.  It sets up the network infrastructure, including subnets, internet gateways, and route tables, providing a dedicated and isolated environment for the cluster.  A properly configured VPC is essential for network performance and security.

### Install AWS CLI 

As the first step, you need to install AWS CLI as we will use the AWS CLI (`aws configure`) command to connect Terraform with AWS in the next steps.

Follow the below link to Install AWS CLI.
```
https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html
```

### Install Terraform

Next, Install Terraform using the below link.
```
https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli
```

### Connect Terraform with AWS

Its very easy to connect Terraform with AWS. Run `aws configure` command and provide the AWS Security credentials as shown in the video.

### Initialize Terraform

Clone the repository and Run `terraform init`. This will intialize the terraform environment for you and download the modules, providers and other configuration required.

### Optionally review the terraform configuration

Run `terraform plan` to see the configuration it creates when executed.

### Finally, Apply terraform configuation to create EKS cluster with VPC 

`terraform apply`
