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

# for giving read write execute permission to file or folder
sudo chmod a+rwx filename/foldername