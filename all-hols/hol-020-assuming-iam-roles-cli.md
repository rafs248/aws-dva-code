## Assuming IAM roles in CLI
#### Profile that assumes new role and uses existing credentials
1.Create role `ec2-full-access` with ec2 and s3 full access.
2.Create user `Paul` with permission only to assume `ec2-full-access` role.
3.Configure `ec2-full-access` profile in `./aws/config` file; replace role ARN
4.Execute commands in CLI with and without new profile

#### Profile that uses new credentials
1.Create new user `rafal` that has attached permission policies for ec2 and s3 full control
2.Create new profile in CLI with `aws configure --profile rafal`
3.Execute CLI commands with and without profile