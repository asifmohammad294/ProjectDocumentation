# For checking aws installed version
- aws --version

# For listing users
```console
- aws iam list-users
```

```json
- output
{
    "Users": [
        {
            "Path": "/",
            "UserName": "asif",
            "UserId": "AIDAVAJJWVJZRLSUJSPCA",
            "Arn": "arn:aws:iam::344221723251:user/asif",
            "CreateDate": "2022-07-14T18:12:40+00:00",
            "PasswordLastUsed": "2022-10-07T10:34:57+00:00"
        }
    ]
}
```

# Connect to EC2 Instance via SSH Command

```console
ssh -i .\ec2_key_pair.pem ec2-user@13.126.117.233
```

** *Note: Open Powershell or Cmd where .pem file is located.*

# Script to setup httpd web server
    #!/bin/bash
    #Use this for your user data (script from top to bottom)
    #install httpd (Linux 2 version)
    yum update -y
    yum install -y httpd
    systemctl start httpd
    systemctl enable httpd
    echo "<h1>Hello World from $(hostname -f)</h1>" > /var/www/html/index.html


# EBS(Elastic Block Storage)
- it is a volume in network drive we can attach to our instance when they run.
- the data will persist even after the instance termination.
- on (ccp level), ebs vol can be mounted only one one instance.
- it is bound to a specific availability zone.
- it is like a network USB stick
- free tier : 30 gb ebs storage of type General SSD or magnetic.

# EBS Snapshots
- used to make a backup of ebs volume at any point of time.
- can transfer snapshots accross AZ or Region.
