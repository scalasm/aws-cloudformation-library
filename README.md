# aws-cloudformation-library
A set of code snippets used for my Cloudformation experiments

# Support stack
```
aws cloudformation create-stack --stack-name my-support-stack \
 --template-body file://support-stack.yaml \
 --tags Key=ProjectName,Value=MyStudy Key=OwnerTeam,Value=MyTeam \
 --profile development

aws cloudformation update-stack --stack-name my-support-stack \
 --template-body file://support-stack.yaml \
 --parameters file://parameters/support-stack-parameters.json \
 --profile development
```

# Network stack
```
aws cloudformation create-stack --stack-name my-network-stack \
 --template-body file://network-stack.yaml \
 --tags Key=ProjectName,Value=MyStudy Key=OwnerTeam,Value=MyTeam \
 --profile development
```

```
aws cloudformation update-stack --stack-name my-network-stack \
 --template-body file://network-stack.yaml \
 --profile development
```

# Application stack

```
aws cloudformation create-stack --stack-name my-application-stack \
 --template-body file://application-stack.yaml \
 --tags Key=ProjectName,Value=MyStudy Key=OwnerTeam,Value=MyTeam \
 --profile development
```


# FAQ
## VS Code - "Unknown Tag showing up in your YAML document"
Edit your *settings.json* according to [this post](https://stackoverflow.com/questions/53470329/aws-sam-yaml-template-unknown-tag-ref).

## How to connect from Bastion Host to Web server EC2 instance

Both the bastion hosts and any other EC2 instances must use the same Key name: this is done in the two templates:
 * bastion-host-stack.yaml
 * application-stack.yaml

After this, the trick consists in forwarding your private key. From your local desktop:

```
 ssh ec2-user@<your-public-ip-bastion-host> -i /path/to/your-keypair.pem -v -A
```

After this you, can jump over any other EC2 instances (provided that security groups and NACLs allow that, that is!):

```
 ssh <target-host-private-ip>
```
