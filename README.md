## Output Data from Terraform
In this tutorial, you will use Terraform to deploy a web application on AWS. The supporting infrastructure includes a VPC, load balancer, EC2 instances, and a database. Then you will use outputs to get information about the resources you have deployed. Next, you will use the sensitive flag to reduce the risk of inadvertently disclosing the database administrator username and password. Finally, you will use the JSON format to output data in a machine-readable format.

### Create infrastructure
- Initialize this configuration.
- `terraform init`
- Now apply the configuration.
- `terraform apply`

### Output VPC and load balancer information
- Add a block to `outputs.tf` to show the ID of the VPC.
- You can use the result of any Terraform expression as the value of an output.
- `terraform apply`

### Reference
https://learn.hashicorp.com/tutorials/terraform/outputs