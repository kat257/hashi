# Getting Started with Terraform
To begin defining and provisioning infrastructure using HashiCorp’s Terraform, first you’ll need to install the Terraform command line interface (CLI) and secure your cloud infrastructure either locally or using a provider such as Amazon Web Services (AWS) or Google Cloud Platform. 
Next, you can create your Terraform infrastructure and ensure that it is properly installed, then clean up by destroying the infrastructure. 
*Optionally, you can sign up for [Terraform Cloud](https://app.terraform.io/signup/account?utm_source=iopage&utm_campaign=tf_cloud_ga "Terraform Cloud").*
## Prerequisites 

* Terraform command line interface (CLI)
* Cloud infrastructure
## Install Terraform
To install Terraform, visit [Terraform.io](https://www.terraform.io/downloads.html) and download the installer file for your preferred platform.
## Create infrastructure 
Once you’ve installed Terraform, you can begin creating infrastructure.
### Create directory
We recommend creating a new directory for Terraform on your local machine.
```shell
$ mkdir terraform-demo
$ cd terraform-demo
```
### Create configuration code file
Next, create a file for your Terraform configuration code.
```shell
$ touch main.tf
```
Paste the following lines into the file.
```hcl
provider "docker" {
    host = "unix:///var/run/docker.sock"
}

resource "docker_container" "nginx" {
  image = docker_image.nginx.latest
  name  = "training"
  ports {
    internal = 80
    external = 80
  }
}

resource "docker_image" "nginx" {
  name = "nginx:latest"
}
```
### Initialize Terraform
Initialize Terraform with the `init` command to install the AWS provider. 
```shell
$ terraform init
```
### Provision the resource 
Check for errors. If the initialization ran successfully, provision the resource with the `apply` command.
```shell
$ terraform apply
```
The command will take up to a few minutes to run. When complete, a message will indicate that the resource was created.
## Clean up infrastructure
Finally, clean up your work by destroying the Terraform infrastructure.
```shell
$ terraform destroy
```
Look for a message at the bottom of the output asking for confirmation. Type `yes` and hit ENTER. Terraform will destroy the resources it had created earlier.
## Next steps
Now you’ve defined and provisioned your Terraform infrastructure using the command line interface (CLI) on your selected cloud provider, checked that it is properly installed, and destroyed the infrastructure.   

In the next section, you’ll learn how to modify your cloud infrastructure to match your requirements. 

