## Create VPC with wizard
1. Create VPC using `VPC and more` wizard

## Create VPC manually
1. Create VPC with `VPC only` wizard
 - use CIDR as in provided file (or come up with own one)
2. Create subnets: 2 private and 2 public ones
3. Rename default routing table as public
4. Create private routing table and associate subnets with it
5. Create internet gateway
6. In public subnets enable `Autoassign public IP` option
7. Create EC2 instance in public subnet
 - create new security group with default settings
8. Use `Instance connect` to connect to EC2
 - `ping google.com`
9. Terminate EC2 instance