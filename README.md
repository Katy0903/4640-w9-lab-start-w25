# 4640-w9-lab-start-w25

See lab instructions on D2L


## Prerequisites
- AWS CLI configured with appropriate credentials
- Packer installed
- Terraform installed
- Git installed

## Steps to Run
1. Clone the repository:

```
git clone <your-repo-url>
cd <repo-directory>
```

2. Build the AMI with Packer:

```
cd packer
packer init .
packer build ansible-web.pkr.hcl
```
Note: you will get the AMI ID from the output.

3. Update Terraform configuration:

```
cd ../terraform
```
Edit main.tf and update the aws_ami data source with the new AMI ID.

4. Deploy with Terraform:

```
terraform init
terraform apply
```

5. Test the deployment:

- SSH into the instance using the output IP address
- Check if Nginx is running: systemctl status nginx
- Visit the public IP in a web browser to see the Nginx welcome page

6. Clean up:

```
terraform destroy
```

Note: Creating a new AMI will create a new AMI and a new Snapshot in your AWS account. To clean up these resources first Deregister the AMI then Delete the snapshot.