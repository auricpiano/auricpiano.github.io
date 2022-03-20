---
title: Setup codebuild project using custom docker image
tags: [AWS, Codebuild, ECR, Docker]
---

## My work environment
- Windows
- Ubuntu (VMware)

## Prerequisites
1. awscli (with configuration)
2. docker

## Steps
1. Create ECR repository
```sh
aws ecr create-repository \
--repository-name codebuild \
--image-tag-mutability MUTABLE \
--image-scanning-configuration scanOnPush=true
```

2. Build docker image
```sh
sudo docker build -t codebuild:latest .
```

3. Login to ECR using awscli
```sh
aws ecr get-login-password --region ap-northeast-1 | sudo docker login --username AWS --password-stdin {AWS Account ID}.dkr.ecr.ap-northeast-1.amazonaws.com
```

4. Set tag to image in order to push to ECR repository
```sh
sudo docker tag codebuild:latest {AWS Account ID}.dkr.ecr.ap-northeast-1.amazonaws.com/codebuild:latest
```

5. Push image to ECR repository
```sh
sudo docker push {AWS Account ID}.dkr.ecr.ap-northeast-1.amazonaws.com/codebuild:latest
```

6. Create codebuild project
    - Set project configuration.
    ![](/assets/images/posts/2022-03-20/build_project_1.png)
    - In order to use github as source provider, connection to github repository from AWS is required.
    ![](/assets/images/posts/2022-03-20/build_project_2_source.png)
    ![](/assets/images/posts/2022-03-20/build_project_3_connect_github.png)
    ![](/assets/images/posts/2022-03-20/build_project_4_connect_github_confirm.png)
    ![](/assets/images/posts/2022-03-20/build_project_5_source_set.png)
    - Set environment as custom docker image (pushed at step 5).
    ![](/assets/images/posts/2022-03-20/build_project_6_environment.png)
    ![](/assets/images/posts/2022-03-20/build_project_7_environment.png)
    - Default named buildspec file (buildspec.yml in repository root) will be used.
    ![](/assets/images/posts/2022-03-20/build_project_8_buildspec.png)
    - Leave artifacts blank.
    ![](/assets/images/posts/2022-03-20/build_project_9_artifacts.png)
    - Log build result to Cloudwatch
    ![](/assets/images/posts/2022-03-20/build_project_10_log.png)


7. Start build
```sh
aws codebuild start-build \
--project-name y-services \
--source-version dev \
--environment-variables-override name=ARGS,value='-c api -a deploy'
```

8. Check build result
![](/assets/images/posts/2022-03-20/build_project_11_result.png)
