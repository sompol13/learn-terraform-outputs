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

### Query outputs
Now that Terraform has loaded the outputs into your project's state, use the `terraform output` command to query all of them.
- `terraform output`
- Next, query an individual output by name.
- `terraform output lb_url`
- You can use the `-raw` flag when querying a specified output for machine-readable format.
  
*Use the `lb_url` output value with the `-raw` flag to cURL the load balancer and verify the response.*
- `curl $(terraform output -raw lb_url)`

### Redact sensitive outputs
- Add the following sensitive output blocks to your `outputs.tf` file.
- Apply this change to add these outputs to your state file.
- Use `terraform output` to query the database password by name, and notice that Terraform will not redact the value when you specify the output by name.
- `terraform output db_password`
- Output values are stored as plain text in your state file.
- Use the `grep` command to see the values of the sensitive outputs in your state file.
- `grep --after-context=10 outputs terraform.tfstate`

### Reference
https://learn.hashicorp.com/tutorials/terraform/outputs