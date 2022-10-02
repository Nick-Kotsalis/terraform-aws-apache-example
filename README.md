Terraform module for provisioning an ec2 instance that is running Apache

Not intenended for any production. Simply a way for myself to learn and practice. 

```hcl
terraform {

}

provider "aws" {
  region = "us-east-1"
}

module "apache" {
  source = ".//terraform-aws-apache-example"
  server_name = "Apache Example Server"
  instance_type = "t2.micro"
  public_key = "ssh-rsa AAAB..."
  my_ip_with_cidr = "MY_IP/32"
  vpc_id = "vpc-00000000"
}

output "public_ip" {
    value = module.apache.public_ip
}
```