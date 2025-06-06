## Switching IAM roles
1. Create user `Joe` with no permissions
2. Log in as `Joe` to EC2 dashboard (no access)
3. Create role `ec2-full-access`
   - trusted entity: AWS Account
   - ec2 full access
4. Use link provided to switch role (no access)
5. Add permission to `Joe` user
   - sts assume role - it is in the file
6. Now `Joe` should have access in EC2 dashboard
7. 7.Delete user `Joe` and new role `ec2-full-access`