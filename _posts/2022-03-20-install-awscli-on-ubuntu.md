---
title: How to install awscli on ubuntu
tags: [AWS, awscli, ubuntu]
---

## My work environment
- ubuntu

## Prerequisites
- Python (?)

## Steps
[AWS document](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)

1. Install latest awscli v2
```sh
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```

2. Check if awscli is installed succesfully
```sh
aws --version
```

3. Setup configuration

    Enter command
    ```sh
    aws configure
    ```
    and enter your IAM user's configurations
    ```
    AWS Access Key ID [None]: (Access Key ID)
    AWS Secret Access Key [None]: (Secret Access Key)
    Default region name [None]: ap-northeast-1
    Default output format [None]: json
    ```

4. Check your configuration at
```sh
vi ~/.aws/config
vi ~/.aws/credentials
```

5. Now you can execute aws commands and your configuration above will be used automatically.
