# aws-cloudformation-library
A set of code snippets used for my Cloudformation experiments

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

```
aws cloudformation create-stack --stack-name my-application-stack \
 --template-body file://application-stack.yaml \
 --tags Key=ProjectName,Value=MyStudy Key=OwnerTeam,Value=MyTeam \
 --profile development
```


# FAQ
## VS Code - "Unknown Tag showing up in your YAML document"
Edit your *settings.json* according to [this post](https://stackoverflow.com/questions/53470329/aws-sam-yaml-template-unknown-tag-ref).