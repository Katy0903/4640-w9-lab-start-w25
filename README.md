# 4640-w9-lab-start-w25

See lab instructions on D2L


## Prerequisites
- AWS CLI configured with appropriate credentials
- Packer installed
- Terraform installed
- Git installed

## Steps to Run

1. Build the AMI with Packer:

```
cd packer
packer init .
packer build ansible-web.pkr.hcl
```

2. Deploy with Terraform:


```
cd ../terraform
terraform init
terraform apply

```


3. Test the deployment:

- SSH into the instance using the output IP address
- Check if Nginx is running: systemctl status nginx
- Visit the public IP in a web browser to see the Nginx welcome page

4. Clean up:

```
terraform destroy
```

Note: Creating a new AMI will create a new AMI and a new Snapshot in your AWS account. To clean up these resources first Deregister the AMI then Delete the snapshot.