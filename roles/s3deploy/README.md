# S3Deploy Ansible Role

An Ansible role for deploying and configuring static websites on AWS S3.

## Description

This role automates the deployment of static websites to Amazon S3 by:

1. Creating/ensuring an S3 bucket exists with proper public access settings
2. Configuring the bucket policy to allow public read access
3. Synchronizing local website files to the S3 bucket
4. Enabling S3 static website hosting

## Requirements

- Ansible 2.1 or higher
- AWS credentials properly configured
- AWS CLI
- Python boto3 library
- Access to an AWS account with permissions to create and modify S3 buckets

## Role Variables

| Variable | Description | Default |
|----------|-------------|---------|
| `bucket_name` | Name of the S3 bucket to create/use | Required |
| `bucket_tags` | Tags to apply to the S3 bucket | Required |
| `bucket_local_website_path` | Local path to the static website files | Required |

## Example Playbook

```yaml
---
- name: Deploy static website to S3
  hosts: localhost
  roles:
    - role: s3deploy
      vars:
        bucket_name: my-static-website
        bucket_tags:
          tier: web
          web: static
        bucket_local_website_path: /path/to/website/files
```

## Task Workflow

1. Checks if the S3 bucket exists and creates it if necessary
2. Configures the bucket with public access settings
3. Applies a bucket policy allowing public read access
4. Synchronizes local files to the S3 bucket
5. Enables S3 website hosting with index.html as the default document

## Dependencies

This role depends on the following collections:

- amazon.aws
- community.aws

## License

TBD

## Author

Rafik Bahri
