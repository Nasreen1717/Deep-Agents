# AWS Skill

## When to use this skill
Use this skill whenever the user asks about AWS services — EC2, S3, IAM, Lambda,
VPC, or general cloud infrastructure setup and best practices.

## EC2 quickstart
1. Go to the EC2 console and click "Launch Instance."
2. Choose an AMI (e.g. Amazon Linux 2023 or Ubuntu).
3. Choose an instance type (e.g. t2.micro for free-tier eligible testing).
4. Create or select a key pair for SSH access.
5. Configure the security group to allow the ports you need (e.g. 22 for SSH, 80/443 for web).
6. Launch the instance, then connect via:
   ```
   ssh -i your-key.pem ec2-user@<public-ip>
   ```

## Best practices
- Never hardcode AWS credentials in code; use IAM roles or environment variables.
- Use the least-privilege principle for IAM policies.
- Tag resources for cost tracking.
- Terminate unused instances to avoid unnecessary billing.
